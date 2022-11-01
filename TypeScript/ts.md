### const , let

const 키워드는 굳이 타입을 안줘도됨 알아서 추론

let은 타입을 주는것이좋다.

타입스크립트의 타입은 컴파일중에 확인되지만 자바스크립트는 런타임 중에 확인된다.

### object

자바스크립트에서의 객체는 키 벨류가 한페어이지만

타입스크립트에서의 객체는 키:타입 이 한페어이고

구문이 자스는 ',' 로 나뉘고 타스는 세미콜론으로 끝

중첩된 객체의 타입은 어떻게 주는가?
{
id: string;
price: number;
tags: string[];
details: {
title: string;
description: string;
}
}

요롷게 ㅇ 특별할건없다

### 튜플타입

파이썬의 그거 아닌가 배열 아무튼

튜플은 길이가 고정된 배열 타입도 고정됨

예를들어 role 이란 배열에 [39, ‘작가’] 라는게 있다면

첫번쨰가 나이고 두번쨰가 직업이 고정이라면

그리고 길이도 고정되어야된다면 당연히 push 되어서도안되고

role[1] =10 같이 타입이 변경되어서도안될것이다

이런경우에는 튜플이 적절하다

이걸 어떻게 정의하느냐 ?

```ts
const person: {
  name: string;
  role: [number, string]; //이렇게  이게 튜플
} = {
  name: "kim",
  role: [29, "프론트엔드"],
};
```

염두해야될것은 이닛할떄는 3번째 아이템을 맘대로 추가할수없지만

push method 는 안막아져서 push 하면 push 는된다.

### 열거형(enum)

Enum 도 자스에는 없는형태

자바스크립트에선

전역상수를 선언하고 갖다붙여서 if 조건문으로 쓰는게 일반적인 흐름

이것의 단점은

모든 상수를 정의하고 관리해야된다는 것

enum은 enum키워드로 정의한다

enum 은 커스텀타입임

```ts
enum Role {
  ADMIN,
  READ_ONLY,
  AUTHOD,
}

{
  role: Role.ADMIN;
}

컴파일된 자바스크립트 를 보면


Role[Role["ADMIN"]=0]="ADMIN"

//"READ_ONLY"=1
//"AUTHOR"=2

형태로 관리

enum Role{ADMIN=5,READ_ONLY,AUTHOD};

이런식으로 이닛밸류 넣어줄수도있음 문자열도가능


```

이넘의 강점 : 백그라운드에 매핑된 값이 있는 식별자가 필요할때 훌룡한 구성

### 유니언타입

유니언 타입

서로 다른 두 종류의 값을 사용해야 하는 애플리케이션에서

함수나 상수 혹은 변수의 매개변수를 사용해야된다면 유니언 타입을 사용하여 타입스크립트에게

숫자나 문자열 중 하나를 사용해도된다는 걸 알릴수있다.

```ts
function add(n1: number, n2: number) {
  const result = n1 + n2;
  return result;
}


function add(n1: number|string, n2: number|string) {//이런식으로해결
  const result = n1 + n2;//하면 여기서 에러가 남
  return result;
}


typeof 로 해결


function add(n1: number|string, n2: number|string) {
let result
if(typeof n1==="number" && typeof n2==="number")result = n1+n2
else result = n1.toString() + n2.toString()

return result

}

```

### 리터럴 타입

```ts

정확한 값을 가지는  타입

const number1 =2 ;

위에 마우스 올리면 number1:number 로 추론하는 것이 아닌

number1:2

이런식으로 명시적으로 뜬다.

이걸 유니온 으로 구현했던 add 함수 에 활용


function add(n1: number | string, n2: number | string, resultConversion: string) {
  if (resultConversion === "isString") return n1.toString() + n2.toString();
  if ((typeof n1 === "number" && typeof n2 === "number") || resultConversion === "isNumber") return +n1 + +n2;
}



function add(n1: number | string, n2: number | string, resultConversion: "isString" | "isNumber") {
이런식으로 혼재도 가능
```

### 타입 alias

```ts
type Combinable = number | string; //별칭으로 하고자하는 타입을 지정
type ResultConversion = "isNumber" | "isString";

function add(n1: Combinable | string, n2: Combinable | string, resultConversion: ResultConversion) {
  if (resultConversion === "isString") return n1.toString() + n2.toString();
  if ((typeof n1 === "number" && typeof n2 === "number") || resultConversion === "isNumber") return +n1 + +n2;
}
```
