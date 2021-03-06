## sort

> 2018-08-14

`Array.sort`这方法一段时间不用就忘了规则是啥了。。。

先举一些最简单例子：

```js
var array = [3, 7, 2, 8, 2, 782, 7, 29, 1, 3, 0, 34]
array.sort()
// => [0, 1, 2, 2, 29, 3, 3, 34, 7, 7, 782, 8]
```

默认情况下，`sort`是按照`Unicode code points`排序的，换而言之，先回比较首个字符的 code point，若相同的情况下依次位数比下去。

所以很多时候我们需要自定义 sort 的规则。最常见的操作：

```js
const array = [3, 7, 2, 8, 2, 782, 7, 29, 1, 3, 0, 34]
array.sort((pre, next) => pre - next)
// => [0, 1, 2, 2, 3, 3, 7, 7, 8, 29, 34, 782]
```

其实它的规则很简单，你想让 next 和 pre 换位子就返回一个`>0`的值，其它情况位置不变，即返回`<=0`的值。

所以我们可以让某些特定数字排在第一位，其它顺序不变：

```js
const arr = [1, 2, 3, 4, 5]

arr.sort((p, n) => {
  return n === 3 ? 1 : 0
})
// => [3, 1, 2, 4, 5]
```
