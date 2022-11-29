### Loading 구현

와... 그동안 무적권 && 연산자썼는데 진짜 뭐한거지 뭐 아무튼

```jsx
const [loading, setLoading] = useState(false);
const [err,setErr]=useState(undefined) // 그냥 냅둬도 undefined

하고 useEffect 에서 처리

뭐 시작할때 둘다 set 해서 각각 true / undefiend 할당 해주고

loading의 경우에는 finally 에서 처리해주면 되고 에러는 catch 에서 처리해주면 되는데 그게문제가아니고


내가 놀랐던건

컴포넌트 리턴 문밖에서

if(loading) return<p>로딩중</p>

이게 된다는거였다는거 생각해보면 당연한건데 역시 자바스크립트 실력이 많은걸 뒷받쳐주는구나

```
