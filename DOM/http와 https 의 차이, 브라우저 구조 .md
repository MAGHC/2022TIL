### http/https 차이

알다시피 http 는 인터넷 통신 규약 프로토콜이다.

web Apis security 는
사용자의 권한이나, https 를 요구할수있다고 하는데

http는 그렇다 치고 s 가 붙은 저건 뭘까?

s는 바로 secure 로 보안처리가 됨을 의미한다.

그냥 http 는 아무 처리없이 정보들을 보낸다면

https 는 암호화를 통해 주고받는다.

### 브라우저 구조

window객체에

screen : 모니터 크기
outer : 브라우저 전체 크기 (조절 창 다 포함)
inner: 조절창 빼고 브라우저 안에 크기 (스크롤 바 포함)
documentElement.clientWidth : 스크롤 바 까지 뺴고 난 다음의 브라우저 안 컨텐츠 크기

아 참고로 마지막꺼는 window 객체아니고 document 객체

document.documentElement.clientWidth 로 찾아야됨
