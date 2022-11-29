## MVC

https://www.youtube.com/watch?v=ogaXW6KPc8I

테코톡 영상 참고 했음

model view controller 로

model 은 데이터 view 는 view controller 는 model 의 변경사항 을 적용하는 것 정도로 알고있었음

### 생겨난 이유

코드가 많아지면 파악하기힘듦 -> 유지보수 어려움 -> 이렇게 구성하면 쉽더라 -> 패턴

컨트롤러는 모델과 뷰의 중계자

### mvc 법칙?

1. model 은 컨트롤러와 view 를 의존하면 안된다.
   model 내부에 컨트롤러와 view 코드가있으면 안된다.

2. view는 model 에만 의존해야되고 컨트롤러에는 의존하면 안된다.
   view 내부에는 model 의코드만 있을수있다.

3. view 가 model 로 부터 데이터를 받을때에는 사용자 마다 다르게 보여줘야 하는 데이터에 한해서만 해야된다.

4. 컨트롤러는 view 와 model 에 의존 해도 된다.
   ? 근데 이러면 컨트롤러가 아니고 잡탕아닌가 뭐하러 컨트롤러라고해놓음 셋다 건드려도되는데 최상위 app.js 도아니고 모르겠다

5. view 가 model로 부터 데이터를 받을때 controller에서 받아야된다.

그럼 controlled 된 model 을 받는다 뭐 그런의미겠지?

개인적인 생각이지만 늘 패턴에 크게 목매려고 생각하진 않는다. node 서버는 모르겠는데 이건 이거대로 완전히 분리가 안됨 객체지향에서 mvc패턴인건지 찾아봐야겠네

mvc의 핵심은 로직과 화면을 구분하는것.

고로 model의 원초 생김새의 분리와 model을 controller 하는 class 난 그렇게 생각하는데 어렵네
