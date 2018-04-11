

- [1 复制数组](#1-复制数组)
  - [1.1 遍历复制法](#11-遍历复制法)
  - [1.2 用slice方法实现数组复制](#12-用slice方法实现数组复制)
  - [1.3 concat复制](#13-concat复制)
- [2 排序数组](#2-排序数组)
  - [2.1 Sort排序法](#21-sort排序法)
  - [2.2 冒泡排序法](#22-冒泡排序法)
  - [2.3 选择排序法](#23-选择排序法)
- [3 数组去重](#3-数组去重)
  - [3.1 ES5的filter方法](#31-es5的filter方法)
  - [3.2 ES6的set方法](#32-es6的set方法)

## 1 复制数组

原理注意(数据在内存中的状态， 栈内存与堆内存)：

数组是属于引用数据类型：**变量都会存在栈里面； 数组中的内容存放在堆里面**。所以，改变该数组内容（堆），数组的两个变量(两个指针)的值都会改变 。

而基本数据类型，**数组内容和变量声名都是存放在堆里面**。所以，改变内容的值，两个变量都会改变。=>变量等于内容，是真实值非指针；

 因此，复制数组的重点是要复制堆的内容。



### 1.1 遍历复制法

 遍历复制   复制堆里面的内容,而不能复制栈,复制栈只是复制一个指针而已;

```js
var arr = [10, 20 ,30]
var arr2 = arr
console.log('arr === arr2', arr === arr2) // 堆内存相同，返回true
var arr3 = []
for (var i = 0; i < arr.length; i++) {
  arr3[i] = arr[i]
}
console.log('arr===arr3', arr === arr3) // 堆内存不同，返回false

var num = 123
var num2 = num
console.log('num === num2', num === num2)
```

引用数据类型 判断是否同一个数据，堆内存不同，返回false；

基本数据类型判断值是否相等；



### 1.2 用slice方法实现数组复制

（超级简单的方式，适用于不需要遍历的情况下）

```js
//  复制数组的操作
var arr = ['A', 'B', 'C', 'D', 'E', 'F', 'G'];
var aCopy = arr.slice() // ['A', 'B', 'C', 'D', 'E', 'F', 'G']
aCopy === arr; // false
```



数组复制的方法有两种 ，遍历与非遍历

### 1.3 concat复制

```js
var arr = [1,2,3]
var add = arr.concat()
console.log(add === arr) // false
```





## 2 排序数组

排序也是在程序中经常用到的算法。无论使用冒泡排序还是快速排序，排序的核心是比较两个元素的大小。如果是数字，我们可以直接比较，但如果是字符串或者两个对象呢？直接比较数学上的大小是没有意义的，因此，比较的过程必须通过函数抽象出来。**通常规定，对于两个元素`x`和`y`，如果认为`x < y`，则返回`-1`，如果认为`x == y`，则返回`0`，如果认为`x > y`，则返回`1`**，这样，排序算法就不用关心具体的比较过程，而是根据比较结果直接排序。

### 2.1 Sort排序法

sort：将数组中的元素排序，并返回排序后的数组  （以第一个进行排序）

注意：默认把所有元素先转换为String再排序（再用ASCII码进行对比）;

​           sort()方法会直接对Array进行修改，它返回的结果仍是当前Array：

字的排序：

```js
// 从小到大排序
var arr = [10, 23, 5, 6, 7, 9, 8 ,33]
arr.sort(function (x, y) {
  if (x < y) {
      return -1; // 把小的数放前面
    }
  if (x > y) {
      return 1; // 把大的数放后面
  }
  return 0;
})
console.log(arr) // [5, 6, 7, 8, 9, 10, 23, 33]

// 从大到小排序
var arr = [10, 23, 5, 6, 7, 9, 8 ,33]
arr.sort(function (x, y) {
  if (x < y) {
      return 1; // 把小的数放后面
    }
  if (x > y) {
      return 1; // 把大的数放前面
  }
  return y - x
})
console.log(arr) // [33, 23, 10, 9, 8, 7, 6, 5]
```

字母的排序：

```js
var arr = ['Google', 'apple', 'Microsoft'];
var newArr = arr.sort(function (s1, s2) {
  // 忽略大小写来比较两个字符串，实际上就是先把字符串都变成大写（或者都变成小写），再比较
  x1 = s1.toUpperCase();
  x2 = s2.toUpperCase();
  if (x1 < x2) {
    return -1;
  }
  if (x1 > x2) {
    return 1;
  }
  return 0;
}); // ['apple', 'Google', 'Microsoft']
console.log(arr === newArr)  // true; sort()方法会直接对Array进行修改，它返回的结果仍是当前Array：
```



 

### 2.2 冒泡排序法

规则：遍历数组，按顺序两两进行对比，每次把最大的值往后排；

优化：

![img](file:///C:\Users\freshjn\AppData\Local\Temp\ksohtml\wps7162.tmp.jpg) 

冒泡排序法的两个优化方法：

案例

![img](file:///C:\Users\freshjn\AppData\Local\Temp\ksohtml\wps7163.tmp.jpg) 

 

优化1：J < arr.length-i;  //减少多余循环的次数，但是仍没有直接写循环次数来的方便；

优化2：用splice   // 位置交换优化：

​		// var delItem = arr.splice(j,1)[0];

​		// arr.splice(j+1,0,delItem)

​		arr.splice(j+1,0,arr.splice(j,1)[0])

 

 

**从大到小：**

**reverse属性法：将****‘从小到大的’****数组中的元素颠倒顺序，返回逆序后的数组** **console.log(arr.reverse())**

**或者将大于改为小于，两两对比，每次将最小的值往后排；**

总结:冒泡排序法:----大于：从大到小；小于:从小到大；----

 

 

### 2.3 选择排序法

规则：第一个和第二个，第二个和第三个对比，把小的往前面排

```js
var arr = [10,23,5,6,33,7,9,8];
for(var i=0;i<arr.length;i++){
  for(var j=i+1;j<arr.length;j++){
    if(arr[i] > arr[j]){
      var temp = arr[i];
      arr[i] = arr[j];
      arr[j] = temp;
    }
    console.log(arr.join());
  }
	console.log('--------------------');
}
console.log(arr);
```

 

​	![img](file:///C:\Users\freshjn\AppData\Local\Temp\ksohtml\wps7174.tmp.jpg)

 

案例：

随机点名：点击事件绑定触发的时候才执行函数，才会打印；

元素的value与innerHTML的区别；Div用 innerHTML ， input用 ID名.value;

全局作用域  的name是不能用的。一般放在window.onload function里面，避免变量命名与window的属性值出现冲突；

Tofixed(2)保留后面的2位小数， 返回的是一个字符串，修改为Number（tofixed(2)）



## 3 数组去重

### 3.1 ES5的filter方法

```js
var spread = [12, 5, 8, 8, 130, 44,130]
var filtered = spread.filter((item, idx, arr) => {
  return arr.indexOf(item) === idx;
})
// 筛选符合条件找到的第一个索引值等于当前索引值的数组
console.log('数组去重结果', filtered)
```



### 3.2 ES6的set方法

```js
var spread = [12, 5, 8, 8, 130, 44,130]
var setFun = [...new Set(spread)]
console.log('数组去重结果', setFun)
```

