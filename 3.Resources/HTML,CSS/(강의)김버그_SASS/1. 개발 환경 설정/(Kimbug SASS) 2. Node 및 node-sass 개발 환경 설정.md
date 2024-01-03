---
created: 2023-10-31
---
키워드:: [[(KimBug SASS)]]

## 개발 환경 설정

### LTS 버전의 Node 설치

npm이 같이 깔린다.

```Shell
node -v
# v20.9.0
npm -v 
# 10.1.0
```

### node-sass 설치

이거 말고 "dart sass" 깔아야 함 [[Node-sass vs. Dart sass]]

Document : [node-sass - npm (npmjs.com)](https://www.npmjs.com/package/node-sass)

```shell
# package.json이 생성된다.
npm init -y

# node-sass 설치 (i == install의 줄임말)
npm i node-sass
```

### package.json의 scripts 수정

참고 : [node-sass#command-line-interface](https://www.npmjs.com/package/node-sass#command-line-interface)

#### 1. 수정

```json
"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1",
  "node-sass": "node-sass",
  "sass": "node-sass -wr styles/main.scss ./style.css"
},

// sass 용으로 수정
"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1",
  "sass": "sass --watch styles/main.scss:style.css"
},
```

- `sass`: 이 부분은 Sass 컴파일러를 호출
- `--watch` : 이 옵션은 `styles/main.scss` 파일을 지속적으로 감시하도록 지시
- `styles/main.scss:style.css` : `main.scss` 파일을 `style.css`로 컴파일하도록 지정

#### 2. 실행

```shell
npm run test
npm run node-sass

# 이거만 쓰면 됨
npm run sass
```

파일 및 폴더 변경 감지 (-wr)
![[Pasted image 20231031232154.png]]