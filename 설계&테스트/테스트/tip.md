### 에러처리문 테스트

thorow 한 error 를 테스트할때 유의할점은

expect()를 한번더 래핑해야된다

[https://stackoverflow.com/questions/46042613/how-to-test-the-type-of-a-thrown-exception-in-jest](https://stackoverflow.com/questions/46042613/how-to-test-the-type-of-a-thrown-exception-in-jest)

기존 함수가 인수 집합과 함께 발생하는지 여부를 테스트해야 하는 경우 의 익명 함수 안에 이를 래핑해야 합니다 `expect()`.

```js
test("Test description", () => {
  expect(() => {
    http.get(yourUrl, yourCallbackFn);
  }).toThrow(TypeError);
});
```

### 배열 deep equality 테스트

배열은 참조 타입임으로 엄격일치 동등연산자 , toEqual 로 하면 실패가난다

고로

JSON.stringify() 를 활용하여 비교한다. 객체도 가능한듯

```js

describe("기능 테스트", () => {
  test("입력받은 문자 배열로 만드는 기능", () => {
    const input = 123;
    const result = JSON.stringify(App.convertUserNumberToArray(input));
    const answer = ["1", "2", "3"];

    expect(result).toEqual(JSON.stringify(answer));
  });

```
