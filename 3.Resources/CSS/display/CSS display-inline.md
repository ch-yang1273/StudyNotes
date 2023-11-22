---
created: 2023-10-10
---
키워드:: [[CSS]] [[CSS display 속성]]

## inline

- inline은 기본적으로 흐름의 성질을 갖고 있습니다.
- 부모의 영역에 들어갈 공간이 없으면 다음 라인으로 줄바꿈 되어 들어간다.
- 텍스트나 작은 요소를 배치할 때 사용한다.

### 사용 불가 속성

실제 사용해보면, 사이즈가 늘어나서 시각적으로 사용되는 것으로 보인다. 사용 불가는 아니지만 영역으로 인정을 받지 못해 다른 요소들도 이 요소를 피하지 않는다. 버그와 같은 동작을 보여주니 사용하지 않는 것이 좋겠다.

inline의 흐름을 방해하는 다음과 같은 속성은 설정할 수 없다.

- inline은 width, height를 사용 불가
- 수직 속성인 padding-top/bottom, border-top/bottom, margin-top/bottom 불가