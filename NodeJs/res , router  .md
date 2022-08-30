### res 체험

```js

const server = http.createServer((req, res) => {
  console.log("유알엘", req.url, "메서드", req.method, "헤더", req.headers);

  res.setHeader("Content-Type");
});

setHeader 로 헤더를 설정할 수 있으면 실제로 Content-Type 은 브라우저가 알고 이해하는 기본 헤더임

두번째 벨류로 헤더키에 대한 값을 설정함

res.write

write 는
응답에 일부 데이터를 쓸 수 있다.


res.setHeader("Content-Type", "text/html");
  res.write("<html>");
  res.write("<head><title>실험용</title></head>");
  res.write("<body><h1>내 첫 node 서버 </h1></body>");
  res.write("</html>");
  res.end();


end() 로 끝도 설정해줘야된다. 참고로 저렇게 했다가 다 깨졌는데 아마 어디 인코딩같은걸 안해줘서 그런거같다. 그래서 영어로 다 바꿈

다만 저렇게 하니까 html 이 제대로 나오는걸 보고 신기했지만 한편으로는 끔찍했다

express 를쓰면 다 해결된다고한다.



```

### 라우터 구현

생각보다 간단했다.

이미 이전에 req.url 로 url 을 parsing 할 수 있었다

다른 경로는 어떻게 routing 하느냐? if 쓰면된다.

```js

if (url === "/") {
    res.write("<html lang=ko>");
    res.write("<head><title>send Message </title></head>");
    res.write("<body><form action=/message method=POST><input name=message type=text><button type=submit>send</button></input></form></body>");//name 설정으로 name 이 키인 벨류를 넣는다

    res.write("</html>");
    return res.end();
  }

return 을 적은 이유는 전에 적었던 setHeader 가 실행되지 않게 하려고

메인 경로 에 들어가면 유저가 메세지를 보낼 수 있는 화면이 나온다.


```

### 유저의 메세지 받기 1 (post 수신)

```js
 res.write("<body><form action=/message method=POST><input name=message type=text><button type=submit>send</button></input></form></body>");//name 설정으로 name 이 키인 벨류를 넣는다

보면 method 도 POST 로 설정한 것을 알 수 있다.

고로 if 를 추가하자

const method = req.method;

if (url === "/message" && method == "POST") {
    fs.writeFileSync("message.txt", "DUMMY");
    res.writeHead(302, {}); //staus 코드와 객체를 넣어서보내줄것임
  }


전에 썼떤 fs 모듈을 불러와서 쓴다.

writeHead 부분은

res.statusCode = 302;

302 = redirect 코드



res.setHeader('Location', '/')
로 풀어서 쓸 수 도있다.


위의 코드는 참고로 유저가 적은 input 값이 아니고 dummy를 일시적으로 기록하게 끔 되어있음







```

### 유저의 메세지 받기 2 (버퍼)

req.on()

on method로 이벤트를등록할수있다.

종류는 한정되어있음

close , err, data , pause ,readable, resume 이렇게 autocomplete 에 있네

```js
req.on("data", () => {});

두번째 인수로 모든 data 이벤트에 대해서처리할 기능을 작성

말그대로 이벤트 작성하는거네

const body = [];
    req.on("data", (event) => {
      console.log(event);
      body.push();
    });
    req.on("end", () => {
      const parsedBody = Buffer.concat(body);
    });

buffer 키워드를 이용해 연결한다. 나의 바디와

const parsedBody = Buffer.concat(body).toString();

버퍼링된 바디를 문자열로 변경 // 실제로 input 에 text를 보내기 때문에 이렇게 해도됨

const parsedBody = Buffer.concat(body).toString();

parsedBody 는 console에 찍으면

input 에 설정해줬던 name 값인 message = 입력한 값

형태로 나온다.

const message = parsedBody.split("=")[1];
이것으로 이제 유저가 input 에 적은 value를 취할 수 있다.


또한 data 에 의존하는 메서드가있다면 eventlistener 안으로 넣어야된다.






```

전체코드

```js

전체코드

const http = require("http");
const fs = require("fs");

const server = http.createServer((req, res) => {
  const url = req.url;
  const method = req.method;

  if (url === "/") {
    res.write("<html lang=ko>");
    res.write("<head><title>send Message </title></head>");
    res.write("<body><form action=/message method=POST><input name=message type=text><button type=submit>send</button></input></form></body>");
    res.write("</html>");
    return res.end();
  }

  if (url === "/message" && method == "POST") {
    const body = [];
    req.on("data", (event) => {
      console.log(event);
      body.push(event);
    });
    req.on("end", () => {
      const parsedBody = Buffer.concat(body).toString();
      const message = parsedBody.split("=")[1];
      fs.writeFileSync("message.txt", message);
    });

    res.statusCode = 302;
    res.setHeader("Location", "/");
    return res.end();
  }
  res.setHeader("Content-Type", "text/html");
  res.write("<html lang=ko>");
  res.write("<head><title>test!</title></head>");
  res.write("<body><h1>first node </h1></body>");
  res.write("</html>");
  res.end();
});

server.listen(3000);


매우 머리아파보이겠지만 express 라는 프레임워크로 다 편하게 작성할수있을것이라 한다.

지금 이것은 원시적인 로직

그리고 해봤는데 message가 생기고 message가 저장되긴하는데 쌓이진 않는다 그건 또 다른 로직인듯

인코딩도 잘안되고


```
