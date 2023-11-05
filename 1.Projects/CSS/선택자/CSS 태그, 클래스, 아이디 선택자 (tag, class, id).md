---
created: 2023-10-08
---
키워드:: [[CSS]]

## 태그 선택자 (없이)

```html
<p>이 텍스트는 파란색입니다.</p>
```

```css
p { 
  color: blue;
}
```

## 클래스 선택자 (.)

```html
<span class="my-class">이 텍스트는 굵게 표시됩니다.</span>
```

```css
.my-class {
  font-weight: bold;
}
```

## 아이디 선택자 (#)

```html
<div id="my-id">이 텍스트의 글꼴 크기는 24px입니다.</div>
```

```css
#my-id {
  font-size: 24px;
}
```

## 복합 선택자

태그 선택자는 뒤로 못 오기는 하겠네?

```css
#my-id.my-class {
  font-size: 24px;
}
```