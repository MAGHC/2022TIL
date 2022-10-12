# 몇개 중복 되는 거 있을 수 있음 인지하고이는건 알아서 넘길 것 임 sort 같은거

## join

[] 벗기기

array.join()

인자로 구분자 전달시

array.join('|')

각각에 인덱스 였던 거 마다 | 가 들어감

하나 의 스트링 으로 묶임

## split

짤라서 새로운 배열을 만듦

array.split(기준으로 할 것 보통 ',' / 두번째 인자는 리밋트라고 하여 받을갯수 설정 가능)

## reverse()

기업협업 당시에 잘 써먹었던 기억이 남
배열 반대로 돌리기

채팅 날짜 순서 아래에서 위로 위에서 아래로 반대로 바꿀 때 잘 써먹음

특징은 원래 선언되어있던 배열도 뒤집음

## splice

이것 또한 배열 자체를 건드림

새로운 배열을 만들어야 되면 splice 를 사용하지 말것

바로 인자설명
(시작할인덱스 , 자를 갯수 , 추가하고싶은내용?)

?옵셔널 뭐시기로 내용정리할때 나도 써먹어 보려고함

## slice

새로운 배열을 리턴함

slice (0,4) 하면 3 까지

(0, array.length) 하면 보통 끝까지 알아서 가능

## find

이제 이런 method 들의 첫번째 인자가 뭘 의미하는 지 잘암

value 이기때문에

두번쨰는 index

앞으로 밑에서는 생략 하겠음

맞는 거 찾으면 그거 리턴함

아마 findindex 라고 index 찾는거랑 id 찾는거랑 그런 것들도 있을거임 예전에 쓴기억남 아무튼 지금은 생략

## filter

필터또한 뭐 마찬가지 해당되는거 리턴함

## map

map 순회하면서 새로운거 만들어냄

## some /every

some => 하나라도 맞는 조건이있는지
every = > 모두다 맞는지

불리언 값 리턴함

## reduce

총합 만들어냄 약간 sort 마냥 동작하는듯

(a,b) 가 있으면 a 에다가 b를 계속 더함

b를 계속 리턴 시킴 a에다가 누적

.reduce((a,b)=>{},0)

const array = [4,5,5,12,412,421,241,214]

console.log(array.reduce((acc,cur)=>{
console.log(acc,cur)
return acc+cur
}))

4 5
9 5
14 12
26 412
438 421
859 241
1100 214
1314

console.log(array.reduce((acc,cur)=>{
console.log(acc,cur)
return acc+cur
},0))

0 4
4 5
9 5
14 12
26 412
438 421
859 241
1100 214
1314

결과는 같네

const initalValue = 0

for(i of array) initalValue += i // 와 같다

const max = array.reduce((acc,cur)=>{
if(acc>mov)
return acc;
else
return mov;
}, array[0]) // 초기값을 0을 넣지말고 array[0] 을넣어라 안그러면 예상한대로 작동하지 않을수도있음

mdn: 누산기는 콜백의 반환값을 누적합니다. 콜백의 이전 반환값 또는, 콜백의 첫 번째 호출이면서 `initialValue`
를 제공한 경우에는 `initialValue`
의 값입니다.

그래서 저렇게 작동하는것.

### map flat

[[]] = > [] = flat

Map 메서드를 통해 생성된 새로운 배열을 평탄화한다.

depth 를 지정해야된다면 flat을 따로 사용해야됨

```js
const arr = [[1, 2, 3], 12, [2, 3, 4]];

arr.flat(); //[1,2,3,12,2,3,4]

const arrDeep = [[[12, 3], 4], 4, , 4, 12]; // flat()=> 한단계만 없앰 flat(2) 해야 동등

//flat map => flat이랑 map 합친거 ;  주의할점은 flat() 처럼 deepth를 설정할수없고 한단계만

Array.from({ legnth: 7 }, () => 1); //이렇게 옵션 쓸수있다. ()=>1 은 fill 과 동일

Array.from({ length: 7 }, (cur, i) => i + 1); // map method 의 것과 동일
```

### from

유사 배열 객체 를 받아 배열로 만듦

set => from 으로 중복 제거 간단히 할 수 있음 for 문 안쓰고도

### 복습 및 추가 사항

```js
let arr = ['a','b','c','d','e','f','g']

arr.slice(2)// 잘라진 new array 배출 ['c','d','e','f','g']
arr.slice(-1) // 'g' 항상 맨마지막.

//slice => 원본 배열을 건드리지않음

arr.splice(2)//잘라진 어레이 배출

//splice = > 원본을 건드림 인자순서대로 삭제시작 // 삭제 갯수 // 추가할 요소


reverse() // 원본 건드림

join('-') // 구분자 넣어서 합침


at() // 2022 새로운 문법  [] 으로 접근 안하고 ()로접근 + 문자열에서도 사용가능

arr[1]= arr.at(1)  //at method 가 브라켓보다 유용한점 ? => arr.[arr.lengt-1] = arr.slice(-1)[0] = arr.at(-1)

아하

forEach() // item // index/ array   entries 로 구조분해할당 구현하던걸 그냥 구현 가능


for(const[i,item] of arr.entries()){
console.log(${i} , ${item})}

arr.forEach((item,i,arr)=>{
console.log(${i},${item})})

```

### forEach 를 Map 과 Set에 썼을때

```js

const mockMap = new Map(["kim","jungsoo"],["kim","soojung"],["lee","lee"])

mockMap.forEach((value,key,map)=>{
console.log(`${key}:${value}`)}) // kim:jungsoo      kim:soojung   lee:lee


const mockSet = new Set(['2','3','5'])

mockSet.forEach((value,key, map)=>{console.log(`${key}:${value}`)})//2:2 3:3 5:5

? set에는 키가 없기때문
```
