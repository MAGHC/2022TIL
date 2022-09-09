### http 메서드 활용

데이터 전달하는 방식은 크게 2가지

쿼리 파라미터를 통한 데이터 전송

주로 get / 정렬 필터 (검색어)

메세지 바디를 통한 전송

포스트,풋,패치

가입,주문,등록,변경

### 정적 데이터 조회

이미지, 정적 텍스트 문서

조회는 겟

정적 데이터는 쿼리 파라미터 없이 리소스 경로로 단순 조회 가능

### 동적 데이터 조회

쿼리파라미터를 기반으로 정렬 필터를 해서 결과를 동적으로 생성

조회는 get

get은 쿼리 파라미터를 사용해서 데이터를 전달

### form 태그를 통한 전송

이거 최근에 node 해서 해가지고 어찌저찌 참 타이밍 잘맞네

name 이 중요

body-parser

buffer

전송버튼의 메서드를 get으로 바꿀수도있다.

아

get으로 바꿀수만있고 어따쓰나했더니

저걸로 동적 조회가 가능 하네

get으로 바꾸고 원래 form 안에있던 input 의 name 과 value 가 키벨류로 메세지바디로 들어갔던것이 쿼리 파라미터로 들어가버림

get/save?username=sdaadasd&age=12313

form 으로 파일 전송할떄 enctype =”multipart/form-data”

보내면 웹 브라우저에서 boundary 라는것을 가지고 자른다(자기가 자동으로)

다른 종류의 여러파일과 폼의 내용함께 전송가능하다 = 그래서 multipart

html 폼 전송은 get,post 만 지원한다.

### api 전송

서버to 서버로

앱클라이언트에서도 사용

웹클라이언트 = > ajax

content-Type:application/json 을 주로 사용한다(사실상표쥰)

- TEXT,XML,JSON
