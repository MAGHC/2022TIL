### useFetch

fetch 함수들을 정의한다.

```ts
const useFetch = <T, V>() => {
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


이런 식으로 해놓았다.
delete 나 다른것들도 추가해야되지만 일단 기본적인 것만 해놓았다.

get은 url 만 먾으면 되니 저런식으로 디자인 되어있고

postData 는 보낼 body 까지 참고로 header 는

이미 API 에서 axios.create() 로 세팅해둔 상태다.

그래서 API = > axios.create({baseurl, header:{} ...}) 같은 형태 로 설정되어있다.


```
