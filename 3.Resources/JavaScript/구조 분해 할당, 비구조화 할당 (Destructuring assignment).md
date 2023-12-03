---
created: 2023-12-04
---
키워드:: [[자바스크립트]]

참고 : [구조 분해 할당 - JavaScript | MDN (mozilla.org)](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)

# 구조 분해 할당

배열이나 객체의 속성을 해체하여 그 값을 개별 변수에 담을 수 있게 하는 JavaScript 표현식

## 배열 구조 분해

```js
var foo = ["one", "two", "three"];

var [red, yellow, green] = foo;
console.log(red); // "one"
console.log(yellow); // "two"
console.log(green); // "three"
```

## 변수에 배열의 나머지 할당하기

```js
var [a, ...b] = [1, 2, 3];
console.log(a); // 1
console.log(b); // [2, 3]
```

## 변수 값 교환하기

```js
var a = 1;
var b = 3;

[a, b] = [b, a];
console.log(a); // 3
console.log(b); // 1
```

## 객체 구조 분해 할당

```js
const person = {
  name: 'Alice',
  age: 25,
  job: 'Engineer'
};

const { name, age, job } = person;

console.log(name); // Alice
console.log(age);  // 25
console.log(job);  // Engineer
```

### 중첩된 객체에서의 구조 분해 할당

```js
const user = {
  id: 42,
  isVerified: true,
  profile: {
    name: 'John',
    age: 30
  }
};

const { profile: { name, age } } = user;

console.log(name); // John
console.log(age); // 30
```

### 함수에서 객체를 구조 분해하여 매개변수로 사용

```js
function display({ title, author }) {
  console.log(`The book "${title}" was written by ${author}.`);
}

const book = {
  title: '1984',
  author: 'George Orwell',
  year: 1949
};

display(book); // 출력: The book "1984" was written by George Orwell.
```