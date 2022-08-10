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
