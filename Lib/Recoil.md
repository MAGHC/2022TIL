### recoil

써봤는데 적어도 redux 나 vuex 보단 되게 간편하다.

구현은 아무래도 recoil 이 state 적으로 투두 리스트 구현하는데에 이런식의 flux 패턴을 써먹을 데라고는 auth provider 정도 밖에 없음으로

당연하게도 그것의 구현에 사용하였다.

보통 useRecoilValue() 하면 밸류만 사용이 가능하고
useRecoilState()하면 스테이트 변경이 가능하다 마치 useState 와 비슷하게 생겼다.

다만 selector를 안써봤다. 일단 내가 구현 하는 범위에서 아직까지는? 필요성을 못 느꼈다

사실 reactQuery 랑 같이 쓰면 좋은 조합이라그래서 reactQuery를 본격적으로 적용하면 아마 selector 를 쓸 일이 생길거같다.

const setState = useRecoilState(state)

setState({key:value}) / setState((pre)=>{...pre , key:value})

### persist 문제

context APi를 통해 authProvider를 구현해봤기에 구현은 그렇게 까지 어렵지 않았다 다만,

로그인 을 성공하면 atom의 value를 true로 변경시키는 방식이여서 이 true 가 유지가 되어야되는데 새로고침하니까 reset 되버리는 문제가생겼다.

스택 오버 플로우에 나랑 같은 문제를 가진 사람을 찾았는데

https://stackoverflow.com/questions/63357128/recoil-not-persisting-state-when-refreshing-page

그것이 정상적인 반응이라나 ? 개인적으로는 이해가 안됬지만 하여간 그런가보다 하고

'recoil-persist' 라는 라이브러리 를 통해 해결했다.
