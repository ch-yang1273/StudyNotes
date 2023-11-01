---
created: 2023-10-31
---
키워드:: [[자바스크립트]] [[CSS]]

## stylelint

sass-lint는 정상적으로 동작하지 않았습니다. 사용자도 더 많고, 계속 업데이트되는 stylelint를 사용합니다.

### stylelint 설치

```shell
npm install --save-dev stylelint stylelint-config-standard stylelint-config-prettier
```

설명을 찾다 보니 `Prettier`와 충돌이 좀 있는 것 같아 "stylelint-config-prettier" 패키지도 받았습니다.

#### Stylelint 설정 파일 생성 및 설정

root 위치에 `.stylelintrc`을 생성하고 설치한 패키지를 `extends`에 추가합니다.

```json
{ 
  "extends": [ 
    "stylelint-config-standard", 
    "stylelint-config-prettier" 
  ],
  "rules": {}
}
```

주의! "stylelint-config-prettier"가 뒤에 있어야 `Prettier`와 충돌하는 `Stylelint` 규칙들이 무시됩니다. 후 순위가 쎈가봐요.

### stylelint, prettier VSCode 설정

Stylelint와 Prettier 확장을 설치하고 활성화합니다.

`Ctrl + ,`을 눌러 VSCode 설정을 열고 `Format On Save`를 검색하여 체크합니다. 파일 저장할 때 자동으로 Prettier가 실행됩니다.

이제 코드를 작성하고 저장할 때마다 Prettier가 자동으로 코드를 포맷하고, Stylelint 규칙에 따라 코드에 문제가 있으면 오류나 경고를 볼 수 있습니다.

#### 수동 Stylelint 실행 (쓸 일 있나?)

```bash
npx stylelint "**/*.css"
```

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

### 버전 정보 확인

해당 패키지의 최신 버전을 알 수 있습니다.

```bash
npm show stylelint version
npm show stylelint-config-standard version
npm show stylelint-config-prettier version
```