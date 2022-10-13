### MasterPokemon

어제부터 이 프로젝트를 진행하려고한다.

생각해보니 9월 한달동안 노드도 꽤배워서 파이어베이스 나 몽고디비 안쓰고도 그냥

내가 노드로 서버 구현 할수도있겠는데? 싶어서 외부 public api로 만들어봐야겠다 싶어서 시작하게되었다.

### req.body 가 비어서 오는 문제

일단 기본적으로 세팅해놓고 req.body 를 console 에 찍었는데 나오질 않았다

뭐지? body-parser 도 쓰고있는데 왜 ?

했는데 cors 에러가 뜨기에 app.use(cors())도 하고

json 변환작업도 하고

```js
app.use(express.json());
app.use(bodyParser.urlencoded({ extended: true })); // 확장도 트루로함
app.use(bodyParser.json());
```

했는데 왜 안되지? 계속 뭔 header 뭔 에러가 떳다.

node 배울때 사실 form 에 action 가지고 엔드포인트 설정하고 method 로 보내줬어가지고 내가 프론트니까 그냥 메서드 만들어서 fetch로 컨텐츠 타입 이랑 다 해서 보내줬는데 이번엔 또 비어서 오는게 아니고 아예 json parse 문법에러가 떴다.

이상하다? 전에 원티드 프로젝트 쓸땐 물론 그건 서버사양이 내가 만든건 아니지만 알아서 잘 돌아갔는데 왜 이건안되지 싶어

그땐 axios 를썼던게 기억나서axios 썼더니 귀신같이 해결됬다

cors를 잘 몰라서 일어난 일인거같기도하다 . 이거하다가 어제 하루 다 날라갔지만 재미있었음

### node js require vs import

갑자기 궁금했다 생각해보니 둘다 js 라 import 도 쓸수있을텐데 차이점이 뭘까?

검색해서 찾아봤다.

그중에서 스택오버 플로우에 나랑 비슷한 의문을 가진 사람을 비슷한 예제로 찾은거 같아서 가져왔다 추천도 많고 1달전이네

[https://stackoverflow.com/questions/46677752/the-difference-between-requirex-and-import-x](https://stackoverflow.com/questions/46677752/the-difference-between-requirex-and-import-x)

**require로 필요한 부분만 선택적으로 로드할 수는 없지만 import를 사용하면 필요한 부분만 선택적으로 로드할 수 있어 메모리를 절약할 수 있습니다. 로드는 동기식(단계별)으로 요구되는 반면 가져오기는 비동기식일 수 있으므로(이전 가져오기를 기다리지 않고) 요구사항보다 약간 더 잘 수행할 수 있습니다.**

앞으론 import 를 써야되겠네 그럼

애초에 es6 문법이 import

그런 이유로 require 를 import로 다 바꾸기로했다 근데 ㅋ 진짜 별거아닐줄알았는데 엄청나게 시간을 써먹었다.

아니 내착각이고 사실 별로 안쓴것일수도 하여간

```js

"type": "module",

쓰려면 pacagke.json 에 type:"module" 추가해줘야 됨
"name": "todos-backend",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "type": "module",

```

근데 안됬다 그러니까 다른 lib 들은 import 가 잘됬는데 내가 생성한 파일들이 import 가 안됬다

에러메세지 하는말이 did you mean ../ ? 하면서 경로 틀린거아니냐고했는데 전혀 아니였다

한참 해맸다 근데 결국.... 검색하다가 찾아냈다

노드 js 의 import 를 위해서는 경로에 확장자까지 적어줘야된다고..

이는 브라우저에서 import
가 작동하는 방식과 맞추기 위해서 의도적으로 설계된 부분이라고 한다...

### git 사용하면서 겪은 문제

어느순간 내 깃의 클라이언트 폴더에 화살표 가 떳다. 이유는 뭔지 알거같았다.

내가 갑자기 프로젝트 폴더에 client / server package.json이 따로있는거 마냥 깃도 따로해놓으면 따로따로 올라가나 싶어서 클라이언트 안에 따로 git init 을 해놓고 만들어놓은게 폐단이였다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aa3b01d0-3db6-4e2c-a1e9-83d5715c523c/Untitled.png)

그리하여 누르게 되면 폴더도 안뜨고 이런식의 화면만 뜨는 현상이 발생했다.

사실 그 이전에 git push -f origin master로 그냥 밀어버렸는데 결국 ㅋㅋ...

신기한건 커밋은 따로 누적되고있었다.

당연히 1차원적인 생각으로 만들었던 client 폴더안의 git 폴더를 지워버리면 되겠지 했는데 여전히안됬다.

프로젝트 최상위 폴더 (클라이언트, 서버가 다보이는곳 ) 에서

```jsx
git rm --cached . -rf
```

명령어를 통해 캐시되어있는 스테이징 파일을 지워야된다.

그 뒤 git add / commit / push 를 하면 정상적으로 돌아온것을 볼 수 있다.

브랜치를 따로 파야되는건가 하면서 별 쌩쇼를 다했다 새로 밀어야되나... 하면서
