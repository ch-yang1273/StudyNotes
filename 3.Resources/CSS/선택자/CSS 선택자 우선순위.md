---
created: 2023-10-09
---
키워드:: [[CSS]]

## 선택자의 우선 순위

- 같은 우선 순위라면 후에 있는 것이 설정을 덮어쓴다.
- **id > class > type 순으로 우선 순위**가 강하다.
- 같은 우선 순위라면 개수가 많은 쪽이 우선
- 인라인 스타일이 더 강력
- CSS 파일에 !important 쓰는 것이 더 강력

```html
<div id="box" class="shape round">
  <p>안녕하세요</p>
</div>
```

```css
/* 타입 선택자 */
div {
  color: blue;
}

/* 클래스 선택자 */
.shape {
  color: green;
}

/* ID 선택자 */
#box {
  color: red;
}

/* 인라인 스타일 (HTML에 직접 적용) */
<!-- <div id="box" class="shape round" style="color: yellow;"> -->

/* !important */
.shape {
  color: pink !important;
}
```