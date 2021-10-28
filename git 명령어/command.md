## git 브랜치 명령어

<br/>

### 새로운 브랜치 생성
+ `$ git branch 새로운 브랜치 이름`

### 새로운 브랜치 생성 후 해당 브랜치로 전환
+ `$ git switch -c 새로운 브랜치 이름`
+ `$ git checkout -b 새로운 브랜치 이름`

### 브랜치 목록 확인
+ `$ git branch`

### 브랜치 삭제
+ `$ git branch -d 삭제할 브랜치 이름`
+ `$ git branch -D` 해당 명령어는 병합하지 않은 브랜치를 강제 삭제하는 방법입니다.

### 브랜치 전환
+ `$ git switch 브랜치 이름`
+ `$ git checkout 브랜치 이름`

### 브랜치 병합
+ master 브랜치로 dev 브랜치를 병합할 때 (master ← dev)
1. `$ git checkout master`
2. `$ git merge dev`

### 로그에 모든 브랜치를 그래프로 표현
+ `$ git log --branches --graph --decorate`

### 아직 commit 하지 않은 작업을 스택에 임시로 저장
+ `$ git stash`

<br/>

## [git 문제해결 참고 사이트](https://dangitgit.com/ko)