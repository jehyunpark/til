# Git flow
## gitflow를 이용해서 만들 수 있는 branch 종류
  - master : 최종 릴리즈한 안정화 버전
  - develop : 다음 릴리즈를 위해 개발중인 최신 버전
  - feature : 특정 기능 개발을 위한 branch
  - release : 릴리즈 점검을 위한 branch
  - hotfix : 긴급 버그 픽스를 위한 branch
  - support : 버전 호환성 문제 처리를 위한 branch

## git flow 설치 확인
```
jehyunpark@innoquartz-server(develop)*$ git flow
usage: git flow <subcommand>

Available subcommands are:
   init      Initialize a new git repo with support for the branching model.
   feature   Manage your feature branches.
   release   Manage your release branches.
   hotfix    Manage your hotfix branches.
   support   Manage your support branches.
   version   Shows version information.
   config    Manage your git-flow configuration.

Try 'git flow <subcommand> help' for details.
```

## git flow 는 master에서 초기화한다.
```
jehyunpark@innoquartz-server(develop)$ git checkout master
Branch master set up to track remote branch master from origin.
Switched to a new branch 'master'
```
```인
jehyunpark@innoquartz-server(master)$ git flow init

Which branch should be used for bringing forth production releases?
   - develop
   - master
Branch name for production releases: [master]

Which branch should be used for integration of the "next release"?
   - develop
Branch name for "next release" development: [develop]

How to name your supporting branch prefixes?
Feature branches? [feature/]
Release branches? [release/]
Hotfix branches? [hotfix/]
Support branches? [support/]
Version tag prefix? []
jehyunpark@innoquartz-server(master)$
```

## develop branch로 변경
```
jehyunpark@innoquartz-server(master)$ git checkout develop
```
## 새로운 feature 생성
```
jehyunpark@innoquartz-server(develop)*$ git flow feature start 450-direct-file-upload
Branches 'develop' and 'origin/develop' have diverged.
And local branch 'develop' is ahead of 'origin/develop'.
M	src/main/resources/static/js/innoquartz/job.js
M	src/main/resources/templates/job/create.html
M	src/main/resources/templates/job/modify.html
Switched to a new branch 'feature/450-direct-file-upload'

Summary of actions:
- A new branch 'feature/450-direct-file-upload' was created, based on 'develop'
- You are now on branch 'feature/450-direct-file-upload'

Now, start committing on your feature. When done, use:

     git flow feature finish 450-direct-file-upload
```

## 개발과 테스트를 완료 했다면 feature에 커밋한다.
```
jehyunpark@innoquartz-server(feature/450-direct-file-upload)*$ git add .
jehyunpark@innoquartz-server(feature/450-direct-file-upload)*$ git commit -m "#450 파일선택 > 업로드 2단계를 파일선택과 업로드 동시에 될 수 있도록 변경"
[feature/450-direct-file-upload 7eaa62d] #450 파일선택 > 업로드 2단계를 파일선택과 업로드 동시에 될 수 있도록 변경
 3 files changed, 143 insertions(+), 74 deletions(-)
```

## 커밋된 feature 테스트 실행
```
jehyunpark@innoquartz-server(feature/450-direct-file-upload)$ ./gradlew test

BUILD SUCCESSFUL

Total time: 52.976 secs

This build could be faster, please consider using the Gradle Daemon: https://docs.gradle.org/2.10/userguide/gradle_daemon.html
```

## 테스트를 정상 완료했다면 feature를 finish 한다.
```
jehyunpark@innoquartz-server(feature/450-direct-file-upload)$ git flow feature finish
Branches 'develop' and 'origin/develop' have diverged.
And local branch 'develop' is ahead of 'origin/develop'.
Switched to branch 'develop'
Your branch is ahead of 'origin/develop' by 1 commit.
  (use "git push" to publish your local commits)
Updating d51a368..7eaa62d
Fast-forward
 src/main/resources/static/js/innoquartz/job.js | 78 ++++++++++++++++++++++++++++++++++++++++++++++++++++++------------------------
 src/main/resources/templates/job/create.html   | 50 +++++++++++++++++++++++++++++++++++---------------
 src/main/resources/templates/job/modify.html   | 89 ++++++++++++++++++++++++++++++++++++++++++++++++++++++-----------------------------------
 3 files changed, 143 insertions(+), 74 deletions(-)
Deleted branch feature/450-direct-file-upload (was 7eaa62d).

Summary of actions:
- The feature branch 'feature/450-direct-file-upload' was merged into 'develop'
- Feature branch 'feature/450-direct-file-upload' has been locally deleted
- You are now on branch 'develop'
```

## remote repository의 소스를 pull 한다. 충돌나면 잘 머징한다.
```
jehyunpark@innoquartz-server(develop)$ git pull origin develop
Password for 'http://jhpark@123.4.5.6:7890':
From http://123.4.5.6:7890/InnoQuartz/innoquartz-server
 * branch            develop    -> FETCH_HEAD
   2aa8c24..d51a368  develop    -> origin/develop
Already up-to-date.
```

## pull 한 최신 소스로 테스트 해본다.
```
jehyunpark@innoquartz-server(develop)$ ./gradlew test
:generateQueryDSL UP-TO-DATE
:compileJava UP-TO-DATE
:processResources UP-TO-DATE
:classes UP-TO-DATE
:compileTestJava UP-TO-DATE
:processTestResources UP-TO-DATE
:testClasses UP-TO-DATE
:test UP-TO-DATE

BUILD SUCCESSFUL

Total time: 6.672 secs

This build could be faster, please consider using the Gradle Daemon: https://docs.gradle.org/2.10/userguide/gradle_daemon.html
```

## clean build 도 해본다.
```
jehyunpark@innoquartz-server(develop)$ ./gradlew clean build


BUILD SUCCESSFUL

Total time: 1 mins 8.187 secs

This build could be faster, please consider using the Gradle Daemon: https://docs.gradle.org/2.10/userguide/gradle_daemon.html
```

## 문제가 없으면 origin에 push한다.
```
jehyunpark@innoquartz-server(develop)$ git push origin develop
Password for 'http://jhpark@123.4.5.6:7890':
Counting objects: 57, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (13/13), done.
Writing objects: 100% (13/13), 3.37 KiB | 0 bytes/s, done.
Total 13 (delta 10), reused 0 (delta 0)
remote: Resolving deltas: 100% (10/10)
remote: Updating references: 100% (1/1)
To http://jhpark@123.4.5.6:7890/InnoQuartz/innoquartz-server
   d51a368..7eaa62d  develop -> develop
```
