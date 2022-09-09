### id 표현

input(type="text" name="title")#title

띄어쓰기 같은게 되게 중요하다 하나라도 인덴트 안맞거나 하면 안됨 예전 파이썬 잠깐했던 기분

### layout 만들기

views 폴더 에 layout 생성

main-layout.pug 생성

block 으로 훅을 달아 서 동적으로 렌더링 가능

block

extends 키워드로 확장 가능

```js
404 페이지로 예시

// 404.pug 를 main-layout에 복사

//main-layout 코드

doctype html
html(lang="en")
    head
        meta(charset="UTF-8")
        meta(http-equiv="X-UA-Compatible", content="IE=edge")
        meta(name="viewport", content="width=device-width, initial-scale=1.0")
        title #{value}
    body
        header.main-header
            nav.main-header__nav
                ul.main-header__item-list
                    li.main-header__item
                        a.active(href="/") Shop
                    li.main-header__item
                        a(href="/admin/add-product") Add Product
        block content//block 으로 훅을 달음



//404.pug

extends layout/main-layout.pug

block content
    h1 Page not found


부차설명 안해도 직관적인듯 저렇게 확장한다음에. 훅달은 내용 밑에 추가


html(lang="en")
    head
        meta(charset="UTF-8")
        meta(http-equiv="X-UA-Compatible", content="IE=edge")
        meta(name="viewport", content="width=device-width, initial-scale=1.0")
        title #{value}
				block styles



extends layout/main-layout.pug

block styles
				link(rel="stylesheet", href="/main.css")
        link(rel="stylesheet", href="/product.css")

로도 활용 가능


뭐 레이아웃 nav footer 쓸때써먹으면될듯




```
