### 클라이언트 서버구조

Request Response 구조

클라이언트는 서버에 요청을 하고 무작정 응답이 올때까지 대기

서버가 요청에 대한 결과를 만들어서 응답

### 무상태 프로토콜(stateless, stateful)

http는 무상태 프로토콜을 지향

stateless = 상태를 유지하지않는다
stateful = 상태를 유지한다

무상태를 지향하는이유? 상태를 유지하려면 서버가 다 기억해야됨

서버를 바꾸면 ? 상태가 다 날라가서 모름

무상태로 하게된다면 = > 서버를 무한 증식시켜도 괜찮

무상태는 스케일아웃 (서버확장) 에 유리하다

흠 맞는 생각인지는 모르겠는데 이게 프론트라는 분야가 생긴이유중 하나라고 봐도되는건가? 뭐 쩃든

stateless 의 실무한계

사실 모든걸 무상태로 할 수는 없다.

로그인 같은거

로그인한 상태를 서버에 유지해줘야 한다.

일반적으로는 브라우저의 쿠키나 세션을 통해 상태를 유지한다.
상태 유지는 최소한 만 사용
state less 의 단점 ⇒ 데이터 전송이 많음 (저장을 안하다보니)
