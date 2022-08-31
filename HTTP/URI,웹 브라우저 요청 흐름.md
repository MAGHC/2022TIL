### URI

uniform resoucrce identifier

URI>Url,Urn 이라 생각하면된다

URI 가 최상위 개념이고 그 안에 url , urn

url 은 리소스 위치 l 이 locator 를 의미

urn 은 리소스네임 n 이 name

### url

url의 전체 문법은

프로토콜 // 호스트명 // 포트번호/ 패스 / 쿼리 파라미터

로 이루어져있다.

프로토콜 : 어떤 방식으로 접근할것인가(http / ftp)
포트는 정리했듯이 http, https 80 / 443 생략 가능

패스 : /search 리소스 경로 계층적 구조로 되어있다

쿼리파라미터 : ?id 이런거 키 밸류 형태로 되어있다
key=value 형태
?로 시작하고 & 로 추가 가능
웹서버에서 제공하는 파라미터 , 문자형태
