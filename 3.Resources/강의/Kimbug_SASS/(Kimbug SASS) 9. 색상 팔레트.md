---
created: 2023-11-14
---
키워드:: [[(KimBug SASS)]]

작업 전 사용할 색상을 설계하고 시작한다.

## @import

상수 선언한다고 CSS가 바뀌지 않으니 최상단에 @import 한다.

```sass
@import './constants/colors';

@import './base/fonts';
@import './base/normalize';
@import './base/reset';
```

## 색상 팔레트

### gray naming 

#### 방법 1

색상 앞자리를 추출. 색상이 바뀌면 낭패. 겹쳐도 낭패

```sass
$black: #000000;
$gray-1: #191a20;
$gray-3: #3f4150;
$gray-8: #8c8d96;
$$gray-b: #b2b3b9;
$gray-e: #e0e2e7;
$gray-f: #f7f8fa;
$white: #ffffff;

$blue: #3da5f5;
$blue-dark: #ecf6fe;
$blue-light: #3186c4;

$red: #f86d7d;
$green: #22c58b;
```

#### 방법 2

디자인 시안에서 해당 색상이 사용되는 용도를 파악. 피그마에서 색상 검색된다.
gray 색상의 용도를 분석했다.

"tertiary"는 잘 몰라서 기억 못하겠다. 그냥 "third"로 해도 되겠다.

```sass
$black: #000000;
$dark: #191a20; // 중요한 정보
$primary: #3f4150; // 대부분의 글자 색상
$secondary: #8c8d96; // 덜 중요한 글자 색상
$tertiary: #b2b3b9; // 검색 창의 "검색" 같은 희미한 글자 색상
$border: #e0e2e7; // 2. 흰색 두 번째로 밝은 색은 대부분 border에 쓰이더라
$background: #f7f8fa; // 1. 흰색보다 첫 번째로 밝은 색은 대부분 배경에 쓰이더라
$white: #ffffff;
```