### data attribute

이거를... 분명 모던에서도 봤고 다른곳에서도 본거 같은데 til 에 따로 정리는 안한것같아서 최근에 또 본김에 다시정리한다.

하긴 내가 모던을 깃헙에다가 정리하진 않아서 없는게 당연하다면 당연할지도 아무튼

원하는 값을 추가할수있다 html 태그에

원래는 id 나 클래스를 주지만

data-셋팅네임

data-index =”1”

같은 형식으로 사용 가능

```js

<div data-index="1"></div>


css 에서 읽는 법

div[data-index="1"]{
font-size:4rem;}



js 에서 읽는법

const div = document.querySelector('div')


const div = document.querySelector('div[data-index="1"]')도 가능
다만 이렇게쓸때 유의 사항은 ''는 중복해서 쓸수없으므로 밖에 '' 를썼으면 안에는 ""

console.log(div.dataset) // index:"1"  key/value 형태로 들어가있음


여러개도 정의가능

<div data-index="1" data-name-user="kim"></div>
console.log(div.dataset)// index:"1" nameUser:"kim"  name-user 에서 - 가 제거되고 카멜로 바뀜


console.log(div.dataset.index)
console.log(div.dataset.nameUser) 로 받아올수있음


주의 해야될 점

만약 사용자 에게 민감한 데이터는 html 태그에다가 추가해서 보관하면 안됨

해커한테 잘 보임



```
