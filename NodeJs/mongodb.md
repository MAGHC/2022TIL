### 몽고db

몽고디비는 말햇듯이 no sql 로 스키마가 없고

db → 콜렉션 → 문서 이런구조를 가지고있음

셋팅

그냥 몽고디비가서 cloud로 만들고 / user 넣어주고 설정해주고 create

your application 그냥 흐름대로 쭉쭉 하면됨

몽고 db 드라이버를 깔자

/util / database.js

mongodb+srv://administrator:<password>@cluster0.aapwhd8.mongodb.net/?retryWrites=true&w=majority

이런형태 참고로 password <> 이거까지 다지워야됨 안에다가 넣었다가 낭패

```js
const mongodb = require("mongodb");

const MongoClient = mongodb.MongoClient;

const MongoConnect = (callBack) => {
  MongoClient.connect("mongodb+srv://administrator:q1w2e3r4!!@cluster0.aapwhd8.mongodb.net/?retryWrites=true&w=majority")
    .then((res) => callBack(res))
    .catch((err) => console.err(err));
};

module.exports = MongoConnect;
```

```js
MongoClient.connect("mongodb+srv://administrator:dlthf214!!@cluster0.aapwhd8.mongodb.net/?retryWrites=true&w=majority")

d여기서

MongoClient.connect("mongodb+srv://administrator:dl412pt!!@cluster0.aapwhd8.mongodb.net/'여기에 데이터 베이스'?retryWrites=true&w=majority")

or

MongoClient.connect("mongodb+srv://administrator:d214!!@cluster0.aapwhd8.mongodb.net/?retryWrites=true&w=majority")
    .then((res) => {
      db = res.db('데이터베이스이름');


sql 과 달리 데이터베이스나 테이블을 생성할 필요가없다.


//util/database
const mongodb = require("mongodb");

const MongoClient = mongodb.MongoClient;

let db;

const mongoConnect = (callBack) => {
  MongoClient.connect("mongodb+srv://administrator:q2qe2qdwa!!@cluster0.aapwhd8.mongodb.net/?retryWrites=true&w=majority")
    .then((res) => {
      db = res.db();
      callBack(res);
    })
    .catch((err) => console.err(err));
};

const getDb = () => {
  if (db) {
    return db;
  }
  throw "no Data";
};

exports.mongoConnect = mongoConnect;
exports.getDb = getDb;


//model/util


const getDb = require('../util/database').getDb;

class Product {
  constructor(title, price, description, imageUrl) {
    this.title = title;
    this.price = price;
    this.description = description;
    this.imageUrl = imageUrl;
  }

  save() {
    const db = getDb();
    return db
      .collection('products')
      .insertOne(this) //insertMany()  도잇음
      .then(result => {
        console.log(result);
      })
      .catch(err => {
        console.log(err);
      });
  }

  static fetchAll() {
    const db = getDb();
    return db
      .collection('products')
      .find()
      .toArray()
      .then(products => {
        console.log(products);
        return products;
      })
      .catch(err => {
        console.log(err);
      });
  }
}

module.exports = Product;

참고로 id는 몽고db가 자동적으로 생성


```

### mongoDb compass(나침반)

몽고 db에서 제공하는 어플리케이션으로

데이터베이스에 연결할수있는 gui 제공

설치후 끄고

mongodb 에서 connect ⇒ compass 뭐시기 처음 db연결할떄처럼 아이디 비번 적는거 복사하고 다시키면 알아서 클립보드읽음

authentication 가서 유저이름 / 비밀번호 설정

### fetchall / 단일 제품 구현

```js
static fetchAll() {
    const db = getDb();
    return db
      .collection("products")
      .find()//find({title:book}) 파인드는 프로미스가아니라 소위 cursor를 반환한다
      .toArray()//자바스크립트 배열로 바꿈 그리고 프로미스를 반환함
      .then((products) => {
        console.log(products);
        return products;
      })
      .catch((err) => {
        console.log(err);
      });
  }

```

```js

//단일제품

static findById(id) {
    const db = getDb();
    return db
      .collection("products")
      .find({ _id: id })
      .next()
      .then((res) => res)
      .catch((err) => console.err(err));
  }

하고 ejs 전부 _id 로 바꿔도 동작안함 바꾸는게 잘못된건 아니고 당연히 해야되는데

mongodb id로 인식할수있게바꿔야됨

.find({ _id: new mongodb.ObjectId(id) }) //mongodb =require('mongodb')

```

### update 구현

```js
product class 수정

class Product {
  constructor(title, price, description, imageUrl, id) {
    this.title = title;
    this.price = price;
    this.description = description;
    this.imageUrl = imageUrl;
    this._id = id;
  }
save method 변경

save() {
    let dbop;
    if (this._id) {
      dbop = db.collection("products").updateOne({ _id: new mongodb.ObjectId(this._id) }, { $set: this });
    } else {
    }
    dbop = getDb();
    return dbop
      .collection("products")
      .insertOne(this)
      .then((result) => {
        console.log(result);
      })
      .catch((err) => {
        console.log(err);
      });
  }


// controller

exports.postEditProduct = (req, res, next) => {
  const prodId = req.body.productId;
  const updatedTitle = req.body.title;
  const updatedPrice = req.body.price;
  const updatedImageUrl = req.body.imageUrl;
  const updatedDesc = req.body.description;

  const product = new Product(
    updatedTitle,
    updatedPrice,
    updatedDesc,
    updatedImageUrl,
    new ObjectId(prodId) // mongodb =require('mongodb')
  );
  product
    .save()
    .then(result => {
      console.log('UPDATED!');
      res.redirect('/admin/products');
    })
    .catch(err => console.log(err));
};


// class Product id 수정

this._id = id ? mongodb.ObjectId(id) : null;

자연히 save method부분 도 수정

delete 생성

static delete(id) {
    const db = getDb();
    return db
      .collection("products")
      .deleteOne({ _id: new mongodb.ObjectId(id) })
      .then((res) => console.log(res))
      .catch((err) => console.err(err));
  }
}


```

### mock user

```js
const mongodb = require("mongodb");
const getDb = require("../util/database").getDb;

class User {
  constructor(username, email) {
    this.username = username;
    this.email = email;
  }

  save() {
    const db = getDb();
    return db.collection("user").insertOne(this);
  }
  static findUserId(id) {
    const db = getDb();
    return db
      .collection("user")
      .find({ _id: new mongodb.ObjectId(id) }) // 확실하다면 findOne 메서드 사용
      .next()
      .then((res) => console.log(res))
      .catch((err) => console.err(err));
  }
}

app.js;

app.use((req, res, next) => {
  User.findUserId("6332abc2cc740c5a3ec8309e")
    .then((user) => {
      req.user = user;
      next();
    })
    .catch((err) => console.log(err));
});

class Product {
  constructor(title, price, description, imageUrl, id, userid) {
    this.title = title;
    this.price = price;
    this.description = description;
    this.imageUrl = imageUrl;
    this._id = id ? mongodb.ObjectId(id) : null;
    this.userid = userid;
  }

postAddproduct 수정

const product = new Product(title, price, description, imageUrl, null, req.user._id);

app.js 에서 user 를 넣어놨음으로.

이거근데 안되가지고 중간에 고생좀했다 depth 틀린듯

```
