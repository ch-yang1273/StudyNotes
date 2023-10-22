---
created: 2023-10-08
---
키워드:: [[CSS]]

Pseudo : 가짜, 가상

## :first-child, :last-child, :nth-child(N)

':'를 공백 없이 붙여서 사용한다. `:nth-child(N)` 의 N에는 숫자도 들어가지만, even (짝수 번째), odd (홀수 번째)도 들어간다. (even 대신 2n, odd 대신 2n-1 가능)

```html
<ol>
  <li>첫 번째 아이템</li>
  <li>두 번째 아이템</li>
  <li>세 번째 아이템</li>
  <li>네 번째 아이템</li>
  <li>다섯 번째 아이템</li>
</ol>
```

```css
/* :first-child 선택자: 첫 번째 li 요소를 선택합니다. */
li:first-child {
  color: red;
}

/* :last-child 선택자: 마지막 li 요소를 선택합니다. */
li:last-child {
  color: blue;
}

/* :nth-child() 선택자: n번째 li 요소를 선택합니다. */
li:nth-child(odd) {
  background-color: lightgray;
}

/* :nth-last-child() 선택자: 뒤에서부터 n번째 li 요소를 선택합니다. */
li:nth-last-child(2) {
  text-decoration: underline;
}

```