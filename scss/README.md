# SCSS

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
$red: #e1463a;
```

```scss
/* styles.scss */
@import '_variables';

body {
  background-color: $red;
}
```

## Nesting

상위 선택자의 반복을 피하고 좀 더 편리하게 복잡한 구조를 작성할 수 있습니다.
중첩 안에서 `&` 키워드는 상위(부모) 선택자를 참조하여 치환합니다.

- SCSS 코드

```scss
body {
  h2 {
    color: $red;
  }
  .box {
    &:hover {
      background-color: gray;
    }
    h2 {
      color: blue;
      font-size: $title;
    }
  }
  button {
    color: $red;
  }
}
```

- Compile to CSS

```css
body button,
body h2 {
  color: #e1463a;
}
body .box:hover {
  background-color: gray;
}
body .box h2 {
  color: #00f;
  font-size: 32px;
}
```

## Mixins

스타일 시트 전체에서 재사용 할 CSS 선언 그룹을 정의하는 기능입니다.
약간의 Mixin(믹스인)으로 다양한 스타일을 만들어낼 수 있습니다.

우선, Mixin은 두 가지만 기억하면 됩니다. 선언하기(@mixin)와 포함하기(@include) 입니다.

`@mixin` 지시어를 이용하여 스타일을 정의합니다. Mixin은 선택자를 포함 가능하고 상위(부모) 요소 참조(& 같은)도 할 수 있습니다.

선언된 Mixin을 사용(포함)하기 위해서는 @include를 사용합니다.

```scss
/* _mixins.scss */
@mixin link($color) {
  text-decoration: none;
  display: block;
  color: $color;
}
```

```scss
@import '_variables';
@import '_mixins';

a {
  margin-bottom: 10px;
  &:nth-child(odd) {
    @include link(blue);
  }

  &:nth-child(even) {
    @include link(red);
  }
}
```
