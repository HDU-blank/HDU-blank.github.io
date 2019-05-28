---
title: ES7新特性
date: 2019-05-04 15:18:23
tags: [ES7]
---

### ES7新特性
ES7在ES6的基础上主要添加了两项内容：
* Array.prototype.includes()方法
* 求幂运算符（**）

##### 1. Array.prototype.includes()方法
includes() 方法用来判断一个数组是否包含一个指定的值，根据情况，如果包含则返回 true，否则返回false。

**注意：** 对象数组不能使用includes方法来检测。
```
let array1 = [1, 2, 3];
console.log(array1.includes(2));	// true

let pets = ['cat', 'dog', 'bat'];
console.log(pets.includes('cat'));	// true

console.log(pets.includes('at'));	// false
```
<!--more-->
##### 语法
```
arr.includes(valueToFind[, fromIndex])
```
**注意：** 如果 fromIndex 大于等于数组的长度，则会返回 false，且该数组不会被搜索。

##### includes相对于indexOf的优点：
* **返回值** indexOf的返回数是值型的，includes的返回值是布尔型，在条件判断时更简单。
* **NaN的判断** indexOf无法判断NaN，而includes可以。
* **undefined的判断** 当数组的有未定义的值的时候，includes会识别undefined，而indexOf不会。
```
let arr1 = [1, 2, NaN];
console.log(arr1.indexOf(NaN))      // -1
console.log(arr1.includes(NaN))     // true

let arr2 = new Array(1);
console.log(arr2.indexOf(undefined));    // -1
console.log(arr2.includes(undefined))    // true
```

##### 2. 求幂运算符（**）
ES7中新增了求幂运算符（**）
```
2 ** 4    // 16
```
结果等同于
```
Math.pow(2, 4)
```
和加/减运算符一样，**还支持以下操作
```
let n = 2;
n **= 4;
// 16
```
