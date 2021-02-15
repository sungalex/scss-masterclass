# SCSS

- [ ] Variables
- [ ] Nesting
- [ ] Mixins
- [ ] Extend
- [ ] Responsive Mixins

## SCSS Set up

SCSS를 컴파일(CSS로 변환) 하는 다양한 방법이 있지만, 여기서는 gulp를 이용 합니다. Gulp는 node.js 패키지 입니다.

nomadcoders(https://github.com/nomadcoders/scss-masterclass) 에서 모든 파일을 다운로드 합니다.
`.babelrc`, `gulpfile.babel.js`, `package.json` 파일만 다운로드 해도 됩니다.

콘솔에서 `npm install` 또는 `yarn` 명령을 실행하여 필요한 패키지를 자동 설치 합니다.

`gulpfile.babel.js` 파일에는 `src/scss` 폴더의 모든 scss 파일의 변동사항을 watching 하고 있다가 변경이 발생하면 css 파일로 컴파일한 결과를 `dist/css` 폴더에 생성하도록 설정되어 있습니다.

콘솔에서 `npm run dev` 또는 `yarn dev` 명령을 실행하여 gulp가 동작하는 상태에서 SCSS 코드를 수정하면 변경한 내용이 index.html에 바로 적용 됩니다.

## Variables

웹사이트에서 사용할 colors, styles 등의 속성을 저장하기 위해 사용 합니다.

`src/scss` 폴더에 `_variables.scss` 파일을 생성 합니다. 파일명은 다른 명칭으로 지정해도 됩니다.
SCSS 파일명이 "\_"(언더스코어)로 시작하면 이 파일은 다른 SCSS 파일에서 참조는 하지만, CSS 파일로 변환하거나 컴파일 하지 않는 파일을 의미 합니다.

`_variables.scss` 파일에 아래와 같이 `$`로 시작하는 변수명과 속성을 지정하고, 다른 SCSS 파일에서 import 하여 사용하면 됩니다.

```scss
/* _variables.scss */
$bg: #e1463a; /* red */
```

```scss
/* styles.scss */
@import '_variables';

body {
  background-color: $bg;
}
```
