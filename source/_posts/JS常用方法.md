---
title: JS常用方法
date: 2019-03-15 19:54:00
tags: [js]
---
### 1. 计算js代码运行时间
```
let arr = [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16];
function shuffle(arr) {
    let n = arr.length;
    while (len) {
        let j = Math.floor(Math.random() * n--);
        [arr[j], arr[n]] = [arr[n], arr[j]];
    }
}
console.time("sort");		// 开始位置写上console.time，并且括号内传一个标识字符串
shuffle(arr);
console.timeEnd("sort");	// 结束的位置使用console.timeEnd方法，并再次把标识字符串传入
```
### 2. JSON化响应结果
```
function parseRes(res) {
    return typeof res === 'string' ? JSON.parse(res) : res;
}
```
### 3. 空判断
```
function isEmpty(data) {
    return data === null || data === undefined || typeof data === 'string' && data.trim() === '' || typeof data === 'object' && Object.keys(data).length < 1;
}
```
<!--more-->
### 4. js小数加减
```
function accAdd(arg1, arg2) {
    if (!isNumber(arg1) || !isNumber(arg2)) {
        return 0;
    }

    let r1, r2, m, c;
    try {
        r1 = arg1.toString()
            .split('.')[1].length;
    } catch (e) {
        r1 = 0;
    }
    try {
        r2 = arg2.toString()
            .split('.')[1].length;
    } catch (e) {
        r2 = 0;
    }
    c = Math.abs(r1 - r2);
    m = Math.pow(10, Math.max(r1, r2));
    if (c > 0) {
        let cm = Math.pow(10, c);
        if (r1 > r2) {
            arg1 = Number(arg1.toString()
                .replace('.', ''));
            arg2 = Number(arg2.toString()
                .replace('.', '')) * cm;
        } else {
            arg1 = Number(arg1.toString()
                .replace('.', '')) * cm;
            arg2 = Number(arg2.toString()
                .replace('.', ''));
        }
    } else {
        arg1 = Number(arg1.toString()
            .replace('.', ''));
        arg2 = Number(arg2.toString()
            .replace('.', ''));
    }
    return (arg1 + arg2) / m;
}
```
### 5. 小数相乘
```
function accMul(arg1, arg2) {
    if (!isNumber(arg1) || !isNumber(arg2)) {
        return null;
    }
    let m = 0, s1 = arg1.toString(), s2 = arg2.toString();
    try {
        m += s1.split('.')[1].length;
    } catch (e) {
        console.log(e);
    }
    try {
        m += s2.split('.')[1].length;
    } catch (e) {
        console.log(e);
    }
    return Number(s1.replace('.', '')) * Number(s2.replace('.', '')) / Math.pow(10, m);
}
```
### 6. 去空格及扩展
```
function trim(str, charlist) {
    //   example 1: trim('    Kevin van Zonneveld    ');
    //   returns 1: 'Kevin van Zonneveld'
    //   example 2: trim('Hello World', 'Hdle');
    //   returns 2: 'o Wor'
    //   example 3: trim(16, 1);
    //   returns 3: 6

    let whitespace, l = 0,
        i = 0;
    str += '';

    if (!charlist) {
        // default list
        whitespace =
            ' \n\r\t\f\x0b\xa0\u2000\u2001\u2002\u2003\u2004\u2005\u2006\u2007\u2008\u2009\u200a\u200b\u2028\u2029\u3000';
    } else {
        // preg_quote custom list
        charlist += '';
        whitespace = charlist.replace(/([\[\]\(\)\.\?\/\*\{\}\+\$\^\:])/g, '$1');
    }

    l = str.length;
    for (i = 0 ; i < l ; i++) {
        if (whitespace.indexOf(str.charAt(i)) === -1) {
            str = str.substring(i);
            break;
        }
    }

    l = str.length;
    for (i = l - 1 ; i >= 0 ; i--) {
        if (whitespace.indexOf(str.charAt(i)) === -1) {
            str = str.substring(0, i + 1);
            break;
        }
    }

    return whitespace.indexOf(str.charAt(0)) === -1 ? str : '';
}
```
