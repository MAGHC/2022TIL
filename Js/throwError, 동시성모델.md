### thorow Error

response 객체안에는 ok 속성이있다.

```js
if(!response.ok){
throw new Error(`not found ${response.status}`)

}

.catch (err=>console.err(`${err.message}`)) // throw 한 error

```

### 동시성 모델

자바스크립트는 싱글 스레드지만. 멀티플이 가능하다 => 웹 api 덕분

이미 이내용은 wbapi를 배울때 한번 배운 내용이지만 복습 겸 다시한번 본다.

```js
el = document.querySelecotor('img')
el.src='dog.jpg'
el.addEventListenr('load',()=>{
el.classlist.add('fadeIn')})
fetch(url).then(res=>console.log(res))

이런 코드가있다면

콜 스택에 쿼리셀렉터() 실행
두번쨰줄로 가면서 콜스택 비워지고 이미지 로딩

webapi 에서 비동기 작업으로 이미지를 가져옴
이게 만약 콜스택에서 이루어진다면 기다릴떄까지 아무것도 못하는 끔직한 일이 생길것임
그래서 메인 스레드가 아닌 웹 api 에서 이루어짐
el.addEventListenr('load',()=>{
el.classlist.add('fadeIn')})
이벤트리스너를 추가하면 이벤트리스너()는 콜스택으로가고

()=>{} 콜백 부분은 웹 api로 감

fetch(url).then(res=>console.log(res))

가 일어나면 fetch()는 콜스택으로 가고 끝나면 .then() 이 콜스택으로
그리고 이 then의 콜백 도 webApi로 감


여기까지 콜스택이 전부끝나고 비동기로 이미지와 res 가 실행되고있을것임

그럼 이 이미지 콜백이  콜백 큐 로 이동

콜백큐는 순서가 지정되어있음

스택이 비어있으면 콜백 큐에 있는것을 가져옴

	el.src 에 대한 것과 클래스리스트 add() 두가지가 추가가되는데


이를 이벤트 루프 틱 이라 한다고 함


이제 fetch 가 webapi 에 남아있는데 promse 만의  특별한 대기열이있음

바로 마이크로 테스크 큐

근데 뭐 또보고 또보고 해야지 다시보니까 아직 까지는 또 완전새롭진 않은데 여전히 다 기억나지만도 않네

```
