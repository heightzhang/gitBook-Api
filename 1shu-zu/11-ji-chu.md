
- [1 in](#1-in)
- [2 for in](#2-for-in)
- [3 toString](#3-tostring)
- [4 deleted ](#4-deleted)

## 1 in

如果我们要检测`xiaoming`是否拥有某一属性，可以用`in`操作符

继承原型链

```JS
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

```
var xiaoming = {
name: '小明'
};
xiaoming.hasOwnProperty('name'); // true
xiaoming.hasOwnProperty('toString'); // false
```

## 2 for in

```JS
for (var prop in obj ) {
// 这里打印的prop为每一个属性名
console.log(prop);
// 这里打印的obj[attr]是每一个属性值;
console.log(obj[attr])
}
```

## 3 toString

 将对象转成字符串或者布尔值转成字符串

```JS
var boo = new Boolean(true)
console.log(boo.toString()) // 'true'
```

## 4 deleted

删除对象的某个属性