### prototype

```js

const Person = fuction(firstName, birthYear){

}

new Person ('kim', 1995);

//1. 새로운 빈 객체 생성
//2. person의 function call , this 바인딩
//3. 프로토타입에 연결
//4. function 이 자동적으로 {} return

 const Person = fuction(firstName, birthYear){

}

const Person = fuction(firstName, birthYear){
this.fristName = firstName;
this.birthYear = birthYear;

}

const kim = new Person('kim',1995)

console.log(kim) // firstName:"kim",birthYear:1995


console.log(kim instanceOf Person)//true



const Person = fuction(firstName, birthYear){
// 인스턴스 속성

this.fristName = firstName;
this.birthYear = birthYear;

//절대로 생성자 함수 내부에서 함수를만들면 안됨 => 이유?
//모든 객체에서 이 기능을 수행할것 그럼일일이 다 만들어줘야됨
//해결? => 프로토타입 상속

this.calcAge = function(){
console.log(2022-this.birthYear)}


}


	모든 자바스크립트에 프로토타입이라는 속성이있다.

이건 person 생성자도 마찬가지다.

Person.prototype.calcAge = function(){
console.log(2022-this.birthYear)}


console.log(Person.prototype)// calcAge :f()

이제 이 생성자 함수에 의해  이 프로토타입의 모든  메서드에 엑세스 가능함

kim.calcAge() // 27

console.log(kim.__proto__)
// calcAge:f, constructor : f

console.log(kimt.__proto === Person.prototype)//true

kim.__proto__는 Person 생성자의 프로토타입 속성이다.

=>
cosnole.log(Person.prototype.isPrototypeOf(kim))// true
cosnole.log(Person.prototype.isPrototypeOf(Person))// false

// 프로토타입은연결된 객체의 프로토타입 .


메서드 말고도 가능

Person.prototype.species= '호모사피엔스'

console.log(kim.species)//호모사피엔스

```

### 2

이전것에 이어서.

const Person = {
}

Person.prototype.calcAge = function(){
console.log(2022-this.birthYear)}

kim.**proto** // calcAge :f  
kim.**proto**.**proto** // hasOwnProperty 같은것들
kim.**proto**.**proto**.**proto** // null

const arr = [213,412,214,214,241] //new Array ==== []
arr.**proto** // fill, concat , find ,등등 method 들

모든 배열은 이 메서드들을 프로토 타입에서 상속한다.

arr.\_\_proto === Array.prototype // true

Array.prototye.unique = function(){
return [...new Set(this)]}

arr.unique()

우옹

혼자하는 프로젝트면 모르겠지만 이런 습관을 들이지는 말것..

다음 버전의 자바스크립트가 같은 메서드를 추가할 수도있음.

버그를 유발할수있음

```js

class Person {
constructor(firstName, birth) {
this.firstName = firstName
this.birth = birth

}

calcAge(){
console.log(2022-this.birth)
}
}

const kim = new Person('kim', 1995)

클래스는 호이스팅 되지않는다.

```

```

```
