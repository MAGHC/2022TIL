### 컬러가 바뀌는 테스트앱 작성해보기

버튼을 누르면 빨간색에서 파란색이되고 다시 누르면 빨간색이되는
screen 을 통해 요소를 찾는데 요소에 어떻게 접근? ⇒ 역할
[https://www.w3.org/TR/wai-aria/#role_definitions](https://www.w3.org/TR/wai-aria/#role_definitions)

jest dom 에 대해서 확인하는곳
[https://github.com/testing-library/jest-dom](https://github.com/testing-library/jest-dom)

\***\*Table of Contents\*\***

에서 mathcer를 볼 수 있다.

테스트 케이스를 작성해놓고

바로 돌려서 실패 확인

이게 레드 테스트 이걸로 절반은 한거라고한다...

?
뭐하여간

진행중에 오류가떴다

하다가 에러가떴다.

\***\*(React) Element type is invalid, expected a string (for built in components) or a class/function but got\*\***

? 컴포넌트의 타입이 인발리드라 뭔가 임포트가 잘못된거같은데 하고 찾아보니

내가 import 를 습관적으로 중괄호로 했다 .

export default 했으면 중괄호가 필요없는데 자꾸 습관적으로 {}를 붙여서하게된다

버튼을 찾을때 name을 안붙여도 되지만 붙이는게 좋은 연습이된다.

유닛 테스트의 경우에는 테스트 하나에 하나의 단언만 나오는것을 선호

하지만 기능 테스트의 경우에는 나중에는 여러작업에 관한것이 된다.

```js
test("button has correct initial color", () => {
  render(<Color />);
  const colorBtn = screen.getByRole("button", { name: "색상변경" }); //button 과 text 를 테스트한다

  //
  expect(colorBtn).toHaveStyle({ backgroundColor: "red" });
});

test("button turns blue when clicked", () => {
  render(<Color></Color>);

  const colorBtn = screen.getByRole("button", { name: "색상변경" });
});
```

작성하다 말아가지고 ; 하여간 지금은 이런상태

testing library 에서 fireEvent 를 임포트 이게 상호작용을 돕는다.

fireEvent.click(colorBtn);

이게 클릭한거임

expect(colorBtn.textContent);

로 textContent 확인가능

순차적으로 내려오다가 실패하면 그 밑에 테스트는 실행하지않는다 .

break

그래서 테스트 마다 하나의 단언을 두는게 좋지만 기능 테스트에선 실용적이지않다.
