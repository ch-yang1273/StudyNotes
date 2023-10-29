---
created: 2023-10-07
---
키워드:: [[모던 자바스크립트 DeepDive]]

# 자바스크립트 개발 환경과 실행 방법

브라우저와 Node.js는 용도가 다르다.

## 브라우저

- 렌더링이 주된 목적
- 파싱된 HTML을 선택/조작하는 `DOM API`를 기본적으로 제공
- 보안상의 이유로 `파일 시스템 API`는 제공하지 않는다.

## Node.js

- 브라우저 외부에서 JavaScript 실행 환경을 제공

### npm (Node Package Manager)

자바스크립트 패키지 매니저

### Node.js REPL (Read Eval Print Loop)

- 자바스크립트를 입력하면 즉시 결과를 출력하는 대화식 환경
- node 명령어로 REPL 환경에 접근할 수 있다.