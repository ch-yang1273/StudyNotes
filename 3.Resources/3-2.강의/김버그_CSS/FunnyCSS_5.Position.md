---
created: 2023-10-23
---
키워드:: [[FunnyCSS - Kimbug]]

MDN: [position - CSS: Cascading Style Sheets | MDN (mozilla.org)](https://developer.mozilla.org/ko/docs/Web/CSS/position)

# Position

**문서 상에서 요소를 배치하는 방법을 지정**합니다.

아래 각 Position Type에 따라, 기준점이 무엇인지 잘 생각해야 합니다.

`top, bottom, right, left` 속성이 요소를 최종 배치할 위치를 결정합니다. 적용 시 `top, bottom` 중 하나를 사용하고, `right, left`도 둘 중 하나만 사용합니다.

static을 제외하고는 float 처럼 자기 원래 위치로 부터 띄우는 현상이 있는데, 이 높이 순서를 정해야 하는데 이 때 `z-index`를 사용합니다.

![[imageFrom김버그CSS_z-index.png]]

```css
position: static;
```

## static

요소를 일반적인 문서 흐름에 따라 배치합니다. `top, bottom, right, left` 속성이 아무런 영향을 주지 안습니다. 모든 태그의 기본 값입니다.

## relative

요소를 원래 있던 자리를 기준으로 `top, bottom, right, left` 값에 따라 오프셋을 적용합니다. 이 오프셋은 다른 요소에 영향을 주지 않고, 레이아웃에서 이 **요소가 차지하는 공간은 "static" 일 때와 같습니다.**

기준점: **원래 자기 위치** (static)

## absolute

**요소를 문서 흐름에서 제거**하고, 페이지 레이아웃에도 공간을 배정하지 않습니다.

Float과 과 같이 display 속성이 block으로 변합니다. 하지만 Float과 다르게 텍스트나 inline 요소들도 이 absolute 타입의 요소를 피하지 않습니다.

기준 점을 잡아야 한다면 만만한 `relative`를 사용하면 좋습니다.

기준점: **부모, 조상 요소 중 Position type이 Static이 아닌 요소**

## fixed

**absolute를 적용했을 때와 동일하게 요소를 문서 흐름에서 제거**하고, 페이지 레이아웃에도 공간을 배정하지 않습니다.

하지만 이 fixed의 기준점은 viewport(브라우저 창의 전체 크기) 를 기준으로 합니다.

기준점: **viewport(브라우저 창의 전체 크기)**