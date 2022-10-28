### 코드 명명 원칙

명시적으로 작성할것

기본 카멜 케이스

상수 - 전부 대문자

const COLOR_RED = "#F00";

클래스 - 대문자 시작

class Person

함수 - 동사형으로 작성

불리언 -is 용법 사용

# eslint 규칙

### Expected literal to be on the right side of <=. (yoda)

```js
if (1 <= left && right <= 400 && right === left + 1) 가;

if (left >= 1 && right <= 400 && right === left + 1) 이렇게;
```

포인트 :변수를 리터럴 값과 비교하는 일관된 스타일의 조건을 적용하는 것
