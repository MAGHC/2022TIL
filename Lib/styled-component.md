### styld.d.ts

theme provider 로 보냈는데 theme 를 쓸때마다 자동완성이 안되었다. 그리고 에러가 났는데

이것떄문이 아니였다만 하여간 결국 했어야되는 작업이였기에 적는다

.d.ts 는 이미 예전에 타스를 배울때 배웠다시피 type 을 정의 하는 파일이다. 프로젝트 최상위에서 생성해야된다.

https://styled-components.com/docs/api#typescript

```ts

// import original module declarations
import 'styled-components';

// and extend them!
declare module 'styled-components' {
  export interface DefaultTheme {
    borderRadius: string;

    colors: {
      main: string;
      secondary: string;
    };
  }
}
공식
예제가 너무 직관적이라서 사실  보고 뭘 더 할 건 없었고 예제대로 적용했다.


import "styled-components";

declare module "styled-components" {
  export interface DefaultTheme {
    colors: {
      primary: string;
      primaryLight: string;
      primaryDark: string;
      secondary: string;
      secondaryLight: string;
      secondaryDark: string;
      font: string;
    };
    mixin: {
      center: () => string;
    };
  }
}


DefaultTheme 는 theme 로 내려줄 styld 에 붙여주면 알아서 저 타입 정의들이 같이 붙는다.

import { DefaultTheme } from "styled-components";

export const styled: DefaultTheme = {
  colors: {
    primary: "#e3f2fd",
    primaryLight: "#ffffff",
    primaryDark: "#b1bfca",
    secondary: "#fafafa",
    secondaryLight: "#ffffff",
    secondaryDark: "#c7c7c7",
    font: "#424242",
  },

  mixin: {
    center: () => {
      return `
            display:flex;
            justify-content:center;
            align-items:center;
        `;
    },
  },
};


```
