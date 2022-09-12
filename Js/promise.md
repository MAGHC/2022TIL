### promise

비동기를 간편하게 처리 할 수 있게 해주는 오브젝트 => promise

const promise = new Promise(resolve, reject)=>{

}

resolve 는 정상일때

reject는 에러시.

.catch를 해야 reject 에러 설정한게 정상적으로 뜸

.then .then (213=>ads(213)) 이렇게 같을경우 출일수있음
.then(ads) 이렇게

.catch는 then 의 맨 마지막에 두면 알아서 에러 핸들링 가능 하며

해당 에러에 대한 빵구를 메꾸고 싶다면 그 해당 then 바로 뒤에 catch 로 빵구를 매우면됨

프로미스는 네트워크와 통신 파일들을 불러오는 무거운 작업들을 하기때문에

사용자가 눌러야 네트워크 통신을 해야 하는 것이라면 해당 사항을 유의 해서 만들어야된다.

### .all

promise.all([함수(),함수()])
로

병렬 실행가능

### .race()

all 과 사용방법은 똑같음

다만 둘중 하나를 레이스 시킨다는 의미인듯

먼저 들어오는거 먼저출력.

### pending

const request = fetch(url)

console.log(request)// promise{<pending>}

pending = 보류중 (백그라운드에서 여전히 실행중)
settled = 끝남 , fulfilled (성공) , reject(실패)

콜백 지옥은 삼각형 형태로 점점 depth 가 들어가지만

promise 는 평면 체인

### 에러 핸들링 / finally

에러핸들링

1.

fetch(url).then(res=>res.json(),err=>alert(err))

2. 마지막에 catch

then().then().then().catch(err=>alert(err))

finally

무슨일이 있던지 간에 항상 호출. 그닥 항상 유용하진 않음

finally 를 사용하는 좋은 예시는 로딩 스피너를 숨길때

로딩스피너는 에러가 나든 성공을 했든 아무튼 result 를 받으면 사라지기 때문

### promise.allSettled

es2020 에서 생긴것
promise가 reject 되던 말던 결과를 배열로 리턴함

```js
Promise.allSetteld([
Promise.resolve('success')
Promise.reject('ERror')
Promise.resolve('another Success')
]).then(res=>console.log(res))

//[{...},{...},{...}]


```

### promise.any

promise.any

es2021

race랑 비슷함 먼저 완료된거 반환

차이점은 reject를 무시함

항상 resolve 만 반환 뭐 어찌되었건 중요한건 all 과 race 정도
