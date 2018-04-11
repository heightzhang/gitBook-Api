
- [1 创建对象](#1-创建对象)
- [2 访问对象](#2-访问对象)
- [3 常用方法](#3-常用方法)
- [3.1 判断对象：是否拥有某一个属性](#31-判断对象：是否拥有某一个属性)
- [3.2 遍历对象 ](#32-遍历对象-)
- [3.3 其它](#33-其它)

## 1 创建对象

字面量 var obj ={}; 用花括号 多个属性值之间用’’,’’号隔开;

构造函数 var obj = new Object()

自定义构造函数: functions person(){}



## 2 访问对象

JavaScript对象的所有属性都是字符串，属性对应的值可以是任意数据类型。

属性是一个有效的变量名通过`.`操作符完成的；

属性包含特殊字符，就必须用`['']`括起来

总结:变量名`.`操作符,特殊字符`['']`;

```js
var xiaohong = {
name: '小红',
'middle-school': 'No.1 Middle School'
};
xiaohong['middle-school']; // 'No.1 Middle School'
xiaohong['name']; // '小红'
xiaohong.name; // '小红'
```




## 3 常用方法

### 3.1 判断对象：是否拥有某一个属性

如果我们要检测`xiaoming`是否拥有某一属性，可以用`in`操作符

继承原型链

```js
var xiaoming = {
name: '小明',
birth: 1990,
school: 'No.1 Middle School',
height: 1.70,
weight: 65,
score: null
};
'name' in xiaoming; // true
'grade' in xiaoming; // false
// 因为toString定义在object对象中，而所有对象最终都会在原型链上指向object
// 所以xiaoming也拥有toString属性
'toString' in xiaoming; // true
```

非继承原型链(来自对象自身)

```js
var xiaoming = {
name: '小明'
};
xiaoming.hasOwnProperty('name'); // true
xiaoming.hasOwnProperty('toString'); // false
```



### 3.2 遍历对象

For in循环

```js
for (var prop in obj ) {
// 这里打印的prop为每一个属性名
console.log(prop);
// 这里打印的obj[attr]是每一个属性值;
console.log(obj[attr])
}
```



### 3.3 其它

tostring() 将对象转成字符串或者布尔值转成字符串

```js
var boo = new Boolean(true)
console.log(boo.toString()) // 'true'
```



deleted 删除对象的某个属性