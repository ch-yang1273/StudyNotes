---
created: 2023-10-31
---
키워드:: [[자바스크립트]] [[CSS]]

## stylelint

sass-lint는 정상적으로 동작하지 않았습니다. 사용자도 더 많고, 계속 업데이트되는 stylelint를 사용합니다.

### stylelint 설치

```shell
npm install --save-dev stylelint stylelint-config-standard stylelint-config-prettier stylelint-config-clean-order
```

설명을 찾다 보니 `Prettier`와 충돌이 좀 있는 것 같아 "stylelint-config-prettier" 패키지도 받았습니다.

#### Stylelint 설정 파일 생성 및 설정

프로젝트 최상단 root 위치에 `.stylelintrc.json`을 생성하고 설치한 패키지를 `extends`에 추가합니다.

```json
{ 
  "extends": [ 
    "stylelint-config-standard", 
    "stylelint-config-prettier",
    "stylelint-config-clean-order"
  ],
  "rules": {}
}
```

주의! "stylelint-config-prettier"가 뒤에 있어야 `Prettier`와 충돌하는 `Stylelint` 규칙들이 무시됩니다. 후 순위가 덮는 로직인가 봅니다.

### stylelint, prettier VSCode 설정

Stylelint와 Prettier 확장을 설치하고 활성화합니다.

`Ctrl + ,`을 눌러 VSCode 설정을 열고 `Format On Save`를 검색하여 체크합니다. 파일 저장할 때 자동으로 Prettier가 실행됩니다.

이제 코드를 작성하고 저장할 때마다 Prettier가 자동으로 코드를 포맷하고, Stylelint 규칙에 따라 코드에 문제가 있으면 오류나 경고를 볼 수 있습니다.

#### 자동 수정

`ctrl + ,` + setting.json 에서 다음 내용을 추가 합니다. 저장 시 자동으로 수정을 해줍니다.

```json
  "stylelint.enable": true,
  "css.validate": false,
  "less.validate": false,
  "scss.validate": false,
  "editor.formatOnSave": true
```

![[Pasted image 20231102224620.png]]

### pacakage.json에 명령어 추가

```json
{
  "scripts": {
    "lint:css": "stylelint --ignore-path .gitignore '**/*.css'",
    "lint:css:fix": "stylelint --ignore-path .gitignore '**/*.css' --fix"
  },
  "devDependencies": {
    "stylelint": "^13.13.1",
    "stylelint-config-standard": "^22.0.0",
    "stylelint-config-prettier": "^9.0.3"
  }
}
```

`lint:css`: 모든 CSS 파일을 lint하며, `.gitignore` 파일에 명시된 패턴을 무시합니다
`"lint:css:fix"`: 모든 CSS 파일을 lint 하고, 가능한 에러를 자동으로 수정합니다

`devDependencies`는 개발할 때만 사용하는 라이브러리 설정인 것 같은데, 좀 더 알아봐야겠다. #search/devDependencies

```
npm install --save-dev stylelint
npm install --save-dev stylelint-config-standard
npm install --save-dev stylelint-config-prettier
```

### 에러 상황 예시

```css
.selector1,
.selector2, .selector3 {
  width: 500px;
  color: blue;
  display: block;  
}
```

### 호환성 오류 및 호환 버전 설정

stylelint의 버전(15.11.0)이 너무 높고, 15보다는 낮아야 한다고 합니다. 그래서 `@^14.0.0`으로 14 버전 중에 최신 버전을 설치 했습니다.

```bash
λ npm install --save-dev stylelint-config-prettier
npm ERR! code ERESOLVE
npm ERR! ERESOLVE unable to resolve dependency tree
npm ERR!
npm ERR! While resolving: css_sass@1.0.0
npm ERR! Found: stylelint@15.11.0
npm ERR! node_modules/stylelint
npm ERR!   dev stylelint@"^15.11.0" from the root project
npm ERR!
npm ERR! Could not resolve dependency:
npm ERR! peer stylelint@">= 11.x < 15" from stylelint-config-prettier@9.0.5
npm ERR! node_modules/stylelint-config-prettier
npm ERR!   dev stylelint-config-prettier@"*" from the root project
npm ERR!
npm ERR! Fix the upstream dependency conflict, or retry
npm ERR! this command with --force or --legacy-peer-deps
npm ERR! to accept an incorrect (and potentially broken) dependency resolution.
```

`stylelint-config-standard`도 버전 너무 높다 해서 Github에서 호환성 버전 정보 확인 후 `@^29.0.0` 버전을 설치합니다.

![[Pasted image 20231102082702.png]]

`package.json`에서 `devDependencies` 내용을 모두 지우고 `npm install`로 반영 먼저 했습니다.

```bash
npm install --save-dev stylelint@^14.0.0
npm install --save-dev stylelint-config-standard@^29.0.0
npm install --save-dev stylelint-config-prettier
```

#### 패키지 설치 결과 버전 확인

```json
"devDependencies": {
  "stylelint": "^14.0.0",
  "stylelint-config-prettier": "^9.0.5",
  "stylelint-config-standard": "^29.0.0"
}
```

#### 참고: 해당 패키지의 최신 버전 확인

```bash
npm show stylelint version
npm show stylelint-config-standard version
npm show stylelint-config-prettier version
```