---
layout: post
title: "Styled-Components에 스타일린트(stylelint) 적용하기"
categories: TIL Style-Components Style
tag: lint
---

# 들어가기

- sass는 lint를 사용해서 통일된 스타일 코드를 유지할 수 있는데, Styled-Components에서는 방법이 없나?
- 라는 생각이 들어서 찾아보던 중 공식 사이트에서 'stylelint'를 발견!
- 그래서 정리합니다. `stylelint 적용하기`

# 설치

1. `stylelint` 설치하기

   ```
   (npm install --save-dev \
   stylelint \
   stylelint-processor-styled-components \
   stylelint-config-styled-components \
   stylelint-config-recommended)
   ```

2. `.stylelintrc` 파일을 루트에 추가하기

   ```
    {
        "processors": [
            "stylelint-processor-styled-components"
        ],
        "extends": [
            "stylelint-config-recommended",
            "stylelint-config-styled-components"
        ]
    }
   ```

3. `package.json` 파일에 stylelint 설정
   ```
   {
       "scripts": {
           "lint:css":"stylelint './src/**/*.js'"
       }
   }
   ```

# 실행

- `npm run lint:css` 를 입력해서 실행할 수 있음
- 또한 VSCode에서 `stylelint` 익스텐션을 설치하면 VSCode 자체에서 확인해 줌.

# Reference

- https://styled-components.com/docs/tooling#stylelint
- https://flamingotiger.github.io/style/styled-components-lint/
