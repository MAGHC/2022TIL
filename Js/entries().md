### entries()

Array.entries()

Array iterator

[1,item1]
[2,item2]

이런식으로 생성됨

For of 로 돌리면 확인 가능

For of 구조분해할당

For(const [I,el] of arr.entries())

로

인덱스와 element 나눠서 사용가능

const arr = [1, 4, 5, 5, 6, 6, 6, 3, 1, 2];

for (const [i, el] of arr.entries()) {
console.log(`${i} 인덱스 ${el} el `);
}

console.log(arr.entries());

0 인덱스 1 el
1 인덱스 4 el
2 인덱스 5 el
3 인덱스 5 el
4 인덱스 6 el
5 인덱스 6 el
6 인덱스 6 el
7 인덱스 3 el
8 인덱스 1 el
9 인덱스 2 el
Object [Array Iterator] {}

이런식으로 나온다.
