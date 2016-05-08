# Git stash
- Stash는 워킹 디렉토리에 unstaged 파일들을 백업하고, 워킹 디렉토리를 깨끗한 상태, 즉 HEAD의 상태로 만드는 기능.  
- 마치 스냅샷을 찍어 어딘가에 잠깐 저장해 놨다가 작업 하던 것들을 그대로 다시 불러온다고 생각하면 이해가 쉽다.

## git stash save
- 현재 작업을 저장해두고 branch를 head로 돌린다.(git reset –hard)  
- [save]는 특정 이름으로 저장할 때 사용
  ```
  mepark@innoquartz-server(develop)*$ git stash
  ```

## git stash list
- 저장되어 있는 stash들 보기

## git stash pop
- 마지막 작업본 가져오기  
- stash들은 stack에 저장된다. 따라서 가장 최근에 save한 stash가 현재 branch에 적용된다.
  ```
  mepark@innoquartz-server(develop)$ git stash pop
  On branch develop
  Your branch is ahead of 'origin/develop' by 1 commit.
    (use "git push" to publish your local commits)

  Changes not staged for commit:
    (use "git add <file>..." to update what will be committed)
    (use "git checkout -- <file>..." to discard changes in working directory)

  	modified:   src/main/resources/static/js/innoquartz/job.js
  	modified:   src/main/resources/templates/job/create.html
  	modified:   src/main/resources/templates/job/modify.html

  no changes added to commit (use "git add" and/or "git commit -a")
  Dropped refs/stash@{0} (37cb63023e5179d86e21cd62d71ac2032da27c43)
  ```

## git stash apply
- 특정 작업본 가져오기  
- git stash pop 과 비슷한 명령어지만 stash list에서 삭제하지 않는다는 점이 다르다.

## git stash drop
- 필요 없는 stash를 삭제

## git stash clear
- 전체 stash list를 삭제
