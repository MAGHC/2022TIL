### 그냥

```js
if (navigator.geolocation) {
  navigator.geolocation.getCurrentPosition(
    function (position) {
      const { latitude } = position.coords;
      const { longitude } = position.coords;
    },
    function (err) {
      alert(err);
    }
  );
}
```

그냥 이렇게썼다고 기록해두고싶었음
