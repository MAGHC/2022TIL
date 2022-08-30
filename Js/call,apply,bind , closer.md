### call

```js
const lufthansa = {
  airline: "Lufthansa",
  iataCode: "LH",
  bookings: [],
  book(flightNum, name) {
    console.log(`${name} booked a seat on ${this.airline} flight ${this.iataCode}${flightNum}`);
    this.bookings.push({ flight: `${this.iataCode}${flightNum}`, name });
  },
};
const eurowings = {
  airline: "Eurowings",
  iataCode: "EW",
  bookings: [],
};

const book = lufthansa.book; // 이런식으로 method 할당가능

하지만

book(23, 'Sarah Williams'); 은 먹지 않는다

왜냐? this 키워드가 있기 때문

여기서 call method 를 사용하면

book.call(eurowings, 23, 'Sarah Williams');
console.log(eurowings);

첫번쨰 인자로 호출하려는 함수의 this 키워드를 설정할 수 있다.





```

### apply

call 과 비슷하다

차이점은 두번쨰 인수로 전달할 것을 배열로 전달해야된다.

```js
const data = [23, "kimjungsoo"];

book.apply(eurowings, data);


근데 결국 이방법은

book.apply(eurowings, ...data)

와 같은 것이므로 스프레드 문법을 활용하면 된다.



```

### bind

bind method 는 조금 성격이 다른데 위의 call, apply 가 바로 함수의 결과를 반환했다면

blind 는 새로운 함수를 만든다.

```js

const newbook = book.bind(eurowings)

newbook 은 eurowings를 bind 한 새로운 함수다.


newbook(23,'kim') 하면된다.

유용한것은 전에 배웠듯이 인수 의 기본값을 설정할 수 도있다.

const newbook = book.bind(eurowings , 23)

이렇게 하면

newbook('kim') 이렇게 쓸 수 있다.


또 다른 예시는 eventListener 에서의 예시

document
  .querySelector('.buy')
  .addEventListener('click', lufthansa.buyPlane));

하면 buyPlane 이라는것의 this 가 가리키는 것은 buy 라는 클래스네임을 가진 버튼이 됨

해결방법은

이벤트 리스터 써먹기전에

lufthansa.buyPlane() 한번실행해주면 함수에 this 가 바인딩됨

아무튼 핵심은 this를 설정해줘야된다는것


call을 써도되지만 인수전달할것도없으므로 bind ㄱ



 .addEventListener('click', lufthansa.buyPlane.bind(lufthansa)));



this 키워드가 없을때도 활용가능하다

세금 계싼서를 만든다고 하자


const calTax =(val,rate)=>val+val*rate;


//다른 나라의 세율을 적용하고싶다고한다면?

const koreaTax = calTax.bind()
근데 val 의 기본값을 뭐라고 하면 되는것인가? 하면 여기에서 null 로 두는게표준이라고 한다

const koreaTax = calTax.bind(null,0.1)

이런식으로 두고

koreaTax(2000) 같이 쓰 면 되는것.




```

### bind 의 예시를 클로저로 구현해보자

```js
마지막으로 만들었던 const koreaTax

를 클로저로 구현해보자


const closerTax = function(rate){
  return functoin(val){
    return val+val*rate
  }
}

const setRate = closerTax(0.1)

setRate(2000)

아니 하라니까 이렇게 하고 이렇게 되는건 늘 알겠지만 솔직히 뭔 원리인지는 정확히는 모르겠다 그냥 이자체가 이런 원리라고 이해 할 뿐


```
