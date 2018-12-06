# js中常见的问题
## 判断数据类型
## typeof方法的重写,null是存在栈里面的是原始值，但typeof的结果却为object这是历史遗留问题,因为以前使用null替对象占位置的
```js
function type (target) {
  let arr = '[object Array]'
  let obj = '[object Object]'
  let num = '[object Number]'
  let str = '[object String]'
  let bol = '[object Boolean]'
  if (typeof (target) === 'object') {
    if (target === null) {
      console.log('this is null')
    } else if (Object.prototype.toString.call(target) === arr) {
      console.log('this is array')
    } else if (Object.prototype.toString.call(target) === obj) {
      console.log('this is object')
    } else if (Object.prototype.toString.call(target) === num) {
      console.log('this is Number object')
    } else if (Object.prototype.toString.call(target) === str) {
      console.log('this is String object')
    } else if (Object.prototype.toString.call(target) === bol) {
      console.log('this is  Boolean object')
    }
  } else console.log('this is ' + typeof (target))
}
```
## 数组去重,但只对原始值有效
```js
Array.prototype.unique = function () {
  var arr = [],
    obj = {},
    len = this.length
  for (var i = 0; i < len; i++) {
    if (!obj[this[i]]) {
      obj[this[i]] = '有值了'
      arr.push(this[i])
    }
  }
  return arr
}
```
## 快排算法,对于大量数据的排序有较大优势
### 经过测试，遍历数组时用for(i = 0; i < arr.length; i ++)的速度是高与for in 和for of的
### 同时对10000个数排序
### for(i = 0; i < arr.length; i ++) 遍历所化时间： 95.992919921875ms
### for of 所需时间 103.6181640625ms
### for in 所需时间 126.7451171875ms
```js
function sort (arr) {
  if(arr.length === 0) return [];
  // 以第中间位元素作为基准，划分数组
  let  flag = arr.splice(Math.floor(arr.length / 2), 1)[0];
  let left = [];
  let right = [];
  for(let i = 0; i < arr.length; i ++) {
    if(arr[i] < flag)
      left.push(arr[i]);
    else right.push(arr[i]);
  }
  return [...sort(left), flag, ...sort(right)];
}
```
