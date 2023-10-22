---
created: 2023-10-17
---
키워드:: [[모던 자바스크립트 DeepDive]]

## 그래서 비동기 처리에 왜 프로미스를 사용하려는 거야?

### 기존 콜백 함수 등록 방식의 문제점

- 결과 값을 return 받을 수 없다. -> [[콜백 헬]] #todo/콜백헬정리
- 에러 처리가 어렵다.

```javascript
const get = url => {
	const xhr = new XMLHttpRequest() 
  xhr.open('GET', url)
  xhr.send()
  
  xhr.onload = () => {
    if (xhr.status === 200) {
      return JSON.parse(xhr.response)
    }
    console.error(`${xhr.status} ${xhr.statusText}`)
  }
}

const response = get('https://jsonplaceholder.typicode.com/posts/1')
console.log(response) // undefined
```

위의 get() 함수는 다음의 작업을 하는 함수이다.

- url 경로로 GET 요청을 보낸다.
- 응답이 오면 반응할 **콜백 함수를 등록**한다.

get() 함수는 반환을 하더라도 콜백 등록에 대한 return을 하지, GET 요청의 응답에 대한 처리 결과를 내주지 않는다. `onload`에 등록한 콜백 함수의 return은 캐치할 수 없다.

## 프로미스

### 형태

- `resolve`와 `reject`를 인수로 갖는 `executor 함수`를 인수로 받는다.
- 받은 `executor 함수`는 바로 실행된다.

#### 예시

```javascript
console.log("Promise 생성 전");

let p = new Promise(function(resolve, reject) {
  console.log("Promise 내부");
  setTimeout(function() {
    resolve("완료");
  }, 2000);
});

console.log("Promise 생성 후");

/**
 * 1. "Promise 생성 전"
 * 2. "Promise 내부"
 * 3. "Promise 생성 후"
 * 4. 2초 후에 `resolve("완료")`
 */
```

- 정상 처리되었을 때는 `resolve`를 호출하고
- 비정상 처리되었을 때는 `reject`를 호출하면 된다.

### Promise Status (프로미스 상태 정보)

- pending: 프로미스가 생성된 직후 기본 상태 (result=undefined)
- fulfilled: resolve 함수가 호출 된 상태 (result=`resolve 함수에 전달한 인자`)
- rejected: reject 함수가 호출 된 상태 (result=`resolve 함수에 전달한 인자`)

### 프로미스 후속 처리 메서드

다음 나오는 후속 처리 메서드들은 콜백 함수를 등록한다.

#### then

then 메서드에는 비동기 수행 결과로 resolve/reject 가 불렸을 때 호출 될 콜백 함수를 등록할 수 있습니다.

then 메서드의 두 번째 실패 처리 콜백은 첫 번째 콜백 함수에서 발생한 에러를 캐치할 수 없고, 가독성도 좋지 않아 잘 사용하지 않습니다.

실패 처리는 다음의 catch를 사용합시다.

```javascript
const p = new Promise(~);

p.then(성공 처리 콜백, 실패 처리 콜백);

// 예시
const p = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("성공");
  }, 1000);
});

p.then(
  (message) => {
    console.log("성공 메시지: " + message);
  },
  (error) => {
    console.log("실패 메시지: " + error);
  }
);

// 출력: "성공 메시지: 성공"
```

#### catch

catch 프로미스에서 reject가 불렸을 때 호출 될 콜백 함수만 등록합니다.

```javascript
const p = new Promise((resolve, reject) => {
  setTimeout(() => {
    reject("실패");
  }, 1000);
});

p.catch((error) => {
  console.log("실패 메시지: " + error);
});

// 예시 출력: "실패 메시지: 실패"
```

#### finally

finally에는 resolve/reject 가 불렸을 때 공통으로 호출 될 콜백 함수를 등록합니다.

```javascript
const p = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("성공");
  }, 1000);
});

p.finally(() => {
  console.log("항상 실행");
});

// 예시 출력: "항상 실행"
```

### 장점

1. 가독성
2. 체이닝: `then` 메서드를 체인으로 연결 할 수 있음
3. 에러 처리: `catch` 메서드를 사용해 중앙화 된 오류 처리가 가능 

### 단점

여전히 가독성이 좋지 않은 콜백 패턴을 사용하고 있다. ES8에서 도입 된 `async/await`를 더 알아 봅시다. 

### 프로미스의 정적 메서드

Promise.resolve, Promise.reject, Promise.all, Promise.race, Promise.allSettled는 용도가 보이면 공부해야겠다.

### 마이크로태스크 큐

#todo/실행컨텍스트 : 실행 컨텍스트 공부할 때 같이 공부하면서 정리합시다.

## fetch

fetch 함수 HTTP 요청 전송 기능을 제공하는 클라이언트 사이드 Web API입니다. fetch 함수는 XMLHttpRequest 객체보다 사용법이 간단하고 프로미스도 지원합니다.

### XMLHttpRequest을 사용한 예제

```javascript
console.log("XMLHttpRequest with Promise 예제 시작");

function fetchTodo() {
  return new Promise(function(resolve, reject) {
    var xhr = new XMLHttpRequest();
    xhr.open("GET", "https://jsonplaceholder.typicode.com/todos/1", true);

    xhr.onreadystatechange = function() {
      if (xhr.readyState === 4) {
        if (xhr.status === 200) {
          resolve("응답 받음: " + xhr.responseText);
        } else {
          reject("에러 발생: " + xhr.status);
        }
      }
    };

    xhr.send();
  });
}

fetchTodo()
  .then(function(response) {
    console.log(response);
  })
  .catch(function(error) {
    console.log(error);
  });

console.log("XMLHttpRequest with Promise 예제 끝");

/**
 * 1. "XMLHttpRequest with Promise 예제 시작"
 * 2. "XMLHttpRequest with Promise 예제 끝"
 * 3. "응답 받음: ..." (서버로부터 응답이 올 때 출력됩니다.) 
 * 또는 "에러 발생: ..." (에러가 발생할 경우)
 */
```

### fetch를 사용한 예제

```javascript
console.log("fetch 예제 시작");

fetch("https://jsonplaceholder.typicode.com/todos/1")
  .then((response) => response.json())  // 응답을 JSON 형태로 파싱
  .then((data) => {
    console.log("성공: ", data);
  })
  .catch((error) => {
    console.log("실패: ", error);
  })
  .finally(() => {
    console.log("항상 실행");
  });

console.log("fetch 예제 끝");
/**
 * 1. "fetch 예제 시작"
 * 2. "fetch 예제 끝"
 * 3. "성공: ..." (서버로부터 응답이 올 때 출력됩니다.)
 * 4. "항상 실행" (성공이든 실패든 실행됩니다.)
 */
```

#### response.json() 주의!

참고: ([Fetch API 사용하기 - Web API | MDN (mozilla.org)](https://developer.mozilla.org/ko/docs/Web/API/Fetch_API/Using_Fetch))

`.then((response) => response.json())` 으로 나눈 이유가 있습니다.

이 **`json()`은 비동기적으로 동작하며, 응답 본문을 JSON으로 파싱하여 반환하는 Promise를 생성**합니다. `json()`은 파싱한 json을 resolve로 return 합니다.

동기적으로 작동하는 `JSON.parse()`과 차이점을 잘 알고 사용합시다.

#### response.json() VS JSON.parse()

모두 JSON 형식의 문자열을 자바스크립트 객체로 변환하는 작업을 수행합니다.

`JSON.parse()`는 동기적인 API로 이미 받아온 JSON 문자열을 파싱할 때 사용하고, `response.json()`은 비동기 네트워크 요청의 결과를 JSON으로 파싱할 때 사용합니다.

##### JSON.parse()

1. **동기적 작동**: `JSON.parse()`는 동기적으로 작동합니다. 즉, 함수를 호출하면 즉시 결과를 반환합니다.
2. **문자열 입력**: `JSON.parse()`는 JSON 형식의 문자열을 인자로 받습니다.
3. **에러 처리**: 문법적으로 잘못된 JSON 문자열을 파싱하려고 시도하면 예외가 발생합니다. 따라서 `try-catch` 블록을 사용해야 할 수도 있습니다.

##### response.json()

1. **비동기적 작동**: `response.json()`은 비동기적으로 작동하며, 프로미스를 반환합니다. 즉, 작업이 완료되면 `then`이나 `async/await`를 사용하여 결과를 얻을 수 있습니다.
2. **응답 객체 입력**: `fetch`나 `XMLHttpRequest`와 같은 API로부터 얻은 응답(Response) 객체에 대해 호출합니다.
3. **에러 처리**: `response.json()`도 잘못된 JSON 데이터에 대해 실패하는 프로미스를 반환하므로, `catch` 블록을 사용하여 에러를 처리할 수 있습니다.