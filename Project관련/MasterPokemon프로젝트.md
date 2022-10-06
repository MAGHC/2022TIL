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
