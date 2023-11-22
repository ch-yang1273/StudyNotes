---
created: 2023-11-14
---
키워드:: [[(KimBug SASS)]]

폰트 size, weight는 잘 지키는데, Line Hight와 Letter Spacing을 잘 안 지키면 텍스트가 많이 구려진다.

폰트 size, weight에 맞는 Line Hight와 Letter Spacing를 세트로 봐야 한다.

강의에서도 font size 별로 constants를 설정했다.

![[Pasted image 20231114052542.png]]

```sass
$font-main: 'Noto Sans KR', sans-serif;
$font-price: 'Tahoma', sans-serif; // 가격과 %에만 사용하더라

// font size에 맞춰 constants를 설정했다.
$font-size-12: 12px;
$line-height-12: 16px;
$letter-spacing-12: -0.005em;

$font-size-13: 13px;
$line-height-13: 20px;
$letter-spacing-13: -0.01em;

$font-size-14: 14px;
$line-height-14: 24px;
$letter-spacing-14: -0.01em;

$font-size-16: 16px;
$line-height-16: 24px;
$letter-spacing-16: -0.01em;

$font-size-18: 18px;
$line-height-18: 28px;
$letter-spacing-18: -0.02em;

$font-size-24: 24px;
$line-height-24: 34px;
$letter-spacing-24: -0.01em;
```

## 적용

`_reset.scss`에 적용해줬다.

```scss
* {
  margin: 0;
  font-family: $font-main;
  box-sizing: border-box;
  // font smoothing 검색하면 모질라에 나온다.
  // font가 부드러워 진다 함.
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

h_tml {
  font-family: $font-main;
  font-size: $font-size-16;
}

body {
  font-family: $font-main;
  color: $primary;
}
```