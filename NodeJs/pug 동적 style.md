### 메인 레이아웃 동적 css

```js
//admin.js

res.render("add-product", { title: "asd", path: "/admin/add-product" })


//main-layout.pug
class=(path==="/admin/add-product" ? "active" : "")



```

class 네임에 ()로 path 사용하는데

path 를 전달하는게 아무래도 admin.js 임으로 해당경로가 맞다면 지금은 노란색으로 처리한 active 클래스가 적용될것

Title 부분도 이런 방식으로 각 페이지 마다 전달 동적 변경 가능
