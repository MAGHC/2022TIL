### 스토리 북으로 컴포넌트 디자인 설계

설계의 중요성을 알고 설계를 위해서

공식문서 보면서 공부중이다.

와이어 프레이밍 도 있긴 한데 그걸 전문적으로 하는지는 좀 찾아봐야될 것 같고

그냥 이해하기론 와이어 프레임은 콘티 그리듯 대강 그리는게 아닌가 차라리 디자이너 입장에서 어떻게 콘티를 그려주면 소통에 원활한지 같은걸 생각해보는게 낫지않을까 뭐 나라면 내가 만드는거니까 내가 이해하기 쉽게 구체화해서 도식화하는 연습

https://storybook.js.org/tutorials/design-systems-for-developers/react/ko/build/

인스톨

`npx sb init`

실행

`yarn storybook` // npm stroybook

깔면 온갖 폴더들이 알아서 생성된다.

//Task.jsx

```js

import React from 'react';

import Task from './Task';

export default {
  component: Task,
  title: 'Task',
};


컴포넌트에 Task 컴포넌트

title 이 스토리북 사이드에 뜨는 이름
const Template = (args) => <Task {...args} />;

이런식으로 템플릿을 바인드 시킴  task 의 템플릿을 args 넣어서 설정가능한듯

export const Default = Template.bind({});
Default.args = {
  task: {
    id: "1",
    title: "Test Task",
    state: "TASK_INBOX",
    updatedAt: new Date(2021, 0, 1, 9, 0),
  },



export const Pinned = Template.bind({});
Pinned.args = {
  task: {
    ...Default.args.task,
    state: "TASK_PINNED",
  },
};

기본값을 따라오고.

그다음 얘만의 고유 state

export const Archived = Template.bind({});
Archived.args = {
  task: {
    ...Default.args.task,
    state: "TASK_ARCHIVED",
  },
};
```

이게 핵심인것 같다. 더 봤는데 컴포넌트를 만들고 해당 값들로 뭘 넣는지를 조금 더 연구해봐야될듯 그냥 컬러 정도만 생각해봤었는데

다크모드 나 다른 옵션들로 뭐가 들어가는지를 좀 더 봐야 컴포넌트 설계나 사용에 유용할듯

### 기본 버튼 설계

기본 클래스네임 설계 <button type="button" className={`button button__${mode} button__${mode}--${size}`}>

props 로 해당 설정들 내려 받아서 어떻게 변경 시킬건지

### 스토리 북 화면에 나오는 최소조건

그냥 혼자 실험해보면서 알음

```js
import React from "react";

import { ButtonSelf } from "../components/ButtonSelf";

export default {
  title: "컴포넌트/ButtonSelf",
  component: ButtonSelf,
  parameters: {
    layout: "cetered",
  },
};

const Template = (args) => {
  <ButtonSelf {...args}></ButtonSelf>;
};

export const Primary = Template.bind({});

Primary.args = {};
```

그러니까 Template 을 설정하고

하나의 테이블 이 있어야됨

지금은 primary

타이틀 같은경우 설정 안하면 뭐 자동이라는데 응 설정 안하게 되면 알아서 컴포넌트 이름으로 생성됨

정확히는 ‘stories/컴포넌트이름’

### 화면에 비추는 레이아웃

```js
// Button.stories.js|jsx|ts|tsximport { Button } from './Button';export default {
  /* 👇 The title prop is optional.
  * See https://storybook.js.org/docs/react/configure/overview#configure-story-loading
  * to learn how to generate automatic titles
  */
  title: 'Button',
  component: Button,
  // Sets the layout parameter component wide.
  parameters: {
    layout: 'centered',
  },
};

```

이건 스토리북 공식 문서에서 가져옴 cetnered 하면 보여지는 화면들이 가운데로 보여줌

### conTrol 설정

스토리북의 control 은 어떻게 설정되어지는가 보니까 해당 컴포넌트에서

```js
import PropTypes from "prop-types";

ButtonSelf.propTypes = {
  size: PropTypes.string,
};

ButtonSelf.defaultProps = {
  size: "medium",
  mode: "light",
};

각 컴포넌트 마다 넣어줘야되는듯

컴포넌트 명.proptypes 는 참고로 소문자

size: PropTypes.bool 같은 형식으로 타입 지정해줘야 제대로 나옴

그리고 디폴트는 설정해줘야 컨트롤해 항목이뜬다.


size: PropTypes.oneOf(['small', 'medium', 'large']),

로하면 이중 하나 라디오


label: PropTypes.string.isRequired,

로 필수값 설정 가능

그 밖에 타입들은 더 봐야될듯 일단 버튼 컴포넌트만 봤음



```

### 아토믹 디자인

과학 원소주기율표에서 영감을 얻은듯
