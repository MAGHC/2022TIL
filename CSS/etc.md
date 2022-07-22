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

### width 와 max-width의 차이

width 속성과 max-width는 비슷해보이지만
width 는 요소크기를 100%로 유지
max-width 는 기본요소 크기 이상으로는 크기가 조절되지 않음

### Emmet lorem

알다시피 lorem 어쩌고 라틴어 나오는 그 텍스트 단을 써먹을수있다

### html 특수 심볼

&rarr

=> 이런식으로 표현 가능

https://css-tricks.com/snippets/html/glyphs/

여기서 확인

### 작은 단위의 unit 이라면 일일이 반응형 단위를 쓰지말 것

아주 작은 단위의 unit 이라면 1px 2px 가지고도 반응형을 쓰면 두배 차이가 나게됨으로 굳이 일일이 아주작은 단위에까지 반응형 단위를 쓰지말것

### skew

기울기. deg

### text-align

text-align 은 부모요소에다가 적용해야지 가운데로 정렬이된다.. 뭣도 모르고 텍스트 자체에다가썼는데 안되서 살짝 고생

### -webkit-background-clip

-webkit-background-clip:text

하게되면 background 가 text에 맞춰서 짤리게 된다.

참고로 color: transparent를 해줘야 color 가 투명해지면서 배경색이 드러나게된다.

### outline

테두리선 border 보다 밖의 선의 개념 인듯
outline: 1.5rem solid $color-primary;

border랑 비슷함 설정값

outline-offset: 2rem;
border와 outline 의 패딩 값이라고 할까

### 이미지

이미지 같은 경우에는 가능한 백분율로 표시 뷰포트에 맞게 멋지게 확장됨

### &>\*

& > \* 선택자 여기까지있던 것의 밑에 요소들 모두
