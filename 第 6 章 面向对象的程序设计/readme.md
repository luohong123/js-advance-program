
# 第 6 章 面向对象的程序设计

# 一、理解对象属性
## （一）属性类型
### 1、数据属性
数据属性包含一个数据值的位置。在这个位置可以读取和写入值。
（1）数据属性
- Configurable：表示能否通过 delete 删除属性从而重新定义属性，能否修改属性的特
性，或者能否把属性修改为访问器属性。

- Emunerable：表示能否通过 for-in 循环返回属性。

- Writable：表示能否修改属性的值。
```javascript
var obj = { }
Object.defineProperty(obj,'name',{
  writable: false, // 设置为false 不可以修改属性值
  value:'honghong'
})
obj.name = 'qingcheng';
console.log(obj.name); // honghong
```
- Value：包含这个属性的数据值。读取属性值的时候，从这个位置读;写入属性值的时候，
把新值保存在这个位置。
