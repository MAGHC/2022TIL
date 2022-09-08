### 동적 html 을 위한 템플릿 엔진

동적 html 을 위해 템플릿 엔진을 쓰는데 가장 유명한것이

ejs

<p><%=name %></p>

일반적인 html 에서 사용

일반적인 js 사용

pug(jade)

p#{name}

미니멀 html 에서 사용 언어 커스텀 가능

Handlebars

<p>{{name}}</p>

일반적인 html , 커스텀 언어

이 세가지이다.

이렇게만 봤을땐 handlebars 가 가장 익숙해보인다 jsx 랑 다를 바 없어보이는데

### 설치 / 적용

npm install —save ejs pug express-handlebars

handlebars 는 express 안에있음

app/server.js 에 가서

app.set() 을 통해 전역설정

set 설정값은 많은데 ‘view engine’ 을 설정할것임으로

app.set(’view engine’,’pug’)

이미 폴더를 views 로 해서 설정할것은 없지만

app.set(’views’, ‘views’) 와같은형태로 설정한다고 만 알아두면됨

이제 html을 모아놨던 view 폴더에 가서 shop.pug 를 생성하면

귀여운 pug 강아지 아이콘이 생긴다 ㅋㅋㅋㅋㅋ

### pug 로 작성

```js

doctype html
html(lang="en")
    head
        meta(charset="UTF-8")
        meta(http-equiv="X-UA-Compatible", content="IE=edge")
        meta(name="viewport", content="width=device-width, initial-scale=1.0")
        title Document
    body


!로 자동완성해보면 알아서 pug 파일로 바뀌는데 희안하게 생기긴함



pug는 네스팅이 중요하다

header.main-header 와 같이 태그.클래스네임

다행히 스닙펫 사용으로 그렇게까지 어렵진않네

attribute 는 () 로 텍스트 컨텐트는 옆에다가 그냥 적으면 됨 띄어쓰고





<header class="main-header">
      <nav class="main-header__nav">
        <ul class="main-header__item-list">
          <li class="main-header__item"><a class="active" href="/">Shop</a></li>
          <li class="main-header__item"><a href="/admin/add-product">Add Product</a></li>
        </ul>
      </nav>
    </header>


가

header.main-header
              nav.main-header__nav
              ul.main-header__item-list
                li.main-header__item
                    a.active(href="/") Shop
                li.main-header__item
                    a.active(href="/admin/add-product") Add product

로

아 참고로 div 는 그냥작성할떄처럼 div.클래스네임 할필요없임
.클래스네임 해도됨




//shop.js

sendFile 부분을 변경할것임

res.sendFile(path.join(rootDir, "views", "shop.html"));
res.render('shop')

shop.pug 도 필요없고 다 지가알아서 찾는다



render method 를 사용하면 두번째 인수로 데이터를 전달 가능하다.

키벨류 형태로
const products = adminData.products
res.render('shop',{prods:products})

그러면 pug 에서 prods 를 사용가능

둘이상의필드도 전달가능

res.render('shop',{prods:products, docTitle:'shop'})


pug 에서 #{docTitle}로 사용



클래스 연결 은 . 으로 활용

ex) card product-item=>card.product-item




each product in prods 키워드로 반복


맨처음 product를 저장할때 했던 key 값 으로 사용
product.push({ title: req.body.title })//요거

h1.product__title #{product.title}


오 ㅋㅋ 조건부렌더링도됨


이거 하면서 걸리는 렉은 데부분 인덴트 때문에 생기는렉이네...

조심



최종 코드

if prods.length > 0
                .grid
                    each product in prods
                        article.card.product-item
                                header.card__header
                                    h1.product__title #{product.title}
                                div.card__image
                                    img(src="", alt="A Book")
                                div.card__content
                                    h2.product__price $19.99
                                    p.product__description A very interesting book about so many even more interesting things!
                                .card__actions
                                    button.btn Add to Cart
            else
                h1 Np

```
