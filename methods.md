# Array

{% method %}
## find

find方法，用于找出第一个符合条件的数组成员。如果没找到符合条件的成员就返回underfind

{% sample lang="js" %}
找出第一个大于2的成员

```js
[1, 2, 3, 4].find(n => n > 2) // 3
``` 

## findIndex

findIndex方法，用于找出第一个符合条件的数组成员的索引。

{% sample lang="js" %}
第一个大于2的成员的索引

```js
[1, 2, 3, 4].findIndex(n => n > 2)// 2
```

## includes

includes方法，用于某个数组是否包含给定的值，返回一个布尔值。如果没找到符合条件的成员就返回underfind

{% sample lang="js" %}

```js
[1, 2, 3].includes(2) // true
[1, 2, 3].includes(5) // false
[1, 2, NaN].includes (NaN)// true
```



