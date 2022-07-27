### router , 동적라우팅

use params()

주소창에 :id
부분을 가져옴 라우터에서 설정한.

카드리스트>카드 > 디테일 페이지> 디테일 페이지의 카드

가있다면

카드리스트에서 나오는 카드를 눌렀을때 디테일 페이지로 이동
use navigate 를 통해 url 설정

여기까지 했다면 주소창은 변경되나 디테일 페이지 카드 아이템이 변경이안됨

디테일 페이지 useEffect 로 데이터 패치 useparams 사용하여 주소값 가져옴

의존성 배열에 params 값을 넣어줘야 다음 이전 버튼 눌렀을때 데이터 패치.

데이터 패치되기전에 초기 카드 컴포넌트의 이미지나 데이터 가 나오는데 이부분을 방지하고 싶다면 조건부 렌더링.

참고로 navigate(-1) 하면 간편하게 뒤로가기 구현

밖에서 정렬 기능 같은게 있다면 id 가 뒤섞이나 ?

### next back button

별거 없음 id값 parseint 가 유의할점 나머지는 그냥 생각대로 하면됨

### 페이지 네이션

구현 플로우는 동적 라우팅 이랑 비슷함

버튼 의 핸들 함수 부터 디자인 onclick

해당 버튼의 인덱스 부모 props 에서 업데이트.

offset - > 시작 지점

limit -> 보여줄 갯수

해서 쿼리문 작성

`?limit=20&offset=0`

알다시피 쿼리문은 ? 로 시작하고 &가 다음 옵션 같이사용할것 적어줌

location = useLocation 을 사용하여 해당 주소의 search 값을 가지고옴.

click 시 해당 useEffect에 데이터 패칭 .

의존성 배열에 location.search 를 넣어주면 동적라우팅 마냥 매번 변경됨.

다만 여기까지만 구현하면

맨처음 화면이 컨텐츠가 100개라면 100개가 다나오는 상태일것임

그래서 || 연산문 을 사용하는데.

알다시피 둘중하나가 true면 그것을 사용함.

아마 구현해놨으면 location.search 가 되어있을텐데 처음에는 비어있음으로 falsy 값일것임
`?limit=20&offset=$0` 값을 함께 추가 해주기

```js
useEffect(() => {
  fetch(`http://localhost:8000/users${location.search || `?limit=20&offset=$0`}`)
    .then((res) => res.json())
    .then((res) => setUsers(res.users));
}, [location.search]);

const updateOffset = (a) => {
  const limit = 20;
  const offset = a * limit;
  const queryString = `?limit=${limit}&offset=${offset}`;
  navigate(`${queryString}`);
};
```
