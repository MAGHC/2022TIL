### useValidation

로그인 페이지를 만들면서 만든 useValid 를 정리해보려고 한다.

물론 join 페이지에서도 쓸 수 있게끔 확장이 되겠지만 하여간

네이밍이좀 모호한거 같은데 validation 이 라는게 꼭 로그인 회원가입할 때만 들어가는건 아니지않나 싶어 그렇기도 하다만 어찌되었건

마땅히 더 나은 이름이 떠오르는 것도 아니긴했다 auth 도 아닌거같고

useAuth 나 useLogin 은 따로 쓸데가있어가지고 그걸로 짓지도못하겟고 join 하자니 join 에만 쓰는것도아니고 그냥...그렇다고

```ts
const useValidation = () => {
  const [email, setEmail] = useState("");
  const [emailValid, setEmailValid] = useState(false);
  const [password, setPassword] = useState("");
  const [passwordValid, setPasswordValid] = useState(false);

  //유효성 검사는 onChange 에서 이루어진다.

  const onChangeEmail = (e: React.ChangeEvent<HTMLInputElement>) => {
    const value = e.target.value;
    setEmail(value);

    const EMAILREG =
      /(?:[a-z0-9!#$%&'*+/=?^_`{|}~-]+(?:\.[a-z0-9!#$%&'*+/=?^_`{|}~-]+)*|"(?:[\x01-\x08\x0b\x0c\x0e-\x1f\x21\x23-\x5b\x5d-\x7f]|\\[\x01-\x09\x0b\x0c\x0e-\x7f])*")@(?:(?:[a-z0-9](?:[a-z0-9-]*[a-z0-9])?\.)+[a-z0-9](?:[a-z0-9-]*[a-z0-9])?|\[(?:(?:(2(5[0-5]|[0-4][0-9])|1[0-9][0-9]|[1-9]?[0-9]))\.){3}(?:(2(5[0-5]|[0-4][0-9])|1[0-9][0-9]|[1-9]?[0-9])|[a-z0-9-]*[a-z0-9]:(?:[\x01-\x08\x0b\x0c\x0e-\x1f\x21-\x5a\x53-\x7f]|\\[\x01-\x09\x0b\x0c\x0e-\x7f])+)\])/;

    // 예전에 보니까 regexp 도 따로 파일 만들어서 관리하시는 분 있던 데 그렇게 하는것도 한번 고려해봐야겠다.

    const checkEmail = value.match(EMAILREG);

    checkEmail ? setEmailValid(true) : setEmailValid(false);
  };

  const onChangePassword = () = >{
    동일 한 형태
  }

  return{onChangePassword,onChangeEmail}
};
```

사용

import 후

const {onChangePassword,onChangeEmail}=useValidation()

onChange 에 넣어서 사용했다.

물론 다른 valid 나 , email 등의 state 들도 다 return 해서 구조분해 할당후 쓴다 정리를 위해 축약 했을 뿐
