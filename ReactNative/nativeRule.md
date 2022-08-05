### 네이티브 기본 rule

html 태그를 안쓴다.

기본적으로 모든 view 는

view 컴포넌트 안에 들어가야되며

마찬가지로 text도 text 컴포넌트안에 들어가야된다.(그리고 import 해야된다)

네이티브는 웹이 아니라 앱이라는 사실을 잊지말것

### stylesheet.create()

이것을 쓰면 좋은 점은 자동완성을 제공한다.

css 속성 처럼 쓰면 되는데 속성명은 js 처럼 카멜케이스로 작성한다.

굳이 stylesheet.create() 하지않고 그냥 객체만들어서 해도 되긴 하지만

단점은 자동완성이 되지않는다 .

사용은

<View style={stylesheet.해당스타일}>

### 써드 파티 패키지
