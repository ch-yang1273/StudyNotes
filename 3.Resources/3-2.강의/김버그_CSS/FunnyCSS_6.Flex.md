---
created: 2023-10-24
---
키워드:: [[FunnyCSS - Kimbug]]

## Flex box 적용 순서

1. Flex box 설정
2. 가로 정렬이야? 세로 정렬이야?
3. 무조건 한 줄에 정렬?
4. flex box 정렬

@ flex box에서 **order**를 사용하면, 마크업 순서에 상관없이 순서를 할당할 수 있다.

## 1. Flex Box 설정

기본적으로 flex는 box와 같고, inline-flex는 inline과 같다.

```css
display: flex;
```

### 누구에게 적용해야지?

정렬 대상의 부모에게 적용을 한다.

## 2. flex-direction

row, row-reverse, column, column-reverse

### flex-direction 설정에 따른 Axis (축)

- **main axis**: flex-direction 방향에 따르는 축
- **cross axis**: flex-direction 방향에 수직으로 생기는 축

```css
/* Example */
flex-direction: row;
/**
 * main axis = 가로 방향
 * cross axis = 세로 방향
 */
```

## 3. flex-wrap

- nowrap: 무조건 한 줄에 정렬. 자식의 사이즈도 강제로 줄인다 (default)
- wrap: 공간이 모자라면 다음 줄에 정렬

## 4. 정렬

float는 left 아니면 right인데, flex는 선택지가 많다.

- main axis 기준 정렬: **justify-content**
- cross axis 기준 정렬: **align-items**, **align-content**

cross axis 기준 정렬은 두 가지가 있는데 기본적으로 `align-items` 쓰고 문제가 있을 때 `align-content`를 쓰면 된다.

### justify-content

flex-start, flex-end, center, space-between, space-around, space-evenly

### align-items

flex-start, flex-end, center, ~~space-between~~, ~~space-around~~, ~~space-evenly~~

- wrap이 적용 되어 새로운 줄이 생겼을 때, **각 줄 마다 정렬 라인 기준**이 생겨 cross-axis 요소 간의 간격 설정은 적용되지 않는다.

![[imageFrom김버그CSS_alignItems.png|200]]

### align-content

flex-start, flex-end, center, space-between, space-around, space-evenly

wrap이 적용 되어 새로운 줄이 생기더라도, **전체를 기준으로 cross-axis 정렬**을 한다. 이 경우에는 cross-axis 요소 간 간격 설정도 적용이 된다.

![[imageFrom김버그CSS_alignContent.png|200]]