### path

const path = require('path')

문자 그대로 주소관련 모듈인데 이걸 쓰는이유

```js

┣ 📂routes
 ┃ ┣ 📜admin.js
 ┃ ┗ 📜shop.js
 ┣ 📂views
 ┃ ┣ 📜404.html
 ┃ ┣ 📜add-product.html
 ┃ ┗ 📜shop.html
 ┣ 📜app.js

 요런 구조에서


const express = require("express");

const router = express.Router();

router.get("/", (req, res, next) => {
  res.sendFile("./views/shop.html");
});

module.exports = router;

하면 동작을 하지 않는다.

참고로 sendFile 의 경로를 절대경로로 하던 상대로 하던 동작하지 않는다. 절대경로로 해야되는데

절대경로로하면 window 에서 시작하기때문에 이런 문제를 해결하는것이 path 모듈

그밖에 리눅스는 경로를 / 로 들어가고 윈도우는 \ 로 들어가는 문제가있는데 path 모듈은 알아서 잘 변환해줌

path.join()으로 조인 첫번쨰인자는 __dirname = 이프로젝트의 경로를 가리켜줌

res.sendFile(path.join(__dirname, "../", "views", "shop.html")); 와 같은 형태로 사용

```
