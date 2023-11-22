---
created: 2023-10-10
---
키워드:: [[CSS]]

## box-sizing

box-siing은 CSS에서 box model을 어떻게 계산할지 결정하는 속성입니다. 기본값은 content-box이지만, **주로 border-box를 사용**합니다.

- content-box: 너비(witdh)와 높이(height)가 content의 영역만을 포함합니다. padding과 border는 너비와 높이에 추가로 더해집니다.
- border-box: 너비와 높이는 content, padding, border까지 포함합니다. content의 사이즈는 `너비 - border - padding` 값이 계산된 값을 사이즈로 갖습니다.