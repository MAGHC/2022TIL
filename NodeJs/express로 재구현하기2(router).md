### router 구현

app.get 은 app. use 와 비슷하지만

들어오는 get 요청에 대해서 만 처리함

app.post 는 post 만 처리

물론 patch , delete ,put 같은 다른것들도 있음

```js
routes 폴더생성


const express= require('express')

const router = express.Router()

router.get()
router.post()

같은 형식으로 app.get 과 같이 써서 변경

module.export = rotuer


현재코드

const express = require("express");

const router = express.Router();

router.get("/", (req, res, next) => {
  res.send("<form action=/url method=POST><input type=text name=url></input><button>click</button></form>");
});

router.post("/url", (req, res, next) => {
  console.log(req.body);
  res.redirect("/");
});

module.exports = router;



server 혹은 app.js 에선


const routes = require('./routes/파일')

app.use(routes)


역시나 import 해서 쓸 때 순서가 중요하다.

잘못 순서 를 쓰면 경로가 이동안된다 저번처럼


```

### 404 페이지 구현

```js
res.status

res.setHeader 역시 물론 할수있다 send 는 마지막에 쓰면됨

app.use((req, res, next) => {
  res.status(404).send("<h1>not found</h1>");
});


status = 404 는 유효하지 않는 페이지



```

### baseUrl 구현

```js
app.use("/admin", adminRoutes);

와 같이 임포트 시킬때 설정 시켜두면 알아서 다 admin 적용

예를들어

router.get("/url", (req, res, next) => {//알아서 /admin/url
  res.send("<form action=/admin/url method=POST><input type=text name=url></input><button>click</button></form>");
});

from 의 action 도 /admin/url 로 작동하기 때문에 고쳐줘야됨 이런 부분이 살짝 까다로울수있음

router.post("/url", (req, res, next) => {
  console.log(req.body);
  res.redirect("/"); // 이건 /admin 아님
});


```
