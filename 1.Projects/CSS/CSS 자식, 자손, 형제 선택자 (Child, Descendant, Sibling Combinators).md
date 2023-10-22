---
created: 2023-10-08
---
키워드:: [[CSS]]

## 자식 선택자 (>)

특정 요소의 직접적인 자식만을 선택합니다.

```html
<div>
  <p>이 텍스트는 녹색입니다.</p>
  <span>
    <p>이 텍스트는 녹색이 아닙니다.</p>
  </span>
</div>
```

```css
div > p {
  color: green;
}
```

## 자손 선택자 ( )

특정 요소의 모든 하위 요소를 선택합니다. ' '(공백)을 사용합니다.

```html
<div>
  <p>이 텍스트는 빨간색입니다.</p>
  <span>
    <p>이 텍스트도 빨간색입니다.</p>
  </span>
</div>
```

```css
div p {
  color: red;
}
```

## 형제 선택자 (~, +)

- `+`: 바로 다음의 형제만
- `~`: 다음의 모든 형제들

```html
<ol>
  <li>첫 번째 아이템</li>
  <li class="selector">두 번째 아이템</li>
  <li>세 번째 아이템</li>
  <li>네 번째 아이템</li>
  <li>다섯 번째 아이템</li>
</ol>
```

```css
/* + 선택자: 두 번째 .selector 바로 다음의 형제 li만 선택합니다. */
.selector + li {
  color: blue;
}

/* ~ 선택자: 두 번째 .selector 다음의 모든 형제 li를 선택합니다. */
.selector ~ li {
  font-weight: bold;
}
```