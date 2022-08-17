## 구조분해할당

### 배열의 구조 분해 할당

```js
const arr = [2, 3, 4];

const [x, y, z] = arr;



Const obj = {

'array':[2,4,5,]
}


const [a,b] = obj.array


console.log(a,b) // 2,4



const [a,,b] = obj.array

,, 로 넘길 수 있다.

Console.log(a,b) // 2, 5


a,b의 순서를 바꾸고 싶다면

[a,b]=[b,a] 로 바꾸면 된다. 중간에 변수에다가 할당안하고 그냥 저렇게 바꿀 수 있다.


오브젝트 안에 메서드를 넣고 구조분해 할당도 가능하다


const obj{
    go:[2,3,4],
    gogo[4,5,6],
    Pick=fucntion(a,x){
    return this.go[a] this.gogo[x]

}}

const [a,b] =Obj.pcik(2,1)



네스팅 구조 분해 할당

const nested = [2,5,[5,6]]

const[i,,j] = nested // 2,[5,6]


디폴트 벨류 설정 가능


const [a ,b,c] = [1,2]

c => undefined

[a,b,c=1] = [1,2]

Console.log(a,b,c) => 1,2,1

이걸 언제써먹냐? 외부 api 쓸 때 써먹기 좋은 방법이라고 함 동적인 데이터 다룰때




```

### 객체의 구조 분해 할당

```js

오브젝트 구조분해 할당은 {} 를 사용한다.


배열에서 다룰 때 처럼 스킵이 필요하지않음

이름을 설정할 수 도 있다.

const{name:restauranName, openinghours:hours, categories:tags,}=restaurant


console.log(restauranName, hours, tags ) // 같은 결과


이것도 기본 값 설정 가능

Let a = 111

Let b = 999

Obj = {a:73, b:24 ,c:2}
변수 a,b를 오브젝트의 a,b로 바꾸고 싶다면?

배열에서 처럼

{}=obj 하면 될것 같지만

{} 만있으면 코드블럭으로 인식하기때문에

{{a,b}=obj} 로 한번 더 감싸주어서 사용하게 된다.


함수 의 매개변수 부분을 구조분해 할당으로 사용할 수 있다.

const obj = {
 data : [2,4,5,3],
 example : function({startIndex=1,time = "2:00"
//  구조분해할당 + 기본값 설정
 }){

 }


}


```
