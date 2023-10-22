---
created: 2023-10-22
---
키워드:: [[FunnyCSS - Kimbug]]

# Float

![[imageFrom김버그CSS_float.png]]

Float: 붕 뜨다. 부유하다.

Float 속성은 박스를 일반적인 흐름에서 빼냅니다. 주로 **text 및 Inline 요소가 Float된 박스 주위를 감싸며 흐르게 할 때 사용**합니다.

Float은 텍스트 배치 용도이지만, 레이아웃 용으로도 사용합니다.

Float를 사용하면 부모가 이 요소를 무시해 사이즈가 줄어드는데, 이런 일이 발생하는 상황 자체가 원래 Float의 목적과 다르게 사용할 때인 것 같습니다. 그냥 고칠 생각하지 말고 다른 속성을 사용하는 것이 좋아 보입니다.

해결법 참고: [css의 clearfix 기능으로 float 문제점 해결하기 (tistory.com)](https://8urther.tistory.com/entry/css%EC%9D%98-clearfix-%EA%B8%B0%EB%8A%A5%EC%9C%BC%EB%A1%9C-float-%EB%AC%B8%EC%A0%9C%EC%A0%90-%ED%95%B4%EA%B2%B0%ED%95%98%EA%B8%B0)

## Float의 특징

1. display 속성이 Block으로 상승한다.
2. 부모와 형제 요소들이 Float 된 요소의 공간을 무시한다. (부모의 사이즈도 줄어듬)0
3. Float으로 띄워진 요소 자체도 부모를 인정하지 않는다.
    - Block: 가능한 한 부모 요소의 전체 width를 차지한다 (X)
    - Block: width를 선언한 경우, 남은 공간은 margin으로 채운다 (X)
4. Bloack 속성을 가진 다른 요소들은 이 Float된 요소를 무시하는데, 텍스트와 inline 속성을 갖는 요소들은 Float된 요소를 인지하고 피합니다.
