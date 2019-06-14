
<img src="https://github.com/luohong123/js-advance-program/blob/master/%E7%AC%AC%203%20%E7%AB%A0%20%E5%9F%BA%E6%9C%AC%E6%A6%82%E5%BF%B5/%E7%9B%B8%E7%AD%89%E5%92%8C%E4%B8%8D%E7%9B%B8%E7%AD%89.png" />


- break
```javascript
var num = 0;
outermost:
for (var i=0; i < 10; i++) {
     for (var j=0; j < 10; j++) {
        if (i == 5 && j == 5) {
            break outermost;
        }
num++; }
}
console.log(num);    //55
```
- continue
```javascript
var num = 0;
outermost:
for (var i=0; i < 10; i++) {
for (var j=0; j < 10; j++) { if (i == 5 && j == 5) { continue outermost;
}
num++; }
}
console.log(num);    //95
```
