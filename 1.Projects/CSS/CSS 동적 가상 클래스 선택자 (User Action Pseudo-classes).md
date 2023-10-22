---
created: 2023-10-08
---
키워드:: [[CSS]]

## :hover, :active, :focus, :not(:~)

```html
<button id="my-button">버튼</button>
<a href="#" id="my-link">링크</a>
<input type="text" id="my-input">
```

```css
/* :hover 선택자: 요소 위로 마우스를 올렸을 때 */
#my-button:hover {
  background-color: yellow;
}

/* :active 선택자: 요소를 클릭하고 있는 동안 */
#my-button:active {
  background-color: green;
}

/* :focus 선택자: 요소가 포커스를 받았을 때 (예: 입력 필드를 클릭했을 때) */
#my-input:focus {
  border: 2px solid blue;
}

/* :not 선택자를 사용한 예시. :hover가 아닌 상태 */
#my-link:not(:hover) {
  color: grey;
}
```

## 이 외의 선택자

| 가상 클래스 선택자 | 설명                                                     |
|--------------------|----------------------------------------------------------|
| `:hover`           | 요소 위로 마우스를 올렸을 때 적용됩니다.                 |
| `:active`          | 요소를 클릭하고 있는 동안 적용됩니다.                    |
| `:focus`           | 요소가 포커스를 받았을 때 적용됩니다.                    |
| `:not(:hover)`     | `:hover` 상태가 아닌 경우에 적용됩니다.                  |
| `:visited`         | 이미 방문한 하이퍼링크에 적용됩니다.                     |
| `:target`          | URL의 앵커 식별자와 일치하는 요소에 적용됩니다.           |
| `:not(selector)`   | 주어진 서브 선택자와 일치하지 않는 요소를 선택합니다.    |
| `:disabled`        | 비활성화된 폼 컨트롤에 적용됩니다.                       |
| `:enabled`         | 활성화된 폼 컨트롤에 적용됩니다.                         |
| `:checked`         | 체크박스나 라디오 버튼이 체크됐을 때 적용됩니다.          |
| `:required`        | `required` 속성을 가진 폼 요소에 적용됩니다.             |
| `:optional`        | `required` 속성을 가지지 않은 폼 요소에 적용됩니다.      |
| `:valid`           | 폼 요소의 값이 유효할 경우 적용됩니다.                   |
| `:invalid`         | 폼 요소의 값이 유효하지 않을 경우 적용됩니다.            |

### 폼 요소의 유효?

```html
<!-- 이메일 형식을 만족해야 유효한 상태가 됨 -->
<input type="email" required>
```

```css
/* 유효한 상태일 때 */
input:valid {
  border: 1px solid green;
}

/* 유효하지 않은 상태일 때 */
input:invalid {
  border: 1px solid red;
}
```