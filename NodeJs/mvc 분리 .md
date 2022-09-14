### mvc

모델 뷰 컨트롤러

뷰는 사실 이미 나누어져있다 (html)

모델과 컨트롤러를 나누면됨

모델 = > 라우터

컨트롤러 = > 라우터 안에있는 로직

```js
const product = [];

router.get("/add-product", (req, res, next) => {
  res.render("add-product", { title: "asd", path: "/admin/add-product" });
});

router.post("/add-product", (req, res, next) => {
  product.push({ title: req.body.title });
  res.redirect("/");
});

이런 라우터 부분이 사실상 컨트롤러
product를 다룸



controller 폴더 생성
product.js 생성

(req, res, next) => {
  res.render("add-product", { title: "asd", path: "/admin/add-product" });
}


//product.js
exports.getproduct = (req, res, next) => {
  res.render("add-product", { title: "asd", path: "/admin/add-product" });
};

exports.postProduct = (req, res, next) => {
  product.push({ title: req.body.title });
  res.redirect("/");
};
//admin.js

const productController = require("../controller/product");

router.get("/add-product", productController.getproduct);

router.post("/add-product", productController.postProduct);

// shop.js 도 동일하게 변경 똑같은 product 데이터를 사용하기떄문


//404 .js 컨트롤러 생성 및 동일
module.exports = (req, res, next) => {
  res.status(404).render("404", { value: "value" });
};



// 이 시점에 컨트롤러 product 전체 코드

const product = [];

exports.getproduct = (req, res, next) => {
  res.render("add-product", { title: "asd", path: "/admin/add-product" });
};

exports.postProduct = (req, res, next) => {
  product.push({ title: req.body.title });
  res.redirect("/");
};

exports.getShop = (req, res, next) => {
  const product = adminData.product;
  res.render("shop", { prods: product, docTitle: "SHop", hasProduct: product.length > 0 });
};

//models 폴더 생성 , product.

const product = [];

module.exports = class Product {
  constructor(title) {
    this.title = title;
  }
  save() {
    product.push(this.title);
  }
  static fetchAll() {
    return product;
  }
};


컨트롤러에서 produtct 관련된 것들 삭제 및 변경

// 컨트롤러 product.js
const Product = require("../models/product");

exports.getproduct = (req, res, next) => {
  res.render("add-product", { title: "asd", path: "/admin/add-product" });
};

exports.postProduct = (req, res, next) => {
  const product = new Product(req.body.title);
  product.save();
  res.redirect("/");
};

exports.getShop = (req, res, next) => {
  const products = Product.fetchAll();
  res.render("shop", { prods: products, docTitle: "SHop", hasProduct: products.length > 0 });
};

```
