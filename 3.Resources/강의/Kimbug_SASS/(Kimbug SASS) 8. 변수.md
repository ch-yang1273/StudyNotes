---
created: 2023-11-07
---
키워드:: [[(KimBug SASS)]]

대문자로 쓰는 곳도 있고, 소문자로 쓰는 곳도 있고, CSS 쪽이니까 소문자에 BEM 규칙 적용해도 좋을 것 같다.

대충 블록 레벨 스코프로 생각하면 되겠다.

CSS에서 value로 사용하는 값은 모두 변수에 대입할 수 있다. 심지어 여러 값도 들어감

```scss
$val: 'Noto Sans KR', sans-serif;
$val-2: underline dotted;
```