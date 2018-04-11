

- [1 复制对象的三种方法](#1-复制对象的三种方法)
- [2 合并对象的两种情况](#2-合并对象的两种情况)

## 1 复制对象的三种方法

遍历法： 浅复制

```js
var xiaohong = {
  name: '小红',
  'middle-school': 'No.1 Middle School'
};
var copy = {}
for (var prop in xiaohong) {
  copy[prop] = xiaohong[prop]
}
console.log(copy === xiaohong) // false
```



assign法： 浅复制

```js
var obj = {name:'laoxie'}
var copyObj = Object.assign({}, obj)
console.log(copyObj) // {name:'laoxie'}

```

JSON法: 深复制

```js
var xiaohong = {
  name: '小红',
  'middle-school': 'No.1 Middle School'
};
var copy = JSON.parse(JSON.stringify(xiaohong))
console.log(copy === xiaohong) // false
```

 forEach法

[参考MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)

```js
function copy(obj) {
  var copy = Object.create(Object.getPrototypeOf(obj));
  var propNames = Object.getOwnPropertyNames(obj);
  propNames.forEach(function (name) {
    var desc = Object.getOwnPropertyDescriptor(obj, name);
    Object.defineProperty(copy, name, desc);
  });
  return copy;
}
var obj1 = {
  a: 1,
  b: 2
};
var obj2 = copy(obj1); // obj2 looks like obj1 now
console.log(obj1 === obj2) // false
```







## 2 合并对象的两种情况

1.相同属性覆盖,不相同属性添加 Object.assign

2.相同属性覆盖,不相同属性剔除 自己封装的一个方法，适合用在自定义的参数赋值



案例如下：

```js
let obj1 = {
  cat_id: NaN,
  name: null
}
let obj2 = {
  cat_id: 1,
  name: 'John',
  hobby: 'playfootball'
}
// 任务1 相同属性覆盖,不相同属性添加
/*
let targetObj = {
  cat_id: 1,
  name: 'John'，
  hobby: 'playfootball'
}
*/

// 方法
Object.assign(obj1, obj2)

// 任务2 相同属性覆盖,不相同属性剔除
/*
let targetObj = {
  cat_id: 1,
  name: 'John'
}
*/
// 方法
function test2 (obj1,obj2) {
  // 拿到共同元素属性名，通过属性名去判断
  Object.keys(obj1).forEach(key => {
    if (key in obj2) obj1[key] = obj2[key]
  })
  return obj1
}
console.log(test2(obj1,obj2))



```

