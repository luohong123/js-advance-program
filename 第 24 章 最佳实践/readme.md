
# 第 24 章 最佳实践

<img src = "https://github.com/luohong123/js-advance-program/blob/master/%E7%AC%AC%2024%20%E7%AB%A0%20%E6%9C%80%E4%BD%B3%E5%AE%9E%E8%B7%B5/image.png" />

### 应用逻辑和事件处理程序相分离
- 优点
1. 可以让你更容易更改触发特定过程的事件。如果最开始由鼠标点击事件触发过程，但现在按键也要进行同样处理，这种更改就很容易。
2. 在不附加到事件的情况下测试代码，使其更易创建单元测试或者是自动化应用流程.
```javascript
/**
 * 接收一个值，并根据该值进行其他处理
 *
 */
function validateValue(value){
    value = 5 * parseInt(value);
    if (value > 10){
    document.getElementById("error-msg").style.display = "block"; }
}
/**
 * 确认是按下了 Enter 键
 *
 */
function handleKeyPress(event){
    event = EventUtil.getEvent(event);
    if (event.keyCode == 13){
        var target = EventUtil.getTarget(event);
        validateValue(target.value);
    }
}
```

- 避免与 null 进行比较
```javascript
function sortArray(values){
  if (values instanceof Array){ //推荐 values.sort(comparator);
  } 
}
```

- 
