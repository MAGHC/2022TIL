String 생성자 함수

표준 빌트인 객체인 String 객체는 생성자 함수객체다. 따라서 new 연산자와 함꼐 호출하여 String 인스턴스를 생성할 수 있다.

String 생성자 함수에 인수를 전달하지 않고 new 연산자와 함꼐 호출하면 [[]]stringData 내부 슬롯에 빈 문자열을 할당한 String 래퍼 객체를 생성한다.

New String()
//String{length:0[[]]primitiveValue:""}

New String('lee')

// string(0:"l",1:"e",2:"e",length 3)
아 갑자기 문득깨달음이 그래서 . Length 하면 저 객체의 legnth 가 나오는건가보다

스트링 래퍼 객체는 배열과 마찬가지로 인덱스를 나타내는 숫자형식의 문자열을 프로퍼티키로 각문자를 프로퍼티 값으로 갖는 유사 배열 객체이면서 이터러블이다.

그래서 인덱스를 사용하여 문자에 접근가능

문자열은 원시값이므로 변경할수없지만 에러가 발생하지않음

String 생성자 함수의 인수로 문자열이 아닌 값을 전달하면 인수를 문자여로 강제 변환한 후 [[]]stringData 내부 슬롯에 변환된 문자열을 할당한 string 래퍼 객체를 생성한다.

9new 연산자를 사용하지 않고 string 생성자 함수를 호출하면 인스턴스가 아닌 문자열을 반환한다.

이를 이용하여 명적으로 타입변환하기도 함.

Length 프로퍼티
string 래퍼 객체는 배열과 마찬가지로 length 프로퍼티를 갖는다. 그리고 인덱스를 나타내는 숫자를 프로퍼티 키로, 각 문자를 프로퍼티 값으로 가지므로 String 래퍼 객체는 유사배열 객체이다.

String 메서드

문자열은 변경불가능한 원시값이기때문에String 래퍼 객체도 읽기전용객체로 제공된다.

String.prototype.indexOf

인수로 전달 받은 문자열을 검색하여 첫번째 인덱스를 반환한다 실패하면 -1 반환

두번째 인수로 검색을 시작할 인덱스를 전달가능

('l',3) -> 3번째부터 l있는지

('hello') 같은것도 가능

String.prototype.includes 를 사용하면 가독성이 더 좋다.

String.prototype.search

Search 메서드는 대상 문자열에서 인수로 전달받은 정규 표현식과 매치하는 문자열을 검색하여 일치하는 문자열의 인덱스를 반환한다. 검색에 실패하면 -1을 반환한다.

아 이런게있었네 뭣도모르고어제 실험할때 match 썻네 아근데 짜피 이건 인덱스반환하는구나

String.prototype.includes

결과를 true /false로 반환한다.

String.prototype.startsWith

전달받은 인수의 문자열로 시작하는지 확인하여 true /false 반환

String.prtotype.endWith

반대 그걸로 끝나는지

.cartAt

대상 문자열에서 인수로 전달받은 인덱스에 위치한 문자를 검색하여 반환한다.

인덱스는 문자열의 범위 0~(문자열의 길이-1) 사이의 정수여야되며 범위를 벗어나면 빈 문자열 반환

.substring

대상 문자열에서 첫번째 인수로 전달받은 인덱스에 위치하는 문자부터 두번째 인수로 전달받은 인덱스에 위치하는 문자의 바로 이전 문자까지의 부분 문자열을 반환한다.

Substring(1,4) => 1,2,3 의 문자열이나옴

indexOf 메서드와 함꼐 사용하면 특정 문자열을 기준으로 앞위에 위치한 문자열을 취득할 수 있다.

Slice

Substirng 메서드와 동일하게 동작한다 단, 음수인 인수를 전달 할 수있다.

음수의 인수를 전달하면 대상 문자열의 가장 뒤에서 부터 시작하여 문자열을 잘라냄

.toUpperCase

대문자
.toLowerCase

소문자

.trim

문자열 앞뒤에 공백이있으면 이를 제거한 문자열을 반환한다.

어따씀 이거

.repeat

대상 문자열을 인수로 전달받은 정수만큼 반복해 새로운 문자열을 반복한다.

정수0이면 빈 문자열 음수면 RangeError

.replace

첫번째 인수를검색하여 두번쨰랑 바꿈

첫번쨰 정규식 갈기고 두번째 변경도 가능

.split

대상 문자열에서 첫번째 인수로 전달한 문자열 또는 정규표현식을 검색하여 구분한 후 배열로 반환

Str.split(' ') 공백으로 구분하여 반환
Split('')문자하나하나 다 분해

두번째 인수로 배열의 길이 정할수있음

### 복습 + 활용및 사용

```js

indexOf = > return number
lastIndexOf -> return nubmer // 해당 글자의 마지막 해당하는 위치


slice() 인자에서 부터 자름  기본문자열을 변경하지 변수에 할당한다면 잘려진 것이 변수 들어감 기존문자열아님


slice() 하나만 받을수도있고 두개받을수도있음 두개는 각각 시작 / 끝 한개는 0부터 해당 시점까지 짜름


마지막은 -1

 이를 활용한 스페이싱있을 때 첫번째 단어 마지막 단어 찾기


const str = 'my name is kim'

console.log(str.slice(0, str.indexOf('')))
console.log(str.slice(0, str.lastIndexOf('')+1))



인자로 음수도 넣을 수 있음


const a = 'tap air portugal'

console.log(a.slice(1,-1)) // 'ap air portuga'


toLowerCase = 소문자

toUpperCase = 대문자



이름 자동 앞글자만 대문자 변환

		const name = kIm

const lowername = name.toLowerCase()

const corrctName = lowername[0].toUpperCase() + lowername.slice(1)


trim () 문자 양끝의 공백 제거


replace() 첫번쨰인자. 바꾸고 싶은것 두번째인자 . 바꿀것

replace => return string

문제 ?
같은단어가 여러개있어도 하나만 바꿈



replaceAll () 사용

정규식도있고. g 플래그 global



includes()
startsWith()
endsWith()

=> true , false 반환



split() 구분자를 인자에 전달하면 => 나눠서 배열로 return []

보통은 ('')



const [lastName, firstName]= 'kim jungsoo'.split('')

구조분해할당.



join('') 구분자를 인자에 전달하면 => 하나의 문자열로 합침



첫번째 글자만 대문자로 바꾸는 fucntion 만들기


const translateFirst = (word) => {
  const words = word.split(" ");
  const result = [];

  for (const item of words) {
    console.log(words);
    console.log(item[0]);
    result.push(item.replace(item[0], item[0].toUpperCase()));
  }

  console.log(result.join());
};

console.log(translateFirst("kim jung soo"));



string.padStart(24,"+")


string.padEnd(24,'+')

padding

length 24 일때까지 해당 문자의 앞/ 뒤에 두번째인자를 추가

string.padStart(24,"+").pad(30,'-')
와 같이도 사용가능



신용카드의 masking 기능 만들기


const maskedNumber = (number) =>{
const str = String(number)
const last = str.slice(-4)
return last.padStart(str.length ,'*')

}

console.log(maskedNumber (12341241413213))



repeat() 인자로 숫자를 넣으면 그숫자만큼 문자가 반복됨.

const flights =
  '_Delayed_Departure;fao93766109;txl2133758440;11:25+_Arrival;bru0943384722;fao93766109;11:45+_Delayed_Arrival;hel7439299980;fao93766109;12:05+_Departure;fao93766109;lis2323639855;12:30';

for (const flight of flights.split('+')) {
  const [type, from, to, time] = flight.replaceAll('_', ' ').split(';');
  const output = `${type}, ${from},${to},${time}`;

  console.log(output);
}







```
