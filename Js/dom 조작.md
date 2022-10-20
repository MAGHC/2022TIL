### document.getElementById()

id를 통해 element 반환

ex)

const title = document.getElementById("title")

### document.querySelector()

selector 의 구체적인 그룹과 일치하는 document 의 첫번째 element를 반환

querySelector : 첫번째 값 하나
querySelectorAll : 전부다

### 차이점

get이 속도 더 빠름

### 공통점

일치하는 값이 없다면 null반환

### 이벤트 리스터

해당 이벤트를 읽고 어떤 function을 취할것인지

title.addEventListenr("읽을 이벤트", 실행할 미리 적어둔 함수 )
or
title.addEventListenr("읽을 이벤트",()=>{}) 그냥 화살표함수로 바로 적어도 됨

### setAttributes

h1.setAttributes('class','title') //<h1 class="title'><h1>

### 이벤트리스너 forEach

ul 안에있는 li들을 이벤트를 줄때 보통 forEach 문으로 처리하곤하는데

이는 좋은 방법이아니다.

ul 을 잡은다음

ul에 이벤트리스너를 놓고 이벤트 타겟의 태그이름이 맞다면? 으로 진행

if(event.target.tagName == "Li")
