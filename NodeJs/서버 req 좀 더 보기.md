### req,res

서버만들기에서 했던

```js
const http = require("http");

const server = http.createServer((req, res) => {
  console.log("유알엘", req.url, "메서드", req.method, "헤더", req.headers);
});

server.listen(3000);

이부분에서의 req 의 맨위를 보면

서버를 실행시키고 봤던 콘솔로그를 보면

맨위에 header 가있음을 볼 수 있다 .

헤더에는 메타 정보가 있고 메타 정보는 요청에 추가되고 응답되는것이 적혀있다.

호스트가 들어있고

어떻게 캐시를 처리해야되는지 , 어떤 브라우저인지 어떤 종류의 응답을 수락하는지, 대역폭 , 쿠키까지

이중 가장 중요한 필드중 하나는 url 이다



/*

$ node server.js
유알엘 / 메서드 GET 헤더 {
  host: 'localhost:3000',
  connection: 'keep-alive',
  'sec-ch-ua': '"Chromium";v="104", " Not A;Brand";v="99",
"Google Chrome";v="104"',

*/

url 이 안보이는 이유는 기본적으로 localhost는 슬래쉬로변환됨

주소창에

http://localhost:3000/test

하면

유알엘 /test 메서드 GET 헤더 {
  host: 'localhost:3000',
  connection: 'keep-alive


보시다시피 test가 생김



```
