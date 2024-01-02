---
created: 2023-10-10
---
키워드:: [[CSS]]

## box-sizing

box-sizing은 CSS에서 box model을 어떻게 계산할지 결정하는 속성입니다. 

### content-box (default)

```css
.content-box-example {
  box-sizing: content-box; /* 기본값이지만 명시적으로 설정 */
  width: 300px; /* 콘텐츠 영역만 300px */
  padding: 20px; /* 패딩 추가 */
  border: 5px solid black; /* 보더 추가 */
}
```

- witdh와 height가 **content의 영역만** 포함합니다.
- padding과 border는 너비와 높이에 추가로 더해집니다.

### border-box (대부분의 개발자가 선호)

```css
.border-box-example {
  box-sizing: border-box;
  width: 300px; /* 전체 박스 크기는 300px */
  padding: 20px; /* 패딩 포함 */
  border: 5px solid black; /* 보더 포함 */
}
```

- witdh와 height가 **content, padding, border까지 포함**합니다.
- 컨텐츠 사이즈 계산 : `content = width - border - padding`
- 직관적이어서 대부분의 개발자가 선호합니다.