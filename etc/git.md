깃에대한 전반 적인 추가적인 지식들 추가

### upStream

git push -u origin main ?

-u ??

= upstream

= 상류

하는 이유? => 관계설정

remote 저장소 → 우리의 리모트 origin → 로컬 이있다.

깃클론 하면 자동적으로 업스트림 설정됨

### 용어

blob : 파일
commit :저장 단위, tree+blob + 메타 정보
tree: blob을 묶어서관리(디렉토리와 유사하다)
tag: 커밋에 대한 참조, 설명이 추가되는 객체

### help

명령어 뒤에

--help를 치면 설명을 볼 수 있다.

ex) git commit --help

### cherry-pick

https://www.youtube.com/watch?v=b72mDco4g78

기능 1,2,3 이 순차적으로 있는데

기능3은 미완이라 올리기싫고

2만 올리고싶다 => 체리픽
보통 바로
메인에 푸쉬하기보단

cherrypick 브랜치를 생성해서 브랜치 푸쉬후 pr을 남겨 머지를 시킨다.
