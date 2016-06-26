# Git 한글 파일명 이슈 해결방법

Git 프로젝트에서 파일명을 한글로 했을 때 아래와 같은 Unicode관련 문제가 발생한다.

``` shell
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   "github/Github\354\227\220\354\204\234 \355\224\204\353\241\234\354\240\235\355\212\270 \354\213\234\354\236\221\355\225\230\352\270\260.md"

no changes added to commit (use "git add" and/or "git commit -a")
```

아래의 명령어를 사용하면 한글 깨짐 문제 없이 한글 파일명을 사용할 수 있다.

```
git config --global core.quotepath false
```
