
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

### 避免全局量
var name = "Nicholas";
变量 name 覆盖了 window.name 属性
```javascript
// 一个全局量——推荐 
var MyApplication = { 
    name: "Nicholas",
    sayName: function(){
        alert(this.name);
    } 
};
```
### 使用常量
显示在用户界面上的字符串应该以允许进行语言国际化的方式抽取出来，如 Constants
URL也应被抽取出来，因为它们有随着应用成长而改变的倾向
```javascript
 var Constants = {
        INVALID_VALUE_MSG: "Invalid value!",
        INVALID_VALUE_URL: "/errors/invalid.php"
};
function validate(value){
    if (!value){
        alert(Constants.INVALID_VALUE_MSG);
        location.href = Constants.INVALID_VALUE_URL;
    } 
}
```
### 后测试循环
```javascript
var i=values.length -1;
if (i > -1){
do {
    process(values[i]);
    }while(--i >= 0);
}
```
将终止条件和自减操作符组合成了单个语句，这时，任何进一步的优化只能在 process() 函数中进行了，因为循环部分已经优化完全了。记住使用“后测试”循环时必须确保要处理的值至少有一个。空数组会导致多余的一次循环而“前 测试”循环则可以避免。

```javascript
var i = 2;
console.log(--i); // 1,  先执行 i = i - 1，再使用 i 的值
var j = 2;
console.log(j--); // 2， 先使用 j 的值，再执行 j = j - 1
```

### 最小现场更新
```javascript
var list = document.getElementById("myList"),
    fragment = document.createDocumentFragment(),
    item, i;
for (i=0; i < 10; i++) {
    item = document.createElement("li"); 
    fragment.appendChild(item); 
    item.appendChild(document.createTextNode("Item " + i));
}
list.appendChild(fragment);
```
