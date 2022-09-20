### 객체타입

참조에 의한 변화

똑같이 생긴거처럼 보이는 객체더라도 === false 다른 메모리를 참조함으로

변화 가 가능하다.

- 향상된 객체 리터럴

다른건 아니고

Const hours = [11,12,3,5,6]

Const obj = {hours:hours
}

할필요없이

Obj = {hours}

하면 알아서 됨

### 클래스

틀 , 템플릿

클래스 자체에는 데이터 가 들어가지 않음/ 정의 해놓는 것

한번만 선언함

### 오브젝트

클래스안에 실제로 데이터를 넣어 만드는 것

굉장히 많이 만들기 가능

클래스는 메모리에 올라가지 않지만 오브젝트 는 들어간다

class 선언

class person{

    constructor (name , age){
        this.age= age;
        speak(){
            console.log(this.name)
        }
    }

}

const kim = new person('kim',20)

kim.speak() // 20

### getter , setter

게터 세터는 기본적으로 함수고

이름 명 대로 데이터를 가져오고 세팅한다

```js
const acount = {
owner = 'jonas'
movement=[200,300,400,500],
get latest(){
return this.movement.slice(-1).pop();
}

set latest(mov){
this.movement.push(mov)}
}

console.log(account.latest)//500
account.latest = 50 ;
console.log(account.movement)// 50 추가

class Person{

constructor(fullname , birthyear){
	this.fullname= fullname;
	this.birthyear = birthyear
}


set fullname(name){
if(name.includes('') this.fullname = fullname)
}

}

fullname 이 이미 있는데 set fullname 이 있다 이럴경우에 일어나는일은

this.fullname이 설정될때마다setter 가 실행될것

set fullname 으로 전달하는 name 은 this.fullname


다만 이렇게 하면 콜스택 오류가 뜸

fullname 이랑  setter 의 fullname 이 겹치기 때문

그래서 컨벤션이잇다

set fullname(name){
if(name.includes('') this._fullname = fullname)
}

이렇게 '_' 를 추가


여기까지만 하면

new Person('kim' , 1995)

console.log(kim.fullname) 하면 안됨 _fullname 이를 해결하기 위해서 getter 사용


get fullname (){
return this._fullname}

여기까지 해놔야 kim.fullname 가능

이미 존재하는 속성을 설정 할 때 이 플로우를 이해하는것 이중요하다

근데 뭐 가끔 유효성 검사할때 써먹을만하는데 잘 쓰지는 않는다

```

### public / private

샵을 붙이면 프라이빗 필드(#)

아니면 퍼블릭 필드

약간 전역변수 지역변수느낌

프라이빗은 내부에서 변경 가능

퍼블릭은 밖에서도 가능

### static 정적 메서드

들어오는 데이터에 상관없이 공통적으로 클래스에서 사용하는 것이라면

스태틱과 스태틱 메서드를 사용하는것이 메모리를 적게 사용하는 방법

타입스크립트에서도 쓴다는데 아직 개념 이해 부족

```js

Array.from() 이 좋은 예시다.

배열로 변환하는 메서드

Array.from() 은 프로토타입이 아니다

그래서 [2,5,6].from () 은 먹지 않는다

상속되지 않기 때문에

이걸 정적 메서드라고 한다.


Person.hey = function(){
console.log(`hey!`)}
이건 상속되지앟음

프로토타입이 아니니까

저렇게 만드는것외에도 static 키워드를 이용해서 만들수있다.

class Person{

constructor(fullname , birthyear){
	this.fullname= fullname;
	this.birthyear = birthyear
}


set fullname(name){
if(name.includes('') this.fullname = fullname)
}

static hey(){
console.log('hi')
}

}

참고로 class 에서 만든 메서드들은 프로토타입에 추가된다 static 을 적지않으면

클래스에 대한 도우미 함수로써 구현하는데에 도움이됨 아니면 생성자함수 ㅇ

```

### 상속 다양성

extends 라는 키워드 사용하여 상속가능

class rectangle extends shape{}

이런식으로 활용

원래 shape 에 선언되어있던 것들도 변경 가능함 // 오버라이딩 이라고함

다만 이렇게 했을시 기존게 지워지는데

기존걸 사용하고 싶다면

super 키워드 사용

### object.create()

```js
const PersonProto ={

calcAge(){
console.log(2022-this.birthYear)
}

}

const lee = Object.create(PersonProto)
이러면 personproto 랑 연결됨

console.log(lee){}calcAge:f calcAge()

lee.birthYear = 1994

lee.cacAge() //정상 작동

lee.__proto__ === PersonProto // true
```

object.create 는 사실 클래스를 만드는 방법중에는 가장 안쓰는 방법이지만

class 끼리 프로토타입을 연결하는데에 아주 중요하다고 한다.
