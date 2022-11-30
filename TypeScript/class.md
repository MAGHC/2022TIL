## Type Script class

### this

```ts
class Person {
  name: string;

  constructor(n: string) {
    this.name = n;
  }
  sayHi() {
    console.log(`hello ${this.name}`);
  }
}

const person = new Person('kim'); // 정상작동

const copy = { sayHi: person.sayHi }; // 이름 똑같아야됨 sayHi , error this 바인딩이슈

sayHi(this:Person) // person 클래스의 인스턴스를 쓰겠다는 것을 명시 그럼 여기서 카피가 되게끔하려면?

const copy= {name:"newz", sayHi:person.sayHi}

copy.sayHi()// hello newz 정상작동




```

### public , readonly

ts에선 private 으로 접근을 막을수있다

js 에선 최근엔 # 키워드로 막음

public은 기본값이기때문에 굳이 네임앞에 public 을 붙일필요는 없다.

원래는 필드에서 만들어놓고 construcotr 에서 초기화 시키는 방법을 사용하지만

```ts

constructor(private id:string , public name:string) 와 같이 약식 초기화 가능

```

readonly 의 경우 js 에는 없고 ts에만 있는 속성인데

이 속성을 넣으면 초기화 중 한번만 사용이 가능하다.

```ts

constructor(private readonly id:string)// 과 같은 형태로 사용
```

### super

상속을 받으면 상속받는 클래스의 constructor 도 자동으로 설정이된다.

물론 고유의 constructor도 추가할수있는데 이때 super 를 추가 하고 실행해야된다.

super로 이전 constructor 하드코딩가능

```ts
class App {
  construcotr(private readonly id: number, public name: string);
}

class App2 extends App {
  constructor(public birth: string) {
    super(1, 'kim');
  }
}

//요런느낌
```
