### react 로 userInput 구현 중 event 객체의 type

event 객체의 타입을 말하라길래 {} 로 했더니 안되서

stackOverFlow 에서 찾았다.

React.ChangeEvent<HTMLInputElement> 이걸로 타입 설정하라고

### react useState type 선언

react로 프로젝트를 새로 생성하여 진행하다보니 문제가 생겼다

useState를 뭐라고 타입을 넣어줘야되는거지? 하는 문제

interface 설정하고 generic 해주면 해결된다.

interface Login {
id: string;
pw: string;
}

const Assignment = () => {
const [userLogin, setUserLogin] = useState<Login>({
id: "",
pw: "",
});

이건 나중에 안건 데 useState에다가 굳이 타입을 일일이 안먹여도 알아서 된다...

### map 의 인자 값

여기서 부터는 빨간 줄 뜨는 것들의 타입을 주기 위해서 한 고군분투? 기 인데 사실 이건 별로 어렵지 않았다 그냥 원래대로 type 선언해서 그대로 넣어주면 됬다

```ts
type TypeChannel = { id: string };

 channels.map((channel: TypeChannel) => (
```

### props

props 에도 타입을 줘야된다. 아 자식컴포넌트에서 받을때

{ channelName }: { channelName: string }

원래 적어주듯이 그옆에 타입 넣어주는 방식으로 해결했다.

### error

catch err 하면 err 객체인지 모르고 받질 못하는 경우 가생긴다.

err가 err객체 가 아닐수도있기 떄문에 그렇다

```ts
 if (error instanceof Error) {

```

### event 인자

event 를 인자로 받게되는 경우가있다. addeventlistenr들인데

주로

리액트에서

e:React.ChangeEvent<HTMLInputElement>
와 같은 형태로 알맞은 이벤트 에따라서 설정해주면된다.

### useRef

useRef 뭔가했더니 별 거 없었다 그냥

ref 이름 설정해서

const dom = useref()

<div ref={dom}>

하면 해당 div 를선택하는 거였다.

scrollIntoView() 를 써야되는데 어떻게 돔을 조작하지 하고 찾아보다가 useRef 사용하면 된다고하여 알게되었다.

다만 ts 에서 쓸려면 문제 가 있으니

```ts
const messageComponent = useRef<null | HTMLDivElement>(null);

useEffect(() => {
  if (messageComponent.current === null) {
  } else messageComponent.current.scrollIntoView();
});
```

이런식으로 해결이 가능하다 null 이 아니면 실행하는거지

### 업데이트 함수 props
