---
created: 2023-11-15
---
키워드:: [[(KimBug SASS)]]

#### Figma Grid 관련 단축키

- Show Layout Grids : Shift + G

## Grid

Flex는 한 방향의 1차원 레이아웃 시스템이고, Grid는 가로/세로 2차원 레이아웃 시스템이다.

Grid를 분석하려면 다음을 파악해야 한다.

- 몇 개의 Columns로 이루어졌는지
- Unit Size는?
- Gutter Size는?

### 용어

#### Unit, Gutter

사이즈는 px 혹은 %를 사용하고, 특히 모바일은 크기가 다양해서 %를 자주 사용한다

- 빨간 색 : Unit Size
- 파란 색 : Gutter Size

![[Pasted image 20231115004421.png]]

#### Column

반으로 쪼갠 Gutter Size가 Unit 양 옆에 붙은 영역

Bootstrap은 12 Columns를 사용한다.

![[Pasted image 20231115004502.png]]

#### margin

CSS 용어와 달리 디자인에서는 전체 Columns 양 옆에 비워두는 영역을 margin이라 하더라

![[Pasted image 20231115010256.png]]

### Grid 사용 방법

Gutter에는 요소를 두지 않는다.

요소가 4 Columns를 사용한다면 아래 그림처럼 Gutter를 양 옆에 두고 요소를 배치한다.

![[Pasted image 20231115005249.png]]