### set

유니크한 밸류를 가진 컬렉션.

중복되지 않은 컬렉션으로
바꿀때 사용하기 좋다.

console.log(new Set('kim')) // {'k','i','m'}

new 키워드로 사용

size = length

has() 인자로 넘겨준 값을 가지고 있는 지 ⇒ true /false 반환

add() 추가 / 두번해도 하나만 들어감

delete() 삭제

배열에는 delete가 없다 아 splice 나 slice 쓰지

set은 인덱스가 없기때문에 인덱스로 전달할 수 없다.

모든 값이 유니크 하다면 굳이 인덱스로 가져올 필요가없기 때문

cleaer() 전부 삭제

배열로 전환 :

const uniqueArray = [...new Set(array)]

### map

객체랑 비슷하게 생긴 iterable

키로 온갖걸 사용할 수 있다 boolean , [] 등등

.set 으로 키밸류를 세팅할수있다

const rest = new Map()

rest.set('name','kim')
rest.set(1,'jung')
console.log(rest.set(2, 'soo')) //{'name'=>'kim', 1=>'jung',2=>'soo'}

rest.set().set().set().set() 도 가능하다 네스팅이 되는건가 했더니 그냥 여러번 set 하는거였다

배열을 키로 하고싶다면

const arr = [1,2]

rest.set(arr, 'true')
로해야된다. 그렇게 하지않으면

같은 배열이더라도 주소값이 다르기 때문에 다른걸로 인지. 해서 get이안됨

rest.set(document.querySelector('h1'), 'heading1') 하면 돔을 키로 추가 할 수 있음

```js
다른 방법으로 key ,value 넣는 방법

const question = new Map([

['question', 'most popular language?']
[1,"c"],
[2,"java"],
[3,"js"],
[true,"good"],
[false,"bad"]
])

하면 각각의 배열마다 [0]이 key [1]이 value 로 들어간다.

이 구조를 어디서 보았는가?

Object.entries(obj)





const question2 = new Map (Object.entries(obj))


이걸로 집어 쳐넣으면 쉽게 map 만들기 가능




for....of 문 사용 가능


for(const[key,value] of question) // 구조 분해 할당 활용 {
if(typeOf key ==='number') console.log('hi')
} 같은 방식으로 활용 가능


array로 변환시

그냥 [...question] 은 사실 별 의미가없음


[...question.keys()]
[...question.values()]

로 하는게 의미가있을것임
```

### 어떨때 어떤 데이터를 사용해야하는가?

1. 간단한 값 목록만 필요한지?

⇒ array , set

array vs set

set을 사용하는경우

1. 높은 퍼포먼스가 필요할때 = > 어레이에서 지우는것과 set에서 지우는것은 퍼포먼스 차이가 10배이상이다.

2. 중복제거

나머지 array

배열 조작할때

1. 키 밸류가 필요한지 ? (= 값을 설명할 필요가 있는지? )

⇒ 오브젝트, map

오브젝트vs map

오브젝트에는 기술적 단점이 있다. 키 가 한정 되어있다는 것

다만 이미 오브젝트는 키접근이 편하고 압도적으로 사람들이 많이쓴다.

다만 돔을 넣거나하는 파워풀한 사용이 가능하고 , 간단한 키벨류를갖는것은 map을 쓰는것이좋다.

map은

iterator고
