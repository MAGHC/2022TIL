### BEM

build 할때 따르면 좋은 방법론

Block\_\_element--modifier

block : 자기스스로 의미를 가짐 // box header 등등
이건 \_\_로 구분

element : 말그대로 element button input etc

modifier : 다른버젼 // logo--white
-- 로 구분

### architecture

7-1 패턴

base
사이트 디폴트 스타일

componetns
각각의 컴포넌트 스타일

layout
전체레이아웃

pages
페이지 스타일

themes
다양한 시각적 테마

abstracts
css를 출력하지않는 코드를 넣는곳
variable
mixin
function
place holder

vendor
외부라이브러리 , 프레임워크
\_\_bootsrap.scss
jquery 등등
