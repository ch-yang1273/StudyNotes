---
created: 2023-11-05
---
키워드:: [[Git]]

> Remote-tracking branches 중심으로 내용 다시 구성해서 글 작성해야겠다.

## Git Local

Local에서 사용하는 Git 작업 영역은 `Working Directory`, `Staging Area`, `Repository (Local)` 세 가지가 있습니다.

![[Git_작업영역.png]]

이미지 출처 : [Introduction to Git, GitHub, and Version Control​ workshop-o-matic Library (microsoft.com)](https://techcommunity.microsoft.com/t5/educator-developer-blog/introduction-to-git-github-and-version-control-workshop-o-matic/ba-p/3951511)

### Working Directory

프로젝트 파일들이 실제 위치한 공간으로 이 영역에서 파일을 생성, 수정, 삭제를 합니다.

### Staging Area

Git에 기록을 준비하는 임시 영역입니다. `git add` 명령어로 Working Directory에서 변경 된 내용을 추가 할 수 있습니다.

### Repository (Local)

프로젝트의 버전 정보와 변경 이력이 저장되는 공간입니다. 기존의 프로젝트를 clone 하거나, 새로운 프로젝트에서 `git init` 명령어로 생성할 수 있습니다.

`git commit` 명령어로 Staging Area의 내용을 Repository에 기록할 수 있습니다.

## Git Remote Reposiotry

참고 : [Git - Remote Branches (git-scm.com)](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches)

Remote Repository는 인터넷이나 네트워크를 통해 접근할 수 있는 중앙 집중식 리포지토리로, Local Repository의 백업 저장소나 협업의 용도로 사용합니다. 

대표적인 Remote Repository 서비스로는 GitHub, GitLab, Bitbucket이 있습니다.

### 리모트-트래킹 브랜치 (Remote-tracking branches)

GitHub과 같은 Remote Repository를 사용하며 작업을 진행할 때, `origin/master`, `origin/branch1`과 같은 브랜치 이름을 본 적이 있을 것입니다. 보지 못했다면, Working Directory의 터미널에서 `git log --oneline --graph` 명령을 실행하거나, 소스트리(GUI Git 프로그램)의 History에서 볼 수 있습니다.

`Remote-tracking branches`는 Remote branch를 추적하는 참조 브랜치로, Local Repository의 브랜치에는 영향을 주지 않습니다. 이 브랜치는 Remote Reopository에 마지막으로 연결했던 순간 Remote Repository의 상태를 나타냅니다.

여러 사람들이 같이 작업하며 Remote Repository에 `git push` 등의 명령으로 반영합니다. 하지만 Remote Repository와 Local Repository는 별개 공간에 위치하고, Local에서는 이러한 변경 사항을 자동으로 알 수 없습니다.

`git fetch` 명령어는 알 수 없었던 Remote Repository의 최신 정보를 가져와 `Remote-tracking branches`에 반영합니다. 이 명령어를 통해 원격에서 어떤 변경이 있었는지 확인할 수 있습니다. 

Local 영역에서 `origin/master`, `origin/branch1`과 같은 브랜치의 상태를 확인 할 수 있는 것은 사실 Remote branch를 보고 있는 것이 아니라. 이 가시화 된 `Remote-tracking branches`를 보고 있는 것 입니다.

### fetch vs. pull

이 `Remote-tracking branches`를 이해했다면, `git fetch`와 `git pull`의 차이도 이해하기 좋습니다.

...

어디서는 git pull 대신 git fetch, git merge를 사용하라고 하지만, 개인적으로 merge 이름이 주는 압박이 있어서 git fetch로 Remote Repository를 확인 후에 그냥 git pull을 하는 편입니다.

...
