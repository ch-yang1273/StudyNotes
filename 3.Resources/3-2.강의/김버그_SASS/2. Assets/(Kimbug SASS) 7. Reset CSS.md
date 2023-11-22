---
created: 2023-11-07
---
키워드:: [[(KimBug SASS)]]

## 유명한 Reset 들

1. [CSS Tools: Reset CSS (meyerweb.com)](https://meyerweb.com/eric/tools/css/reset/)
2. [Normalize.css: Make browsers render all elements more consistently. (necolas.github.io)](https://necolas.github.io/normalize.css/)

## Reset CSS

강사는 nomalize.css를 기반으로 깔고, 자신만의 `_reset/scss`를 추가로 적용했다.

```scss
* {
  margin: 0;
  font-family: 'Noto Sans KR', sans-serif;
  box-sizing: border-box;
}

html {
  font-family: 'Noto Sans KR', sans-serif;
}

body {
  // 강사의 강박: *, html, body 셋 다 해야 잘 먹더라
  font-family: 'Noto Sans KR', sans-serif;
}

h1 {
  // _nomalize.scss에서 준 margin을 덮어야 함
  margin: 0;
}

a {
  color: inherit;
  text-decoration: none;
}

button,
input,
select,
textarea {
  background-color: transparent;
  border: 0;

  &:focus {
    outline: none;
    box-shadow: none;
  }
}

a,
button {
  cursor: pointer;
}

ul,
ol {
  padding-left: 0;
  list-style: none;
}
```