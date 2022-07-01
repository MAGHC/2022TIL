import styled from 'styled-components'

Npm i styled-component

장점 : n o css

다른 파일들이 간섭 안함

**참고로 간섭안하는 문제는 css이름 지을때 ~~이름.module.css 로 해결 가능 **

스타일 클래스 리스트 같은 거 ㅇ 그페이지안에서만 사용가능

이러면 app.js 에만 종속이됨

    3. 로딩시간 단축 css파일 로딩을 안하기 때문

단점 : js파일 ㅈㄴ 복잡해짐

다른 파일에서 스타일 쓰려면 임포트 하는데 그러면 css랑 비슷함

단점 3 협업시 css담당의 숙련도 이슈 (못알아볼수도있다)
