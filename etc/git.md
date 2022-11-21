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

### fork 한 레파지토리 최신 화 시키기

업스트림 설정으로 최신화 시킬수있다.

git remote add origin 마냥 추가 가능

git remote add upstream 주소

git fetch upstream 하면

새로운 브랜치가생긴다.

그럼 그 브랜치를 merge

물론 내가 작업하는 브랜치에서도 merge

### stash

임시 스테이징 저장

rebase할때 스테이징 커밋하라고 난리치면 써먹는다

git stash apply 로 다시 가져올 수 있음

### 커밋지우기

git reabse -i 지우려고하는커밋의 직전커밋.

그리고 여러개 지울수도있고 맨위에꺼 drop 하고

이미 커밋이 올라가있다면 git push origin -f 로 강제로 보낸다.

### 커밋 수정하기

git commit --amend 로 가장 최신 커밋을 수정할수있다.
