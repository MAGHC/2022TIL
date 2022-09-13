### 예시

http api- 컬렉션

- post 기반 등록

ex) 회원관리 api 제공

http api - 스토어

- put 기반 등록

ex) 정적 컨텐츠 관리, 원격 파일 관리

html form 사용

- 웹 페이지 회원 관리
- get, post 만 지원

회원관리 시스템

api 설계 - post 기반

회원목록 /members ⇒ get

등록 members ⇒ post

조회 members/{id} ⇒get

수정 members/{id} ⇒patch,put,post 수정은 개념적으로 patch 가좋다. 다덮어도좋다면 put 이지만 그런상황은 거의 없다

게시글 같은걸 수정한다고 하면 그때는 put 이 의미가있다. 전체를 수정하기떄문에

애매하다 ⇒ post

삭제 members/{id} ⇒ delete

/members 같은걸 컬렉션이라 부름

post - 신규 자원 등록 특징

- 클라이언트는 등록된 리소스의 uri 를 모른다. (id) 서버가 새로운 리소스 식별자를 만들어줌

- 컬렉션 /member

  - 서버가 관리하는 리소스 디렉토리

  - 서버가 리소스의 uri를 생성하고 관리

파일관리 시스템

api 설계 - put 기반 등록

파일목록 /files = > get

조회 files/{filename} = >get

등록 files/{filename} = >put // 파일 업로드하면 기존 파일 지우고 다시올려야되니까.

삭제 files/{filename} = >delete

대량 등록 files/{filename} = >post

put 신규자원 등록 특징

- 클라이언트가 리소스 uri 를 알고있어야된다.
- 클라이언트가 직접 리소스의 uri를 지정한다
- 스토어

  - 클라이언트가 관리하는 리소스 저장소

  - 클라이언트가 리소스의 uri를 알고 관리

  - 여기서스토어는 /files

대부분 post 기반 put은 정말 사용하는 비중이 없다

html form 사용

html form 은 get, post 만 지원

ajax 같은 기술을 통해 해결 가능

목록 /members⇒get

등록폼 /members/new⇒ get

등록 /members/new, /members⇒ post

조회 /members=/{id}⇒get

수정 /members/{id}/edit⇒get

수정 /members/{id}/edit , /members/{id}⇒post

삭제 /members/{id}/delete⇒post //컨트롤 uri

- 컨트롤 uri

get,post 만으로 지원하기에 제약이있어 해결을 위한 동사로 된 리소스 경로 사용

post에 /new / edit / delete 같은것들

http 메서드로 해결하기 애매한 경우 사용 (http api 포함)

참고하면 좋은 uri 설계 개념

[restfulapi.net/resource-naming](https://restfulapi.net/resource-naming/)
