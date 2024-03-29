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

### -moz-

파이어폭스에서도 사용할수있게.

### background-blend-mode

    배경과 혼합하는 방식에 대해서 설정 가능 마치 포토샵 처럼

    ie 나 edge에선 호환이 안됨으로 크롬 개발자도구에서 속성확인

background-blend-mode: screen;

원래는 필요없는데 카드 이중 구조 만들고

backface visiblity hidden 해놔서 사용

### blur

filter:blur(3px);

흐름 효과 활용 뭔가 또 css만의 트릭을 쓰는걸까 했는데 그런거없었다

### :hover 시 다른 class 애니메이션 효과

ex)&:hover &image{

}

그냥 옆에다가 쓰면됨

### shape-outside

-webkit-shape-outside: circle(50% at 50% 50%);
shape-outside: circle(50% at 50% 50%);
-webkit-clip-path: circle(50% at 50% 50%);
clip-path: circle(50% at 50% 50%);

와같이 쓰면 이미지도 동그랗게 해당 태그의 박스 shpae 도 동그랗게 잡혀서 옆에 컨텐츠들도 동그란 테두리에 맞게 배치된다.

### input 의 font 값 // valid

원래는 자동상속인데

input 의 font 값은 상속되지않아서

css에서 font-family - inherit 을 선언해줘야 자동 상속이된다.

어찌보면 당연한 거지만 새삼 신기했던게 css 가상 선택자에 invalid 가 있었다.

그래서 일반적으로 보는 invalid 인지 아닌지에 따른 변화를 직접 줄수있음

### foucs

focus 는 마우스 없이 키보드로만 움직이는 사람들을 위해서라도 굉장히 중요하다.

### 형제 요소 선택자 1

'+' 사용

.a + .b 같은 형태로 사용하는데
html 순서대로 해야 선택가능하다 .

### 형제 요소 선택자 2

'~' 사용

a~b a 요소가 앞에 존재하면 b 를 선택한다 이또한 순서가 맞아야된다.

a가 b 보다 먼저등장하지않으면 선택안됨

### 의사클래스 :checked

:checked 말 그대로 라디오 인풋의 체크 상태를 확인한다.

### radial-gradiant

안에서 밖으로 그라데이션

### cubic-besire

애니메이션 타이밍에 ease-in 같은 것 넣을때 cubic-besire 속성을 넣을수 있다.

참고로 값은 그냥 구글에 cubic-besire 쳐서 그냥 보면되는데

개꿀인 점은 애니메이션이 언제 멈췄다가 언제 어디까지 퍼지고 하는 것들을 핸들링 할 수 있다. 이걸 어따쓰지 했는데 만져보고 적용해보니까 생각보다 멋있었다.

### transform-origin

Transform-origin 값을 설정함에 따라 어디를 기점으로 rotate 시킬건지를 지정할 수 있다.

지정하지않으면 가운데 기준으로 돈다 .

### column

column-count: 2

로 단락을 나눌 수 있다. 개멋있다

column-rule: 1px solid black;

로 단락 사이에 border를 생성할 수 있다.

hyphens: auto;

로 자동으로 hypen을 넣어줄 수 도 있지만 이게 제대로 되려면

html 시작 부분에 lang ="en" 처럼 언어 가 제대로 설정되어있어야 되 서 내생각에 hypens 은 별 큰 의미는 없는 듯 하다.

### 스타일 컴포넌트에서

꼭 굳이 스타일 컴포넌트에만 국한된 이야기는 아니라서 적는다

글로벌 스타일을 지정하고 있었는데 provider 를 통해 theme 가 전달이 잘 되고있었다.

실제로 값은 들어오고있었는데 잘못된 속성값이라고 적혀있고 계속 적용이 안되었다

mixin도, color 도 css가 참 답답한게 에러가 정확히 명시적으로 안뜬다

덕분에 한참을 생각하는데

color:"e1e1e1" 이런식으로 넣어놨었다. 이것의문제는 # 이없다는거

잘못된 속성값이라는게 css 적인 문제겠거니 하고 처음에는 provider 문제라고 생각했다가 점차 점차 검색하고 줄이고 실험하다가 찾았다 역시나는 아직 주니어 구나 하고 다시한번느꼈다.

mixin 이 안먹은 이유는
`display:flex, justify-content:center,`

와 같이 적었기 때문이다 mixin 은 금방찾았다 color 의 오류를 잡아내고 나자마자 아 그럼 이건 그거 때문에 안됬겠네 하고 문제점이 잘 보였다 한동안 scss만 쓰다가 스타일 컴포넌트 다시 쓰니까 좀 햇갈리긴하다.

### variables

:root{

--text-size: 16px;

}

과 같이 사용 가능하다 해당 클래스 내에서만 선언할수도있는데 보통은 루트에 선언하여 사용한다고 한다.

활용으로 미디어 쿼리안에

@media screen and(max-widht:768px){

    :root{
        --text-size:16px;
    }

}
같이 해놓고 활용 가능하며

--로 정의 위의 상태는 정의만해놓은 상태고

사용은 var(--text-size) 로한다

### background 이미지 넣을 때 유의사항

```css
#home {
  background: url("../imgs/background.png");
}

url 넣을때 주의사항 컴파일되는 css 파일 있는 곳 기준으로 경로 작성해야됨 왜 안되나 했네 ㅅ


```

### flex-grow / wrap

wrap을 알아다시피 알아서 화면에 맞게 요소를채워주고
flex-grow:1 // 하게되며 알아서 화면을 매꿔준다 (최근에 반응형에서 사용)
