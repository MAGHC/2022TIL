### 문제

아직까지도 문제를 완전히 무슨 소린지 이해를 못하겠는 게 문제 프로그래밍적 인 생각 뭐 그런것들이 앞으로 점점 풀면서 나아지겠지만 다 읽었는데도 이게 뭔말인지 그리고 예시를 보고 이렇게 하라는거구나 는 알겠는데

예외 사항 이라던지 제약 부분도 뭔 이야긴 지 정확히 알고 푼다고는 못하겠음

배열 두개가 들어가는데 그 배열은 순서가 역순이다

각 배열의 순서를 원래대로 돌려서 합을 더한다음에 다시 역순의 배열을 만들라고 이해했음

### 각 배열을 받아서 숫자 총합 만든 뒤에 숫자 배열로 변환

IIfe 개념 활용해봤고

마지막에 map을 써서 숫자타입의 배열로 다시 변환 시킴

nums / target은 첫번째 문제에서 썻던 변수명 가져온거라 의미없음

```Js

const nums = [2, 5, 5, 3];
const target = [2, 5, 5, 11];

var twoSum = function (nums, target) {
const reverse = nums.reverse();
const reverse2 = target.reverse();

const reverseInt = (function () {
let result = 0;
for (let i = 0; i < reverse.length; i++) {
result += reverse[i];
}
return result;
})();
const reverseInt2 = (function () {
let result = 0;
for (let i = 0; i < reverse2.length; i++) {
result += reverse2[i];
}
return result;
})();

const sum = reverseInt + reverseInt2;

const sumArray = sum
.toString()
.split("")
.map((item) => parseInt(item));

console.log(sum, sumArray);
};

console.log(twoSum(nums, target));
```

이렇게 했다가

아 안의 요소들을 다 그냥 숫자로 더하면 안되고 문자로 더해야

3,4 가 있으면 34 가된다는걸 망각하고 있었음

바꿈

```Js


const nums = [2, 5, 5, 3];
const target = [2, 5, 5, 11];

var twoSum = function (nums, target) {
  const reverse = nums.reverse();
  const reverse2 = target.reverse();

  const reversel1Sum = (function () {
    let result = "";
    for (let i = 0; i < reverse.length; i++) {
      result += reverse[i].toString();
    }
    return parseInt(result);
  })();
  const reversel2Sum = (function () {
    let result = "";
    for (let i = 0; i < reverse2.length; i++) {
      result += reverse2[i].toString();
    }
    return parseInt(result);
  })();

  const sum = reversel1Sum + reversel2Sum;

  const sumArray = sum
    .toString()
    .split("")
    .reverse()
    .map((item) => parseInt(item));

  console.log(sumArray, sum);
};

console.log(twoSum(nums, target));

```

let result = 0 하니까

0123412 이렇게되서 아예 빈 string으로 변경

문자숫자변환과정을 거친뒤 다시 계산

이런 제기랄 그냥 타입 선언한걸줄 알고 넘겼는데 안된다 해서 봤더니

배열이 아니고 ListNode 라는 자료구조라고 한다 뭔데 이런거 js 에 없잖아

- Definition for singly-linked list.
- function ListNode(val, next) {
-     this.val = (val===undefined ? 0 : val)
-     this.next = (next===undefined ? null : next)
- }

아.. 그래도 뭐 썩 재미있는 시간이였다 어째 코드가 길고 더럽고 그런거랑 별개로 쉽게 풀린다했다

일단 07.25 잠시 listNode 라는 자료구조를 따로 알아야될 거 같다 이해를 제대로 못했다.
