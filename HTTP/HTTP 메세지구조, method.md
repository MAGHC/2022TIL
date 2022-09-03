### 메세지 구조

스타트 라인
헤더
공백라인
바디

로 이루어져있다.

시작 라인에는 요청라인(request-line )과 status-line 으로 이루어져있는데

요청라인에는 http 메서드, 요청대상 , 타켓, http 버젼이 있음

ex)GET/search?q=hello HTTP/1.1

method SP(스페이스바=공백 이란뜻) request-target SP HTTP-version CRLF(엔터)

요청메세지-요청대상

절대경로="/"[?query]

응답 메세지(status-line)

200 : 성공
400: 클라이언트 요청오류
500: 서버오류

200 ok 에서 ok 이유문구 사람이 알아먹을수있는 짧은 설명

- 헤더

전송에 필요한 모든 정보가 들어가있음

바디의내용,크기 압축, 인증 , 요청(클라이언트 정보), 서버정보 등등

필요시 임의의 헤더 추가가능

Content-Type

- 바디

실제로 전송한 데이터

html문서, 이미지, 영상,json 등등

? 크게 성공하는 기술은 단순하고 확장 가능한 기술 => http 가 그렇다

### method

api url을 디자인할때

리소스와 행위를 분리하면된다.

resource 와 method
