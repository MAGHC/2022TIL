### handlebars 문법

app.js 에 가서 view engine 을 바꿔줘야됨

다만 핸들바는 express 에서 자동설치 되지않는 express 패키지 이므로 import

```js
const expressHbs = require("express-handlebars");


pug는 내장형이라서 app.engine 이 필요없지만 얘는 아니라서

app.engine('handlebars',expressHbs()) 첫번째인수 엔진이름 , 엔진()
뭐 에러 먹어서 찾아봤더니 강의랑 문법이 바귄듯

app.engine("handlebars", expressHbs.engine({ extname: "handlebars" }));


app.set('view engine', 'handlebars') // engine 에서 정의한 이름


```
