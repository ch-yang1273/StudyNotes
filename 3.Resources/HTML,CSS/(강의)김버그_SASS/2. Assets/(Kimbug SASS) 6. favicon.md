---
created: 2023-11-07
---
키워드:: [[(KimBug SASS)]]

## SVG 파일로 부터 favicon 생성

1. svg 파일 다운로드
2. [realfavicongenerator.net](https://realfavicongenerator.net/) 접속 후 svg 업로드. 사이즈가 크다 해도 그냥 진행하면 됨
3. 하라는 대로 package 다운 받아서 root에 두고, html `<head>`의 title 밑에 code도 붙여 넣으면 끝
4. 별거 없다

```html
<link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png" />
<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png" />
<link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png" />
<link rel="manifest" href="/site.webmanifest" />
<link rel="mask-icon" href="/safari-pinned-tab.svg" color="#3da5f5" />
<meta name="msapplication-TileColor" content="#2b5797" />
<meta name="theme-color" content="#ffffff" />
```

![[Pasted image 20231107014653.png]]