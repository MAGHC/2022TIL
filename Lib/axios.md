### axios.create()

https://axios-http.com/docs/instance

axios.create() 로 인스턴스를 생성 가능하다.

예제 는 이런식으로 나와있다.

```js
({
  baseURL: "https://some-domain.com/api/",
  timeout: 1000,
  headers: { "X-Custom-Header": "foobar" },
});
```

```ts
axios.create({
  baseURL: "https://some-domain.com/api/",
  timeout: 1000,
  headers: { "Content-Type": "application/json" },

});

export const API = axios.create({ baseURL: BASE_URL, timeout: 1000, headers: { "Content-Type": "application/json" } });
같은 형식으로 작성했다

이전에는 config.js 라는 파일로

const BASE_URL = ""

const API={
todos:`${BASE_URL}/todos`

}

같은 느낌으로 정리했었는데

지금은 API.tsx 파일을 생성하여 axios create 로 기본적인 것을 생성해두고 저걸 불러서 사용한다.



hooks 에

export const useFetch = <T, V>() => {
  const getDate = async (url: string): Promise<T> => {
    const res = await API.get(url);

    return res.data;
  };

  const postData = async (url: string, body: V): Promise<T> => {
    const res = await API.post(url, {
      ...body,
    });

    return res.data;
  };

  return { getDate, postData };
};

같은 형태로 현재는 get 과 post 만 구현해둔 상태이다.

여기에 로그인 함수를 또 만들어서 관리하게 되는데 hooks 를 쓰니까 확실히 뭐 다 분리하진 않아도 어느정도 분리해서 관리도 용이한것 같다.

useLogin=(body)=>{
    const submit=async()=>{
         return postData(`/users/login`, body);
    }
}
같은 형식으로 보내게 되는데

이제 에러 핸들링이랑 success 처리를 해줘야된다.





```

### axios.interceptors

https://axios-http.com/kr/docs/interceptors

인터셉트 가 가능하다
axios.interceptors.response.use()

의 형태로 모든 성공시 response 에서 할 반응 을 기본적으로 내가 설정해 줄 수 있다.

```ts
axios.interceptors.response.use(
	(res) => {
		if (res.data.token) {
		   해당 코드
		}
	  return res;
	},
	(error) => {
	  return Promise.reject(error);
	}
);
```
