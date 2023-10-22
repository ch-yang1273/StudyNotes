---
created: 2023-10-04
---
키워드:: [[자바스크립트]]

# 자바스크립트 typeof 연산자

## typeof 연산자의 반환 값

typeof 연산자는 피연산자의 데이터 타입을 __7가지 문자열__ 로 반환한다.

'string', 'number', 'boolean', 'undefined', 'symbol', 'object', 'function'

### 'typeof null' 의 반환 값

- 'null'을 반환하는 경우는 없고, 'object'를 반환한다.
- 이는 자바스크립트 초기 버그지만 기존 코드에 영향을 줄 수 있어 수정되지 못하고 있다.
- null 타입을 확인할 때는 typeof 연산자를 사용하지 말고 일치 연산자를 사용하자

```javascript
var foo = null;
typeof foo === null; // false
foo === null;  // true
```

