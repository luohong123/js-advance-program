
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

# 二、理解创建对象
## （一）工厂模式
```javascript
function createPerson(name, age, job){
    var o = new Object();
    o.name = name;
    o.age = age;
    o.job = job;
    o.sayName = function(){
        alert(this.name);
    };
    return o; 
}
    var person1 = createPerson("Nicholas", 29, "Software Engineer");
    var person2 = createPerson("Greg", 27, "Doctor");
```
- 优点
可以无数次的调用这个函数，创建了多个相似对象的问题
- 缺点
没有解决对象识别的问题，不知道一个对象的类型
## （二）


##
# 三、理解继承
