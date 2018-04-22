
- [1 创建方法](#1-创建方法)
- [2 字符串的方法](#2-字符串的方法)
- [2.1 字符串遍历](#21-字符串遍历)
- [2.2 字符串的查找方法](#22-字符串的查找方法)
- [2.3 字符串分割/拆分](#23-字符串分割/拆分)
- [2.4 字符串的截取方法](#24-字符串的截取方法)
- [2.5 字符串大小写转换](#25-字符串大小写转换)
- [2.6 其它](#26-其它)

## 1 创建方法

```js
//方式一：字面量（推荐）
var str = '城市套路深，我想回农村';

//方式二：构造函数
//PS：用new操作符产生的变量都是引用类型的变量，也叫对象
var str = new String('我不是黄蓉，我不会武功');
```



## 1 字符串的方法

字符串方法总结5个常用

replace(‘旧’,’新’)替换;split()转换成数组;slice()字符串截取; toLowerCase()小写;toUpperCase()大写;trim()过滤空格



### 2.1 字符串遍历

for循环



### 2.2 字符串的查找方法

1.indexOf

注意：索引值的位置是获取第一个字符所在的索引值；

技巧: .indexOf(‘a’)!=-1或者>=0都表明该字符存在的;该方法经常用来检查字符中的存在感;

```js
var name = '"a", "b"';
// 存在返回0以及以上的数字索引值，不存在则返回-1
var indexName = name.indexOf('c');
console.log(indexName) // -1
```



2.Replace replace(str|rgExp,’‘) 替换字符串
这里的替换只能执行一次，不能够进行全局匹配，如果需要全局匹配，则应使用正则表达式

```js
var name = '"a", "b"';
// 双引号替换为单引号
var replaceName = name.replace(/"([^"]*)"/g, "'$1'");
console.log(replaceName) // ''a', 'b''
```



其他方法:

1. lastIndexOf
2. search(str|regExp)
3. match(str|regExp)

### 2.3 字符串分割/拆分

转成数组的方法split;

split(‘分割符’)：根据分割字符，把字符串拆分成数组

作用：split会将分割的字符串转成数组； 感觉与其叫做分割还不如叫作转换;…..

注意:Split(‘’) 如果中间什么都没写,为空, 就代表每个字符都分割;

```js
var name = 'heightzhang, name, hobby'
var splitName = name.split()
console.log(splitName) // ["heightzhang, name, hobby"]
```



### 2.4 字符串的截取方法

slice(start,end) ：截取start到end(不包括end)的字符串，**支持负数(与substring的区别) **常用;

```js
var s = 'hello, world'
s.slice(0); // 从索引0开始到5（不包括5），返回'hello'
s.slice(7); // 从索引7开始到结束，返回'world'
```



slice支持负数，从右往左边数数；

常用在截掉最后一位标点符号,注意截取后要重新赋值给原来的元素

```js
var name = '"a", "b",';
// ,从右往左数为-1
var sliceName = name.slice(0, -1);
console.log(sliceName) // "a", "b"
```

易错混淆点:split ;字符串转成数组; slice 数组和字符串的截取; splice 数组的添加或删除;join，数组转字符串；


### 2.5 字符串大小写转换

toLowerCase()：转换成小写

toUpperCase()：转换成大写



### 2.6 其它

str[3]： //通过下标获取字符串;

trim()：删除前后所有空格，返回新的字符串 适用在用户名注册的时候过滤空格

格式: _usename =_usename.trim()

```js
var name = ' heightzhang '
var trimName = name.trim()
console.log(trimName) // 'heightzhang'
```





