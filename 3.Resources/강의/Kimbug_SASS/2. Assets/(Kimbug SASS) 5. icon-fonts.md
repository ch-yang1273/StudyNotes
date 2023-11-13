---
created: 2023-11-06
---
키워드:: [[(KimBug SASS)]]

## 다운로드 한 icon svg 파일을 적용하는 방법

1. `<img>` 태그 사용

    ```html
    <img src='#' alt='icon-bell'>
    ```

2. CSS background-image
3. svg의 파일 내용 그대로 복사
    ```html
    <svg width="24" height="25" viewBox="0 0 24 25" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path fill-rule="evenodd" clip-rule="evenodd" d="M10.139 ... fill="black"/>
    </svg>
    ```
    - fill 값을 "currentColor"로 바꾸면  부모의 color를 따라간다.
    - transition 같은 속성도 줄 수 있다.
    - (단점) 코드도 더럽고 줄도 길다. (React나 Vue 등 Front Framework 쓰면 큰 문제 아님)
4. Icon font 사용

## Icon font를 만들어 봅시다

1. icomoon 사이트에서 "import icons"하고 대상 svg 파일 선택
2. select all
3. generate font
4. 대문자들 다 소문자로 변경 (class명이 되는데 html에서 대문자 안좋아함)
5. 다운로드 전 설정 표시 클릭
    1. Font name: tomorrow
    2. prefic: ic-
    3. css selector: "Use I (for selecting i)" 체크
6. 다운로드
7. zip 파일 내 fonts 폴더 안의 파일들을 `assets/fonts/`로 copy
8. zip 파일 내 style.css 내용을 `style/base/_fonts.scss` 에 copy
    1. 내용보면 url() 있는데 이 안의 내용만 './assets/fonts/~'가 되도록 수정 (생성 될 main.css 위치 기준임)
    2. url() 안에 ?...#~ 부분에 해시값 있는데 ... 내용은 지워도 됨

## @import

package.json에는 `"sass": "node-sass -wr styles/main.scss ./style.css"` 만 있어 main.scss만 알고 있습니다.

- maint.scss에 @import를 해줍니다.
- 파일이름은 `./base/_fonts.scss`지만 `fonts`로 깔쌈하게 적습니다.

```scss
@import './base/fonts';
```

## 사용

사이즈 조절도 `font-size: 30px`로 할 수 있습니다.

```html
<i class="ic-community"></i>
<i class="ic-bookmark"></i>
```