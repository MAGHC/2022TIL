### h1

h1은 구글 또는 다른 검색엔진 에 중요한 부분이다.

seo search engine opimize 뭐 하여간 검색엔진최적화

image 에 alt 속성도 마찬가지

h1을 단일로만 쓸 생각을 했는데 h1 안에 span이나 p태그를 넣어서도 활용가능

### figure / figcaption

figure: 그림 , 이미지요소 시맨틱 마크업 하는데 사용 보통 그 컨텐츠들을 감싼다.

활용은 css에서 shape out-side로 이미지 말고 해당 박스의 모양을 설정할 수 있다.

figcaption 말그대로 fig의 caption 이다 이미지나 동영상 인용문의 설명

### form /input / label

form 에 action 속성은 제출됬을때 사용할 js 파일 등을 말한다.

여기안에도 a 태그 마냥 href # 을 넣어둘수있다.

input id 와 label for 속성을 맞추면 해당 input 에 대한 label 만들수있는데

label 을 클릭하면 해당 인풋으로 포커싱 된다 .

### 특수 심볼

&rarr &nbsp 같은것들

https://css-tricks.com/snippets/html/glyphs/

사이트 참고

### input name

인풋에는 name 속성값이 있다 왜있는거지 하고 검색해서 w3c 스쿨에서 보니 뭐 활용에 참조를 위한 값이라고 적혀있고 아무것도 안적혀있길래 어쩌라는거지 하고있었는데

react로 구현하다가

운좋게도 바로 활용을 찾았다.

```js
const handleInput = (e: React.ChangeEvent<HTMLInputElement>) => {
  const { value, name } = e.target;
  setUserLogin({
    ...userLogin,
    [name]: value,
  });
};
```

name 값을 구조 분해할당으로 빼내어서 위와 같이 set 할때 원래 useState 의 키값과 맞춰서 넣을수있었다.

### meta

헤드는 웹사이트에 대한 정보가 있는곳

<head>
<meta name="description" content="설명">
</head>

같은 형태로 설명 추가 가능
