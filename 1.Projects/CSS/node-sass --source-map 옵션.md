---
created: 2023-11-07
---
키워드:: [[CSS]]

css 적용 상태를 확인하기 위해 개발자 도구를 보면, 자동 생성된 `.css` 파일에서 선언 위치를 찾아준다.

하지만 개발에 필요한 내용은 `.scss`의 선언 위치이다.

node-sass의 `--source-map` 옵션을 사용하면 이 문제를 해결 할 수 있다. `--source-map true` 옵션을 추가하면 `.map` 파일을 생성해준다.

package.json에 다음 내용을 적용하면 된다.

```json
"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1",
  "node-sass": "node-sass",
  "sass": "node-sass -wr --source-map true styles/main.scss ./style.css"
}
```

> The `--source-map` option accepts a boolean value, in which case it replaces destination extension with `.css.map`. It also accepts path to `.map` file and even path to the desired directory. When compiling a directory `--source-map` can either be a boolean value or a directory. --https://www.npmjs.com/package/node-sass

![[Pasted image 20231107041634.png]]

![[Pasted image 20231107041549.png]]

