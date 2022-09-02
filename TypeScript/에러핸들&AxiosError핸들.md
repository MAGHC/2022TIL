### 에러 핸들링

```ts
try{

    const practice = async()=>{
       const res = await (){
            ...code
        }
        return res
    }


}catch(err){
    ...code


}
의 형태지만 타입스크립트에선 그대로 쓰면 쓸수가없다.

catch(err){
    if(err instanceOf Error){
console.log(err.message )
    }


}
로 처리해줘야 사용 가능하다 .



```

### axios 에러 핸들링

https://github.com/axios/axios/issues/3612

깃헙 이슈를 보고 해결했다

아니 내가 이슈를 뒤져본건 아니고 검색했는데 이슈가나왔다 뭐아무튼

```ts


.catch((err: Error | AxiosError) => {
        if (axios.isAxiosError(err)) {
          if (err.response?.status === 400) {
            alert("이메일, 비밀번호를 확인해주세요");
          } else {
          alert("서버를 확인해주세요! ");
        }
        }
      });
```

크게 다를 건 없다 instanceOf 부분에 err를 저런식으로 axiosError 인지 확인하고

단지 이제 좀 자바스크립트 좀 알겠다 싶었더니 이제 메서드들의 타입같은것도 같이 봐야되겠구나 인자에 뭐가 들어가고

그런것들이 좀 더 자바스크립트에 대한 심화 공부가 되겠구나 하는 생각이 들었고 많이 모자라다는 생각이 들었다

갑분일기 다른분들의 코드를 보니까 에러범위도 정해주는것 같았다 코드 자체가 어렵다기보다 대략적으로 왜쓰는지 알거는같은데 그냥 감에 불과해서 쓰지는 않았다.
