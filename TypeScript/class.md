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
