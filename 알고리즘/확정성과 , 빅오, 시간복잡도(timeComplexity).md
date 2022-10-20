### 확장성

좋은코드란? => 가독성이 좋고 확장성이 좋은 코드

어떻게 측정하는가 ?

```js
const array = [2, 4, 5, 6, 3];

const a = (array) => {
  let t0 = performance.now();
  for (i of array) {
    if (i === 2) {
      console.log("hi");
    }
  }
  let t1 = performance.now(); //performance.now() 는 내장

  console.log("2를 찾는데 걸리는 시간은" + (t1 - t0) + "밀리초");
};

console.log(a(array));
```

하지만 이방법은 컴퓨터마다 환경마다, 다르게 찍힌다.

그러면 어떻게 효율성을 측정할수있는가

빅오 표기법은 알고리즘을 실행하는데 걸리는 시간을 말할때 사용하는 용어.

컴퓨터차이에 상관없이 측정가능하다.

### 시간복잡도

시간복잡도를 고려한다? =>입력값의 변화에 따라 연산을 실행할 때, 연산 횟수에 비해 시간이 얼마만큼 걸리는가? 를 고려한다.

효율적인 알고리즘을 구현한다는 것은 바꾸어 말해 입력값이 커짐에 따라 증가하는 시간의 비율을 최소화한 알고리즘을 구성했다는 이야기

### 빅오

```js
const array2 = [2]

const array10 [1,2,3,4,5,6,7,8,9,10]

const everyArray = new Array(100000).fill('2')

const array = [2,4,5,6,3]


const a = (array)=>{

  for(i of array){

  if(i===2){
    console.log('hi')
  }
}


  }

console.log(a(array))

위의 코드는 선형에 해당하며

입력수가 증가하고 그에따라 작업수도 증가한다.

이게 빅오 혹은 리니어 타임이라고 부른다


O(n)에는 무엇이든 들어갈수있다.

O(x) O(fish)  n은 그냥 표준

이것이 위의예제에서 array2 라면 O(1)  이고 array10 이라면 O(10) everyArray 라면 O(100000)

```

### O(1)

```js
ex) function log(boxes){

console.log(box[0])}
```

아무리 요소가 많아도 작업수는 그대로 유지된다

요소를 아무리 많이넣어도 첫번째꺼만 빼니까.

뭘 넣든 똑같음 확장성 측면에서 단선임 위에건 선형

입력이 얼마나 크든 별 상관이없다.

확장성 측면에서 아주 좋다.

동일한 예측은 매우 훌룡한것.

### 빅오 예제

```js
function challenge() {
  let a = 10; // o(1)
  a = 50 + 3; // o(1)

  for (let i = 0; i < input.length; i++) {
    // o(n)

    anotherFunction(); //o(n)
    let starnger = true; //o(n)
    a++; //o(n)
  }
  return a; //o(1)
}
```

⇒ 3+4n

BIG O(3+4n)

사실 이건 그냥 O(n)
