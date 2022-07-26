### useInput

유저의 인풋 가져오는 훅

간단한데 은근히 이해하는데 애먹음 특히 구조분해 할당 좀 햇갈림

```js
const Practice = () => {
  const useInput = (init) => {
    const [value, setValue] = useState(init);
    const onChange = (event) => {
      const {
        target: { value },
      } = event;
      setValue(value);
    };
    return { value, onChange };
  };
  const name = useInput("init");
  return (
    <div>
      <h2>hi!</h2>
      <input placeholder="name" {...name}></input>
    </div>
  );
};
export default Practice;
```

### 발리데이션 추가

```JS

const Practice = () => {
  const useInput = (init, valid) => {
    const [value, setValue] = useState(init);
    const onChange = (event) => {
      const {
        target: { value },
      } = event;
      let vvv = true;
      if (typeof valid === "function") {
        vvv = valid(value);
        console.log(vvv);
      }
      if (vvv === true) {
        setValue(value);
      }
    };
    return { value, onChange };
  };
  const max = (value) => value.length <= 10;
  const name = useInput("init", max);
  return (
    <div>
      <h2>hi!</h2>
      <input placeholder="name" {...name}></input>
    </div>
  );
};
export default Practice;
```

type of 로 function 이라면 변수명 막지었는데 vvv 라는 상태업데이트를 해줌

name.value 를하면 useInput 함수의 return 되는 {value, onchange} 가 뜨니까

{...name} 을 속성으로 넣으면 다해결됨
