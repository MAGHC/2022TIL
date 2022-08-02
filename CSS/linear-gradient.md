### linear-gradient

선형 그라데이션

- css에서 사용
  background : linear-gradient(blue,green)

이런식으로 파라미터 두개

- 방향설정 가능

background : linear-gradient (to right,blue,green)

right , bottom , top ,left

- 각도사향 가능

맨앞에 70deg

- 2개 보다 많은 색상도 가능 mdn 예시에서는 4가지 까지 보여줌

### js 에서 사용

const body = document.querySelector('body')
하고

body.style.background = linear-gradient 했는데 안먹음

backgroundColor 도 안먹음

backgroundImgae 하니까 먹음

통일해라 좀

### 기울기 적용

linear-gradinent 에

to right bottom 말고 기울기를 적용시킬수있다

그리고 해당 컬러 뒷부분에 몇 %로 채울지도 정할수있음 .

linear-gradient(105deg, rgba($color-white, 0.9) 50%, transparent 50%), url()

요런식으로 참고로 몰랐는데 tranparent 도 색상으로 인식하기때문에 저렇게 사용할 수 있다고한다.

그러면 마치 skew 나 polygon을 사용한거처럼 모양이 휘어있으며

나중에 html 로 요소잡을때도 parent 부분을 안잡고 싶다면 위의 퍼센테이지 값을 참조하여 디자인을 잡으면 된다.
