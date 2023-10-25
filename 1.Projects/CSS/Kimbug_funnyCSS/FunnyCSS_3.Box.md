---
created: 2023-10-08
---
키워드:: [[FunnyCSS - Kimbug]]

## Box Model

![[20231010_CSS_Box_Model.png]]

### Box Size 속기형

- 기본 순서로는 시계방향을 생각하면 된다.
- Top-Bottom, Left-Right 는 세트이다. 하나가 설정되지 않았으면 세트를 따라간다.

```css
// 전체 1px
margin: 1px;

// 탑, 라이트, 바텀, 레프트
margin: 1px 2px 3px 4px;

// Top-Bottom 1px, Left-Right 2px
padding: 1px 2px;

// Top 1px, Bottom 2px, Left-Right 3px
padding: 1px 3px 2px;
```

## box-sizing 속성

![[CSS box-sizing 속성]]

## box type

### display: block;

![[CSS display-block]]