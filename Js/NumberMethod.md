### 숫자 메서드들

## isNaN()

주어진 값이 isNaN값인지 판별한다
공백을 false 로 처리하기때문에 공백에대한 처리가 따로 필요하며
문자열로 되어있는 숫자의 경우도 거짓처리하기때문에 형 변환을 미리해놓고 비교해야됨

개인적으로 그래서 typeOf !=="number" 따로 넣어둠

https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/isNaN

isNaN() 함수는 어떤 값이 NaN인지 판별합니다. isNaN 함수는 몇몇 혼란스러운 케이스을 가지고 있으므로, ECMAScript 2015에서 추가한 Number.isNaN()으로 바꾸는 편이 좋을 수도 있습니다.

ㅇㅇ Number.isNaN()으로 사용한다

isNaN(NaN); // 참
isNaN(undefined); // 참
isNaN({}); // 참

isNaN(true); // 거짓
isNaN(null); // 거짓
isNaN(37); // 거짓

// 문자열
isNaN("37"); // 거짓: "37"은 NaN이 아닌 숫자 37로 변환됩니다
isNaN("37.37"); // 거짓: "37.37"은 NaN이 아닌 숫자 37.37로 변환됩니다
isNaN("123ABC"); // 참: parseInt("123ABC")는 123이지만 Number("123ABC")는 NaN입니다
isNaN(""); // 거짓: 빈 문자열은 NaN이 아닌 0으로 변환됩니다
isNaN(" "); // 거짓: 공백이 있는 문자열은 NaN이 아닌 0으로 변환됩니다

Number.isNaN(23/0) //0으로나누는것은 무한을 준다 그래서 infinity 를 뱉는데 false 로나온다

그래서 숫자를 판별하기에 온전하진않다

## toFixed()

https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number/toFixed

소수점 반올림 메서드

그냥 toFixed()하면 그냥 반올림

var numObj = 12345.6789;

numObj.toFixed(); // Returns '12346': 반올림하며, 소수 부분을 남기지 않습니다.
numObj.toFixed(1); // Returns '12345.7': 반올림합니다.
numObj.toFixed(6); // Returns '12345.678900': 빈 공간을 0으로 채웁니다.
(1.23e+20).toFixed(2); // Returns '123000000000000000000.00'
(1.23e-10).toFixed(2); // Returns '0.00'
2.34.toFixed(1); // Returns '2.3'
2.35.toFixed(1); // Returns '2.4'. 이 경우에는 올림을 합니다.
-2.34.toFixed(1); // Returns -2.3 (연산자의 적용이 우선이기 때문에, 음수의 경우 문자열로 반환하지 않습니다...)
(-2.34).toFixed(1); // Returns '-2.3' (...괄호를 사용할 경우 문자열을 반환합니다.)

### parseInt, parseFloat

```js
Number.parseInt('2.5rem'); //2

Number.parseFloat('2.5rem'); //2.5
```

문자열에서 값을 읽을떄는 parseFloat 가 좋을것이다.

### isFinite

전역 함수는 주어진 값이 유한수인지 판별합니다. 필요한 경우 매개변수를 먼저 숫자로 변환합니다

이걸 무한대가 나오면 false로 나옴
그래서 이것이 숫자를 확인하는데 궁극의 방법이다.
정수만쓴다는 확신이있다면 isInteger 를 쓰면된다.
