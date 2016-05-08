# 커밋 후 푸시까지 했는데 되돌리고 싶을 때 해결방법

1. 방금 푸시 하기 바로 전 Revision 으로 되돌린다.
```
git reset HEAD^
```

2. 원하는대로 수정한다.

3. 다시 Stage로 추가하고 커밋한다.
```
git add .
git commit -m ‘Revert push and re-push’
```

4. 그냥 푸쉬하면 에러가 발생한다. 그러므로 `+master`로 강제 푸시한다.
```
git push origin +master
```
