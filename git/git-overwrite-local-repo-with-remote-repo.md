# Remote Repository 내용을 Local에 덮어쓰기
- repository를 clone해서 여러 곳에서 개발을 하다가 보면 지금 이 local repository가 어떤 상태인지 불분명할 때가 있다.
- 그래서 'pull로 remote repository 내용을 가져와서 다시 작업하자.' 라고 생각하고 pull을 하면 충돌나면서 merge 하라고 뜰 때도 있다.
- 그냥 remote repository가 다 맞다. 옳다. 그러니 난 local에 덮어 쓰고 처음부터 다시 코딩하고 싶다.
- 이럴 때 local repository를 뭐 지우고 다시 clone 받는 방법도 있겠지만, 아래와 같은 방법도 있다.

  ```
  git fetch --all
  git reset --hard origin/master
  ```

- 이렇게 하면 remote repository의 최신 내용으로 덮어써진다.
