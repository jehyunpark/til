# button 안의 element나 text를 클릭하면 button 클릭 이벤트가 실행되지 않는 문제 해결방법

# 문제 발생
`<button>` 안에 `<i>text</i>` 가 있었는데 `text` 부분만 클릭하면 버튼을 클릭되지만 안에 바인딩하는 데이터가 전송되지 않았다.
그러나 `text` 를 둘러싸고 있는 버튼 가장자리를 잘 클릭하면 제대로 작동했다.

# 해결
`<i>text</i>` 에 `style="pointer-events: none"` 를 추가했다.
```
<i class="i i-download2" style="pointer-events: none">text </i>
```


# css에 추가하는 방법
- button 안의 span element에 `pointer-events: none;` 스타일을 추가한다.
```
span {
    display: block;
    padding: 20px;
    pointer-events: none;   // < --- Solution!
}
```

# 참고
- [stackoverflow - Button element not firing click event when clicking on button text and releasing off it (but still inside the button)?](http://stackoverflow.com/questions/15679787/button-element-not-firing-click-event-when-clicking-on-button-text-and-releasing)
