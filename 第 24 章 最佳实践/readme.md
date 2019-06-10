
# 第 24 章 最佳实践

<img src = "https://github.com/luohong123/js-advance-program/blob/master/%E7%AC%AC%2024%20%E7%AB%A0%20%E6%9C%80%E4%BD%B3%E5%AE%9E%E8%B7%B5/image.png" />

- 避免与 null 进行比较
```javascript
function sortArray(values){
  if (values instanceof Array){ //推荐 values.sort(comparator);
  } 
}
```
