배열에 넣는 방식이 아닌 data를 파일로 저장시킬것임

```js

const fs = require("fs");
const path = require("path");

// 모듈 임포트



완성된 save  method


save() {
    const p = path.join(path.dirname(process.mainModule.filename), "data", "products.json");
    fs.readFile(p, (err, fileContent) => {
      let products = [];
      if (!err) {
        products = JSON.parse(fileContent);
      }
      products.push(this);
      fs.writeFile(p, JSON.stringify(products), (err) => {
        console.log(err);
      });
    });
  }

this 말고 this. title 해야되는 거아닌가? 했는데 그러면 키밸류 형태가아니고 벨류만 들어감

하고

prods.length 가 없다는 에러가 뜸으로


fetchAll 함수 변경
static fetchAll(cb) {
    fs.readFile(p, (err, fileContent) => {
      if (err) {
        cb([]);
      }
      cb(JSON.parse(fileContent));
    });
  }
};


getShop 변경

exports.getShop = (req, res, next) => {
  Product.fetchAll((products) => {
    const productss = Product.fetchAll();
    res.render("shop", { prods: productss, docTitle: "SHop", hasProduct: products.length > 0 });
  });
};

물론 제품 아이디추가에는 외부라이브러리 같은것을 이용하는게 제일 좋겠지만 지금은 math.random() 으로 생성



save() {
    this.id = Math.random().toString();
    getProductsFromFile((products) => {
      products.push(this);
      fs.writeFile(p, JSON.stringify(products), (err) => {
        console.log(err);
      });
    });
  }


//shop / product-list 파일
 <a href="/products/<%= product.id %>" class="btn">Details</a>

detail 버튼



//routes 폴더

router.get("/products/:productId");

//컨트롤러/ shop.js
exports.getProduct = (req, res, next) => {
  const prodId = req.params.productId;
  console.log(prodId);
  res.redirect("/");
};
params 이름이랑 맞춰줘야됨

콘솔에 id 잘 찍힘

```
