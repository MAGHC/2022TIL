### xmlhttprequest

이걸로 api 통신을 해봤다.

구식이지만 항상 공부가 그런것같다 이런 불편함을 거쳐서 이렇게 발전되었다 정도는 알아야 되는듯 유데미도 그렇고 예에전 부트캠프에서도 강조했던 덕목? 이기도 하고

하여간 지금은 본지 얼마안되서 알지만 이걸 나중에도 기억할것 같지는 않은데 아무튼 이렇게 해봤다

```js
 const request = new XMLHttpRequest(); // 이렇게 requres 를 만들어준다

request.open('GET', `https://restcountries.com/v3.1/name/${country}`);//로 요청을 열고

  request.send(); // 보낸다

  request.addEventListener('load', function () {//리퀘스트 에 대한 이벤트 핸들러를 만든다.
    const [data] = JSON.parse(this.responseText); // 이렇게 구조분해할당하는 건 또 처음 보는거 같음
    console.log(data);

참고로 위의 get api 주소는 public api 라 괜찮다.


이모든걸 새로운 이벤트로 감싸서 버튼을 누를때마다 html 이 추가되게 끔 만들었는데

여기서 비동기의 단점을 단적으로 볼 수 있었다.

여러번 버튼을 누르면 해당 국가의 정보들을 html로 dom에 추가하게되어있는데

어느떄에는 한국 미국 일본

어느때에는 미국 일본 한국

이런식으로 뭐가 먼저 도착할지 뭐가 먼저 나올지 알 수 가 없었다. 그냥 알고는 있었는데 이렇게 쳐보고 뵈니까 신기했다





```
