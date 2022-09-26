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
