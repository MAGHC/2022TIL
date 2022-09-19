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

### 아토믹 디자인

과학 원소주기율표에서 영감을 얻은듯
