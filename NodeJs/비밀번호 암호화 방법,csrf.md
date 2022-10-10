### csrf 란?

복제된 웹사이트에서 들어온 위조 요청으로 권한 도용하는거

=> 복제 웹사이트를 사용해서 돈 인출 등등

### csrf 토큰

csrf를 방지하기 위해 실서버와 동일한지 확인하는 토큰

### 비밀번호 암호화

npm install --save bcryptjs

방법. 첫 번째 값으로 해시 메서드는 해시하려는 문자열을 가져오고,

두 번째 인수는 양념값? 인데

몇 번의 해싱 라운드가 적용될 것인지 지정하는 것이라고함

값이 높을수록 시간이 오래 걸리지만 더 안전하다고.

값 12정도면 매우안전

```js
User.findOne({ email: email })
    .then(userDoc => {
      if (userDoc) {
        return res.redirect('/signup');
      }
      return bcrypt.hash(password, 12);//중복이메일이없다면 hash 값 인자1: string인자2: saltyvalue 라고하는데 양념값
    })
    .then(hashedPassword => {
      const user = new User({
        email: email,
        password: hashedPassword,
        cart: { items: [] }
      });
      return user.save();
    })
    .then(result => {
      res.redirect('/login');
    })
    .catch(err => {
      console.log(err);
    });
};
```

### 라우터 보호방법

auth 컨트롤러 폴더에 세션일치 확인 메서드 만들어놓고

next()

```js

rotuer.get('/',auth, adiminRouter.getAdmin) 같은형태로 넣으면 auth 걸쳤다가 다음라우터로 넘어가게됨


```
