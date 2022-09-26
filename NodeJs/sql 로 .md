product 추가방법

```js
// /model / product.js

save(){
db.execute('INSERT INTO products (title,price,imageUrl,description) VALUES(?,?,?,?)', [this.title, this.price,this.imageUrl,this.description]) // 당연히 일치해야됨
}
q벨류에 들어가는 ? 는 필드에 대해 하나씩 추가

두번째인수가 넣을 값들

이제 save method를 쓰는곳에 then . catch 로 핸들링 해주면 됨

```

findId 재정의

```js
static findId(id){
return db.execute('SELECT * FROM products WHERE products.id ='?', [id])
}

오 뭔가 알거같애 sql 문법이 어떻게 돌아가는지 대략...


```

### 시퀄라이즈

시퀄라이즈 = 객체 관계형 맵핑 라이브러리

한마디 sql 코드 쉽게 작성하는거

user 에 name,age,emali,password 가 있다면

const user = users.create({

id:

name:

age:

password:})

이렇게 일일이 sql 구문을 작성하는게 아니라 js 객체로 맵핑

npm install —save sequalize

참고로

mysql2 가 있어야됨

```js

// /util/database.js

const mysql = require("mysql2");

const pool = mysql.createPool({
  host: "localhost",
  user: "root",
  database: "node-complete",
  password: "비밀번호
",
});

module.exports = pool.promise();

 이것들을 다 지우고 sequlize 로 새로 작성할것임

sequalize가 mysql2 를 사용함으로 필요없음



const Sequalize = require('sequalize')

const sequalize = new Sequalize()

new Sequalize 의 3가지 인자

데이터 베이스 이름 , 사용자이름, root 비밀번호

4번쨰 인자로 객체 옵션을 전달할 수 도있음

const Sequelize = require("sequelize");

const sequelize = new Sequelize("node-complete", "root", "비밀번호!!", { dialect: "mysql", host: "localhost" });


```

sequelize 로 모델 재작성

기존코드 전부삭제

/model/product.js

```js

const Sequelize = require('sequelize');

const sequelize = require('../util/database');

const Product =sequelize.define('product',{
id:{
type: Sequelize.INTEGER,
autoIncrement: true,
allowNull:false,
primaryKey:true },

title:Sequelize.STRING,
price:{
type:Sequelize.DOUBLE,
}}) )첫번째 인수 모델이름 / 두번쨰 인수 모델 구조 정의(대문자 Sequelize 에서가져올수있음

이런식

전에했던 거 그냥 여기서 다 한번에 정의

const Product = sequelize.define('product', {
  id: {
    type: Sequelize.INTEGER,
    autoIncrement: true,
    allowNull: false,
    primaryKey: true
  },
  title: Sequelize.STRING,
  price: {
    type: Sequelize.DOUBLE,
    allowNull: false
  },
  imageUrl: {
    type: Sequelize.STRING,
    allowNull: false
  },
  description: {
    type: Sequelize.STRING,
    allowNull: false
  }
});


	sequelize.sync()모든 모델을 살펴본다.

sequelize
  .sync()
  .then((res) => {
    console.log(res);
    app.listen(3000);
  })
  .catch((err) => console.log(err));


  // /controller/ admin.js

exports.postAddProduct = (req, res, next) => {
  const title = req.body.title;
  const imageUrl = req.body.imageUrl;
  const price = req.body.price;
  const description = req.body.description;
  Product.create({
    title: title,
    price: price,
    imageUrl: imageUrl,
    description: description
  })


  exports.getProducts = (req, res, next) => {
  Product.findAll()
    .then(products => {
      res.render('shop/product-list', {
        prods: products,
        pageTitle: 'All Products',
        path: '/products'
      });
    })
    .catch(err => {
      console.log(err);
    });
};

가져오기

하나만 가져오기

Product.findAll({ where: { id: prodId } })
    .then(products => {
      res.render('shop/product-detail', {
        product: products[0],
        pageTitle: products[0].title,
        path: '/products'
      });
    })
    .catch(err => console.log(err));

where 쿼리 사용


```

### 업데이트

```js
exports.postEditProduct = (req, res, next) => {
  const prodId = req.body.productId;
  const updatedTitle = req.body.title;
  const updatedPrice = req.body.price;
  const updatedImageUrl = req.body.imageUrl;
  const updatedDesc = req.body.description;
  Product.findById(prodId)
    .then((product) => {
      product.title = updatedTitle;
      product.price = updatedPrice;
      product.description = updatedDesc;
      product.imageUrl = updatedImageUrl;
      return product.save();
    })
    .then((result) => {
      console.log("UPDATED PRODUCT!");
      res.redirect("/admin/products");
    })
    .catch((err) => console.log(err));
};

//삭제

product.destroy();
```

### mock user 작성

```js
const Sequelize = require("sequelize");
const sequelize = require("../util/database");

const User = sequelize.define("user", {
  id: {
    type: Sequelize.INTEGER,
    autoIncrement: true,
    allowNull: false,
    primaryKey: true,
  },
  name: Sequelize.STRING,
  email: Sequelize.STRING,
});

module.exports = User;
```

//app.js

```js
const Product = require("./models/product");
const User = require("./models/user");

Product.belongsTo(User);

두번째 인수로 관계를 설정할 수 있다.

Product.belongsTo(User, { constrainst: true, onDlete: "CASCADE" });

제약 : true
사용자를 삭제하면 관련된 모든것을 삭제 .



이미 제품 테이블을 설정한 상태이기때문에

sequelize
  .sync({ force: true })

로 강제로 덧붙임

더미유저 작성

sequelize
  // .sync({ force: true })
  .sync()
  .then(result => {
    return User.findById(1);
    // console.log(result);
  })
  .then(user => {
    if (!user) {
      return User.create({ name: 'Max', email: 'test@test.com' });
    }
    return user;

    findById를 읽는 미들웨어 작성

app.use((req, res, next) => {
  User.findById(1)
    .then(user => {
      req.user = user;
      next();
    })
    .catch(err => console.log(err));
});


이제 이 시점부터 생성되는 모든 새 재품은 로그인 한 사용자와 연결되어야 함

컨트롤러에 postAddproduct 를 변경해야됨

create({}) 에  userId:req.user.id

추가하듯이

연관을 설정하는 특수한 시퀄라이저 메소드

req.user.createProduct()

```

### model/cart 변경

약간 후회하고있다 node 걍 레파지토리 만들어서 첨부터관리하면 일일이 이렇게 안적어도 커밋내역에 다 남는걸 ; 지금부터 할까 하다가도 좀 멀리온거같기도

아무튼 sql 끝나고 non sql로 가면 고려좀 해봐야겠다

```js
const Cart = sequelize.define("cart", {
  id: {
    type: Sequelize.INTEGER,
    autoIncrement: true,
    allowNull: false,
    primaryKey: true,
  },
});


/model / cartITem 생성

const Sequelize = require('sequelize');

const sequelize = require('../util/database');

const CartItem = sequelize.define('cartItem', {
  id: {
    type: Sequelize.INTEGER,
    autoIncrement: true,
    allowNull: false,
    primaryKey: true
  },
  quantity: Sequelize.INTEGER
});

module.exports = CartItem;


app.js


Cart.belongsTo(User);


Cart.belongsToMany(Product, { through: CartItem });// 두번째 인수로 연결위치 알려줌
Product.belongsToMany(Cart, { through: CartItem }); //다 대 다

```
