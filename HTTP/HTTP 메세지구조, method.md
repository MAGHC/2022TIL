### 메세지 구조

스타트 라인
헤더
공백라인
바디

로 이루어져있다.

시작 라인에는 요청라인(request-line )과 status-line 으로 이루어져있는데

요청라인에는 http 메서드, 요청대상 , 타켓, http 버젼이 있음

ex)GET/search?q=hello HTTP/1.1

method SP(스페이스바=공백 이란뜻) request-target SP HTTP-version CRLF(엔터)

요청메세지-요청대상

절대경로="/"[?query]

응답 메세지(status-line)

200 : 성공
400: 클라이언트 요청오류
500: 서버오류

200 ok 에서 ok 이유문구 사람이 알아먹을수있는 짧은 설명

- 헤더

전송에 필요한 모든 정보가 들어가있음

바디의내용,크기 압축, 인증 , 요청(클라이언트 정보), 서버정보 등등

필요시 임의의 헤더 추가가능

Content-Type

- 바디

실제로 전송한 데이터

html문서, 이미지, 영상,json 등등

? 크게 성공하는 기술은 단순하고 확장 가능한 기술 => http 가 그렇다

### method

api url을 디자인할때

리소스와 행위를 분리하면된다.

resource 와 method

### 메서드의 종류

get, post ,put , delete ,patch
조회, 등록, 대체, 삭제 , 부분 변경

기타 : head ,options,connect,trace
헤더만 변경,옵션설명(cors에서사용),서버터널 설정,리소스에 따른루프백테스트 수행

### get

get을 통해사실 메세지 바디를 사용하여 보낼수는 있지만

전송받을때 처리안하므로 무의미

### post

핵심은 메세지 바디를 통해 서버로 요청을 전달

포스트는 의미가 되게많다.

댓글 , form / 새로운 리소스 (신규 주문 생성) // 기존자원에 데이터 추가 (이건 put 이나 patch아님 ? )

정해진것이없음

post 요청이 오면 리소스마다 어떻게 해야될지 알아서 해야됨

url을 디자인할때 동사의 url 이 후에 나오게 될 수 도있다.

리소스 와 메서드 만으로 분리가 되면 이상적인데 현업에서 그럴 수 없는 상황도 생기기떄문이라고 ..

=> 재정리

동사의 url 가 나올수있는데 이것은 컨트롤 url 라고한다

리소스만으로 url 를 다 설계하면 베스트지만 어쩔수없으면 컨트롤 uri 를 사용

조회데이터를 get으로 받으면 안받는 서버도 많기때문에 조회형이지만 post 로

사실 post는 모든걸 할 수 있다.

하지만 약속된걸 써야. get은 캐싱이 쉽지만 post는 캐싱이 어렵다거나 하는 일들이 있기 때문.

### put

리소스를 대체한다. (완전히)
리소스가 없으면 생성한다.

중요한 것은 클라이언트가 리소스를 식별한다는 점이다.

post 에선 members/ 로끝이라면
얘는 members/100 과 같이 id 든 뭐든 알고있다.

### patch

완전히 대체하는 것의 단점을 이해하여 부분적으로 변경하고싶다 ⇒ patch

딜리트는 뭐 ... 그냥 제거

### 메서드의 속성

-safe

말그대로 다만 세이프의 기준? = 호출해도 리소스가 변경되지않음 ex)get

- 멱등

idempotent

한번 호출하던 몇번 호출하던 결과가 똑같다.

get ⇒ 몇 번 호출해도 똑같다.

put 도 멱등 ⇒ 똑같은 욫청을 여러번 해도 최종결과는 같다.

delete 도 멱등 : 몇번 삭제해도 결국 결과는 같다.

post 는 아님 ex) 결제

멱등이라는 개념이 필요한 이유?

⇒ 자동 복구 메커니즘 ⇒ 서버에서 성공했는지 안했는지 몰름 그럼 계속 delete 시도 의 판단 근거

단 , 멱등은 외부 요인으로 리소스가 변경되는것은 고려 안함

예 ⇒ get 계속하고있는데 다른사람이 put 해서 고쳤을때 get 결과가 바뀜

내가 계속 요청했을때만 고려함

- 캐시 가능

캐시가능

응답 결과 리소스를 캐시해서 사용해도 되는가?

캐시? 웹 브라우저에 큰 이미지 요청 ⇒ 로컬 pc에 웹브라우저가 저장 (다시 요청 x)

get head post patch 캐시가능스펙상 ㅇ

실제로는 get, head 만 사용

⇒ 캐시를 하려면 key가 맞아야되는데 post 같은것들은 본문 내용까지 캐시키로 고려해야 해서 구현이 쉽지 않다.
