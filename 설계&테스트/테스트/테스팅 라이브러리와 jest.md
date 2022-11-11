### 테스팅 라이브러리와 jest 의역할

rtl 테스트를 위한 가상 dom을 제공

브라우저없이 테스트를 진행한다면 클릭요소같은것들을 진행할때 가상 dom 이 필요하다.

가상dom이 원하는대로 작동하는지 확인할수있음

jest 는 테스트 러너

테스트 통과여부를 결정하는 역할을 한다.

### jest 기초 사용

npm test 를 하면 테스트 메뉴 가 뜸 yarn test 도 됨

render method 는 jsx 에 관한 가상 dom을 생성한다.

jsx 에 관한 인수는 app 컴포넌트다.

render(<Login />);

여기에 접근하는방법? = > screen

screen.getByText

모든 dom 에서 텍스트를 찾음 / 정규식을 인수로 넣을수있다.

### aseertion (단언부)

expect 메서드 로 시작

인수 는 단언되는것으로 예측에 들어맞는 지확인하기 위해 jest에서 확인하는것

expect().toBeInTheDocument()

toBeInTheDocument()는 jsetDom에서 온 matcher

가끔 matcher에 인수가있는경우도 있으나 위의경우는 x

위의경우는 문서에 있냐없냐

matcher에 인수가 들어가는 경우

ex) expect(element.textContent).toBe(’hello’)

hello 와 일치해야됨

ex) expect(elementsArray).toHaveLength(7);

jest dom 은 cra 와 함꼐 제공되며 설치된다.

setup.test.js 를 통해 테스트이전에 jest-dom을 가져오기한다

### jest 의 작동원리

est 의 작동원리

rtl 의 역할은 가상돔으로 상호작용하는거

테스트러너가 따로 필요함 ⇒ 테스트를 찾고 실행하며 단언할 뭔가

⇒ 그것이 제스트

mocha나 jasmine 같은것들이있지만 cra에서는 jest를 권장한다.

제스트 워치모드란?

제스트를 실행하는 방법으로

마지막 커밋 이후파일의 모든 변경사항을 확인하여 이후변경된 파일과 연관된 테스트만 실행함

그래서 커밋후 바로 npm test 를 실행하면 커밋이후 변경사항이없다는 메세지가 뜬다.

글로벌 테스트 메서드는 2개의 인자를 가지고있다.

하나는 텍스트설명, 또 하나는 테스트 함수

테스트의 성공과 실패를 판가름하기위해선 테스트 함수를 실행한다.

단언부가 통과되면 pass 아니면 에러

그렇기때문에 빈 테스트도 통과되어야한다.

### jest의 matcher

toBe() 엄격일치비교
toEqual() deep equality 비교
