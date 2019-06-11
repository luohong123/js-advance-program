
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
    alert(Object.prototype.toString.call(person1)); // [object Object]
```
- 优点
可以无数次的调用这个函数，创建了多个相似对象的问题
- 缺点
没有解决对象识别的问题，不知道一个对象的类型
## （二）构造函数模式
- 构造函数模式与工厂模式的不同之处在于
1. 没有显式地创建对象。
2. 直接将属性和方法赋给了 this 对象。
3. 没有 return 语句。
-  调用构造函数过程
1. 创建一个新对象。
2. 将构造函数的作用域赋给新对象(因此 this 就指向了这个新对象)。
3. 执行构造函数中的代码(为这个新对象添加属性)。
4. 返回新对象。
-  优点

- 缺点

## （三）原型模式
-  优点

- 缺点
如不同的实例对象修改引用类型的值会相互影响，如下代码：
```javascript
function Person(){
}
Person.prototype = {
    constructor: Person,
    name : "Nicholas",
    age : 29,
    job : "Software Engineer",
    friends : ["Shelby", "Court"],
    sayName : function () {
        alert(this.name);
} };
var person1 = new Person();
var person2 = new Person();
person1.friends.push("Van");
alert(person1.friends);    //"Shelby,Court,Van"
alert(person2.friends);    //"Shelby,Court,Van"
alert(person1.friends === person2.friends);  //true
```
由于共享的本质，修改了 person1.friends 引用的数组，向数组中添加了一个字符 串，导致person2.friends共享了prototype中的friends属性，值也被修改了。
## （四）组合使用构造函数模式和原型模式
-  优点

- 缺点

## （五）动态原型模式
-  优点

- 缺点

## （六）寄生构造函数模式
-  优点

- 缺点

## （七）稳妥构造函数模式
-  优点

- 缺点


# 三、理解继承
## （一）原型链

## （二）借用构造函数继承

-  优点

- 缺点

## （三）组合式继承

-  优点

- 缺点

## （四）原型式继承

-  优点

- 缺点

## （五）寄生式继承

-  优点

- 缺点

## （六）寄生组合式模式

-  优点

- 缺点
