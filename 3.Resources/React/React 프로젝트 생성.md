---
created: 2023-12-03
---
키워드:: [[React]]

## React 프로젝트 생성

프로젝트 생성 시간이 오래 걸리긴 했지만 생성 방법은 쉽다.

```bash
# 프로젝트 생성
npx create-react-app study
# 프로젝트 폴더로 이동
cd study
# 개발 서버 구동
npm start
```

![[ReactDevServerStartPage.png]]

### 프로젝트 생성 에러

```bash
λ npx create-react-app study
npm ERR! code ENOENT
npm ERR! syscall lstat
npm ERR! path C:\Users\username\AppData\Roaming\npm
npm ERR! errno -4058
npm ERR! enoent ENOENT: no such file or directory, lstat 'C:\Users\username\AppData\Roaming\npm'
npm ERR! enoent This is related to npm not being able to find a file.
npm ERR! enoent
```

`C:\Users\username\AppData\Roaming\` 경로에 `npm` 폴더 하나 만들어주면 된다.