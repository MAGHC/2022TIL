### 문제

양수 N을 이진법으로 바꿨을 때, 연속으로 이어지는 0의 갯수가 가장 큰 값을 return해 주세요.

- 이어지는 0은 1과 1사이에 있는 것을 의미합니다.
- 1과 1사이에 있는 0을 binary gap 이라고 하겠습니다.

```
input: 9
output: 2
```

설명: 9의 이진수는 1001 입니다.
1과 1사이에 있는 0은 2 이므로, 2를 return

```
input: 529
output: 4
```

설명: 529의 이진수는 1000010001 입니다.
binary gap은 4와 3 두개가 있습니다.
이 중 큰 값은 4이므로 4를 return

```
input: 20
output: 1
```

설명: 20의 이진수는 10100 입니다.
1과 1사이에 있는 연속된 0의 수는 1 뿐입니다.
(뒤에 있는 0은 1사이에 있는 것이 아니므로)

```
input: 15
output: 0
```

설명: 15의 이진수는 1111 입니다.
binary gap이 없으므로 0을 return

```
input: 32
output: 0
```

설명: 32의 이진수는 100000 입니다.
binary gap이 없으므로 0을 return

### 풀이

```js
const solution = (N) => {
  const decimal = N.toString(2).split("1"); // 이진수로변경  후 1을 기준으로 split

  const zzz = decimal.map((item) => {
    // map 돌려서 0 있으면 길이 반환
    if (item.includes("0")) {
      return item.length;
    } else {
      return 0; //없으면 0
    }
  });

  const sort = zzz.sort((a, b) => b - a); // 정렬

  console.log(sort);
  return sort[0];
};

console.log(solution(32));
```

하면? 7개의 테스트중 5개만 통과가된다

이유가 뭐지? 하고 예시에있는걸 하나하나 넣어보니

input: 20
output: 1

설명: 20의 이진수는 10100 입니다.
1과 1사이에 있는 연속된 0의 수는 1 뿐입니다.
(뒤에 있는 0은 1사이에 있는 것이 아니므로)

이런 케이스가 통과가 안된것같았다.

아 for문으로 바꿔야되나? 생각하다가 잘 생각해보니 마지막 배열만 없애면되는거잖아

```js
const decimal = N.toString(2).split("1");

const zzz = decimal.map((item) => {
  if (item.includes("0")) {
    return item.length;
  } else {
    return 0;
  }
});
zzz.pop(); //추가

const sort = zzz.sort((a, b) => b - a);

return sort[0];
```

그나저나 종종 귀찮거나 바로 생각안나면 변수명 막짓는데 고쳐야겠다 zzz 이뭐냐
