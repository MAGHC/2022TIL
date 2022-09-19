````js
음…?

생각보다 별거없네

그리고 이거 노드 기반인듯

```jsx
function add(a, b) {
  return a + b;
}

module.exports = add;
````

해당js 파일 이름 .test.js

```jsx
const add = require("./test");

it("성공", () => {
  expect(add(5, 5)).toBe(10);
});

모듈 넣어주고

expect() 기대값 넣고 .toBe() 결과값 넣고

packageJson 에서 script 로 가서

아무이름에다가 jest 넣어주면

.test 들어간거 전부 지가알아서 실행함

신기하당

```

타입스크립트는 또 따로있나보다. 그건 또 나중에찾자
