### path 좀 더 간단하게

```js
router.get("/add-product", (req, res, next) => {
  res.sendFile(path.join(__dirname, "../", "views", "add-product.html")); //이부분을 좀 더 간단하게 만들수있다
});

util 폴더생성 path.js 생성

const path = require("path");

module.exports = path.dirname(process.mainModule.filename);



/// admin js

const rootDir = require("../util/path");

router.get("/add-product", (req, res, next) => {
  res.sendFile(path.join(rootDir, "views", "add-product.html")); 이렇게 변경
});

```

### css import

기존 방식처럼 분명 html 에다가 link 태그로 css를 임포트 했으나 임포트가 안된다.

이역시 path 때문인데

express 를 통해 정적으로 파일을 제공한다는것을 알려야된다

css파일은 public 폴더에 생성한다.

```js

<link rel="stylesheet" href="../public/main.css" />

작동안함


express.static()으로 path.join() 하면

app.use(express.static(path.join(__dirname, "public")));

? 그래도 작동안함


아 public 이라는 경로를 정적 으로 쓰겠다고 전달했음으로 경로를 수정해야됨

<link rel="stylesheet" href="/main.css" />

모든경로는 public 부터시작이므로 생략하고 main.css


```

### 데이터 공유

```js
admin.js

product 변수를 생성해줌

const product = [];


export 시킬건데

module.exports 말고


exports.routes = router;
exports.product = product;

로 변경 단 변경 했으면 당연히 server.js 에가서 고쳐줘야됨

sever.js

const adminData = require("./routes/admin");
app.use("/admin", adminData.routes);


admin.js


router.post("/add-product", (req, res, next) => {
  console.log(req.body); // 이부분 변경할것임
  res.redirect("/");
});


router.post("/add-product", (req, res, next) => {
 product.push({ title: req.body.title });
  res.redirect("/");
});



shop.js


const adminData = require("./admin"); // 임포트

router.get("/", (req, res, next) => {
  console.log(adminData.product); // 여기서 admin js 의 body-parser로 받아온 req.body 값을 넣은 data를 볼수있음
  res.sendFile(path.join(rootDir, "views", "shop.html"));
});

하면 입력할때마다 잘 들어오는것을 확인할 수 있음 그리고 이전에 text 파일 만들었던것과 달리 새로 덮어씌워지는것도 아니고 당연히 계속 push 가능

```
