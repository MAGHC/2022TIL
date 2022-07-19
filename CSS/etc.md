### 높이나 넓이만 설정해도

css 에서 알아서 비율을 설정해준다.

### backface-visibility

backface-visibility: hidden;

애니메이션 사용시 지들끼리 시키지도않은 위로 혼자 올라가는 알수없는 현상 발생시 부모요소 에 넣어주면 해결됨

참고로 이 속성은 요소의 뒷면을 사용자에게 보여줄건지 정하는 속성

### :link :visited

링크 에 접속전 / 접속후

### :not(:last-child)

:not(:last-child){
margin-right : 20px;

}

하게 되면 last-child 에서만 제외하고 margin-right를 적용한다.

### [class^="col-"]

컬리브라켓으로 ^= 로 하면 해당문자열로 시작하는 모든 클래스를 다 선택할수있음
