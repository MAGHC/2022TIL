### this

자기 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 자기 참조 변수

this를 통해 자신이 속한 객체 또는 자신ㅇ ㅣ생성할 인스턴스의 프로퍼티나 메서드를 참조할 수 있다

단 this 가 가리키는 값, 즉 this 바인딩은 함수호출 방식에 의해 동적으로 결정된다.

### 에로우펑션

에로우 펑션에서의 this 는 상위 스코프를 가리킨다 이를 통해 class 를 만들때 class안의 함수에서 유용하게 사용할 수 있다.

### var

var는 전역에 바인딩 되어서 window 객체에 속해지게 된다 const 나 let 아닌데.

그래서 this 쓸 때에도 var는 쓰지말기

근데 뭐 나는 var 를 써본적이없다 배울때부터 하도 쓰지말래서

---

https://www.youtube.com/watch?v=7RiMu2DQrb4

객체지향에서 this 라는 예약어는 함수가 속해있는 자기자신과 관련이 깊다.

일급객체인 자바스크립트의 함수는

변수나 데이터에 저장 가능하고 함수의 인수로도 전달 가능하며

함수의 반환값으로 도 사용가능하다.

```js
const myFunc = func();

function func1(func2) {}

function func1() {
  return myfunc;
}

obj.func(), obj2.func();
```

자바스크립트에 서 this 라는것이 여간 까다로운것은 같은 함수가 다른 객체에서도 사용되기도하기때문

자바스크립트에서 모든 함수에는 this 랄가지고있다.

함수를 호출하면 대상에따라 this 의 맵핑객체가 변경되는데

이런 동적 this 할당을

this 가 바인딩 된다고한다.

자바스크립트 엔진은 실행가능한 코드를 평가하고 실행문맥을 만든다.

일반적으로 this는 호출되는 객체에 바인딩된다.

### this 바인딩 룰

기본바인딩

암시적 바인딩

new 바인딩

명시적바인딩

브라우저 환경에서 단독실행하면 자연히 윈도우객체에 바인딩됨

use Strict를 사용하면 기본 바인딩이 제외가 된다.

노드에선 전역 코드상에서 하면 빈객체가 나오는데 모듈객체에있는 exports객체와 동일하다고한다.
함수코드의 경우에는 global 객체

암시적 바인딩에서 this를 사용하면서 조심해야될것은

닷 연산이나 브라켓 연산은 참조타입이라는 특별한 것을 반환한다.

```js
const obj = {
  name: 'kim',
  getName() {
    return this.name;
  },
};

function show(callback) {
  console.log(callback);
}

show(obj.getName); //undefined
```

닷이나 브라켓 연산은 참조타입이라는 특별한것을 반환한다.

obj.getName() 은 참조 타입을 통해 암시적바인딩이 되지만

함수로 전달하면 함수의 참조값만 전달 되어 함수 단독실행이된다.

이걸 해결하는 방법이 call, apply, bind 인데

명시적으로 바인딩하는것으로

바인딩시킬 this 의 context가 첫번째인자고 두번째인자를 일일이 전달하냐 배열형태로 전달하냐가 call 과 apply 의 차이점.

bind는 예전에 배웠듯이 apply와 call이 함수의 결과를 내뱉는다면 함수를 새로만든다.

기본인수도 설정가능.

this가 참조하는 개체를 고정시켜주는데 이걸 하드바인딩이라고도 부른다.

new 연산자를 이용한 호출을 하면

생성자함수로써의 역할을 수행할수있게되어 새로운 객체가 생성되고 함수코드가실행되고 생성된 객체를 반환

this 의 우선순위는 new>명시적>암시적>기본

### 화살표함수에서의 this

렉시컬 스코프와 관계없이 화살표함수안의 this는 선언된 당시의 상위를 참조한다.

이게 화살표함수의 장점이기도함