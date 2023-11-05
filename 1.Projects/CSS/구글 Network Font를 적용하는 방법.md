---
created: 2023-11-05
---
키워드:: [[CSS]]

## 구글 폰트

URL : [font.google.com](font.google.com)

1. 사용할 font weight를 확인하고, 사이트에서 선택한다.
2. 생성된 `<link>`를 복사해서 HTML 의 **Stylesheet `<link>` 위에** 붙여 넣는다.
3. 개발자 모드에서 `Rendered Fonts`를 확인한다.

### 생성된 HTML 링크 예시

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@400;500;700&display=swap" rel="stylesheet">
```

### CSS 적용 예시

```css
* {
  font-family: 'Noto Sans KR', sans-serif;
}
```