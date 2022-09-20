sql 가서 기업용 말고 community 용 다운

커스텀 가서 워크브런치랑 server 다운

비밀번호 설정

함

워크 브런치 열리면 서버인스턴스 열수있음

스키마에가서 스키마 생성가능

node 에서 mysql 과 접근하려면

패키지를 설치해야 됨

npm install —save mysql2

mysql2 에 별의미는 없음 그저 최신버젼의 mysql

```js

//경로와 파일네임은 자유  util 폴더에 database.js


const mysql= require('mysql2')


sql에 연결하는 방법은 두가지가 있는데 하나는 쿼리를 실행하는데 사용할 수 있는 하나의 연결을 설정하고 항상 닫는것

쿼리가 끝나면 연결하고

이것의 단점은 모든 새쿼리에 대한 연결을 생성하기 위해 코드를 다시 실행해야된다

=> 많은 쿼리 발생 =>매우 비효율
그래서 구축된 데이터 베이스 및 성능저하 발생 가능


더 나은 연결방법? => pool 생성

const pool = mysql.createPool({
		host:'localhost'
		user:'root',
		database:'아까 만든 스키마',
		password:"설치할때 적은 패스워드"

})

단일 연결이지만 언제라도 항상 연결 될 수 있는 연결 풀

실행되어있으면 풀에서 늘 새 연결을 찾음  각 쿼리에는 자체 연결이 필요하고 한번만 필요함으로 동시실행가능


애플리케이션 종료 시 풀 완료

module.exports = pool.promise();
로 내보냄




const db = require('./util/database')

이제 db. 해보면 몇가지가 자동으로 있는걸 알수있는데

그중 end 는 끄는거

db.execute('')로실행하는데 인자로 들어가는건 sql 구문

```

mysql 로 돌아가서 아까만든 스키마 - > 테이블 생성

속성값

nn = not null

uq= 유니크

b= 바이너리 데이터

un=unsigned data 음수값을 보유하지 않는경우 시작하는 정수

zf = 0채우기

ai = 자동증가

아이디를 만든다. uq/ai / un /nn 설정

데이터타입 int / double(소수점)/ varchar(글자수)/TEXT

```js

CREATE TABLE `node-complete`.`product` (
  `id` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `title` VARCHAR(255) NOT NULL,
  `price` DOUBLE NOT NULL,
  `decription` TEXT NOT NULL,
  `imageUrl` VARCHAR(255) NOT NULL,
  UNIQUE INDEX `id_UNIQUE` (`id` ASC),
  PRIMARY KEY (`id`));
//생성하면 나오는 sql 메세지 그냥 복붙해봄


sql에서 더미 데이터 작성가능




db.execute('SELECT * FROM products')
테이블 이름 맞춰야됨



db.execute("SELECT * FROM products")
  .then((result) => {
    console.log(result[0], result[1]);
  })
  .catch((err) => {
    console.log(err);
  });


//model/product.js

json으로 작성했던거 다 삭제후 재 작성

컨트롤러 도 수정

db.excute()는 프로미스이기 때문에

Product.fetchAll()
    .then(([rows, filedata]) => {
      res.render("shop/product-list", {
        prods: rows,
        pageTitle: "All Products",
        path: "/products",
      });
    })
    .catch((err) => console.err(err));

구조분해할당 활용
```
