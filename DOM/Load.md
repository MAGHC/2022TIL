### load

window.addEventListenr('load', ()=>{
console.log('hi')
})

다른것보다 아마 라이프 사이클 훅과 관련이 많은 내용일것이다.

js용 useEffect 같은 느낌이지만 사실 반대겠지?

load 말고

DOMContentLoaded 라는 것 도 있는데

차이점은 html요소 다 끝나면 저게 나옴

unload 와 beforeunloaded 도 있는데
페이지를 나갈때 내리기 전에 뭔가를 해야된다면 사용.

beforeunloaded 는 resource
