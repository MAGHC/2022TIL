### handlebars 문법

app.js 에 가서 view engine 을 바꿔줘야됨

다만 핸들바는 express 에서 자동설치 되지않는 express 패키지 이므로 import

```js
const expressHbs = require("express-handlebars");


pug는 내장형이라서 app.engine 이 필요없지만 얘는 아니라서

app.engine('handlebars',expressHbs()) 첫번째인수 엔진이름 , 엔진()
뭐 에러 먹어서 찾아봤더니 강의랑 문법이 바귄듯

app.engine("handlebars", expressHbs.engine({ extname: "handlebars" }));


app.set('view engine', 'handlebars') // engine 에서 정의한 이름


```

### 핸들바에서의 동적 처리

```js

404.handlebar

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Page Not Found</title>
    <link rel="stylesheet" href="/css/main.css">
</head>

<body>
    <header class="main-header">
        <nav class="main-header__nav">
            <ul class="main-header__item-list">
                <li class="main-header__item"><a class="active" href="/">Shop</a></li>
                <li class="main-header__item"><a href="/admin/add-product">Add Product</a></li>
            </ul>
        </nav>
    </header>
    <h1>Page Not Found!</h1>
</body>

</html>


핸들바는 일반 html을 사용하기떄문에 pug 같이 안바꿔도된다고함
개꿀이

인가? 그냥 익숙하다 하여간


<title>Page Not Found</title>

이부분을 원래 우리가 보내는

app.use((req, res, next) => {
  res.status(404).render("404", { value: "value" });
});

value 가 보이게 하고싶다면
<title>{{value}}</title> 면 됨

조건부 렌더링

{{#if }}
	컨텐츠

{{#else}}
<h2>상품이없습니다</h2>
{{/if}}

다만 if 뒤에오는것은 true false 밖에 안됨으로. pug 마냥 .length >0 같은 식을 넣을수가없다.

res.render("shop", { prods: product, docTitle: "SHop", hasProduct: product.length > 0 }); 추가

{{#if hasProduct}}


반복은

{{#each prods}}
{{this.title}}
{{/each}}

각 item은
each 키워드안에

있을시에

this 키워드사용



main-layout 기능


app.engine("handlebars", expressHbs.engine({ extname: "handlebars", layoutsDir: "views/layout", defaultLayout: "main" }));


{{{body}}}

세개의 중괄호로 표현 가능


동적 스타일링

pug 랑 다르게 true false 밖에안됨으로 좀 쉬운 방식

shop 에서는 shop 값을 보내주고

add-product에선 add-productcss 값을 보내주고

{{#if addproductCss}}
<link href="/css/product">
{{/if}}

같은식으로 동적 임포트



<a class="{{#if activeShop}}active{{/if}}">
와같이 동적 스타일링

```

### ejs

```js

hanldebars 처럼 할필요없으므로 engine 같은거 다 삭제하고

pug 처럼 view engine ejs 하면됨

아. html 이랑 똑같음 퍼그만 자체 문법쓰는듯



<title><%= value %></title>

if 문 사용

ejs 는 그냥 js 문법을 사용가능


<% if(prods.length>0) {%>

컨텐츠

<% } else { %>

<h2>컨텐츠가없습닌다</h2>


<% } %>

each 도


그냥 for of 문 사용하면됨

<% for(let product of prods) { %>

<%= product.title%>


핸들바가 제일 나을줄알았는데 ejs 가 젤낫네..



레이아웃


views 에 includes 폴더 생성

네이밍은 자유지만 head.ejs 생성


<%- %>  %= 는 variables  %- 는 html

<%- include('includes/head.ejs') %> 이건... 믹스인인가 신기하게 짬뽕해서 쓰네

%= include 도 되지만 그냥 text로 나옴



//head.ejs 예시

<html lang="en">

  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />



//end.ejs 예시

</body>
</html>


// 동적 페이지들

<%- include('includes/head.ejs')%>
<body>
	<%- include('includes/navigation.ejs')%>
	<h1>hi</h1>
<%- include('includes/end.ejs')%>


// 고유 css link 는 냅둠
<%- include('includes/head.ejs')%>
<link href="css/style">



//동적 스타일링

퍼그랑 비슷하게 하면됨

삼항 연산자 사용가능

<%= path==='/admin/add-product'? 'active': '' %>



```

pug,handlebar,ejs 셋다 본 결과 ejs 가 가장 낫다.
