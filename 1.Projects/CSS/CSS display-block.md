---
created: 2023-10-10
---
키워드:: [[CSS]] [[CSS display 속성]]

## block

- 기본적으로 길막하는 성질을 갖고 있습니다.
- 새로운 줄에서 시작합니다.
- 가능한 한 부모 요소의 전체 너비(width)를 차지합니다.
- 별도의 width를 선언한 경우, 남은 공간은 margin으로 채웁니다.

### margin: 0 auto;

auto 속성을 사용하면, 위에서 설명한 남은 공간을 margin으로 채우는 방식을 설정합다.

```css
// 남은 공간 margin을 왼쪽에 몰빵합니다.결국 box는 오른쪽 정렬이 됩니다.
margin-left: auto;

// 남은 공간 margin을 오른쪽에 몰빵합니다.결국 box는 왼쪽 정렬이 됩니다.
margin-right: auto;

// 양쪽 공평하게 margin을 배분합니다. 위 설정 두개 써도 똑같습니다.
margin:0 auto;
//margin-left: auto;
//margin-right: auto;
```

### block의 height

- 부모 요소의 height를 따로 설정하지 않은 경우, 자식 요소의 height 합 = 부모 요소의 height
- 부모 요소의 사이즈를 설정했는데, 자식 요소가 더 크다면?
- 자식 요소의 사이즈가 없으면 0px인가?
