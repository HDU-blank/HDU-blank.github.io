---
title: CSS常用小技巧
date: 2019-03-14 19:36:00
tags: [css]
---
### 1. 溢出文字...展示
text-overflow用来标记溢出内容如何显示，并不能强制文字溢出，要想让此属性生效，必须设置
```
{
    text-overflow: ellipsis;
    overflow:hidde;
    white-space:nowrap;
}
```
并且元素必须是块状元素
```
{
    display:block; //inline-block;
}
```
<!--more-->
<br>
### 2. 高度自适应分割竖线
最近做到一个需求：两个div中间加条分割竖线，在高度上需要自动占满整个父div(即这条竖线的高度和两个div中较高的一个等高)。
##### 实现思路：
在两个子div中加多一个div，并设置左（右）边框为可见，并且利用padding-bottom|margin-bottom正负值相抵消的原理。<br>
例如设置 `padding-bottom:1600px`,`margin-bottom:-1600px`<br>
我们可以理解为：运用的是**padding可以撑开外层标签而margin不用来撑开外层标签**。即当padding-bottom时撑开外层标签的高度,外层标签用overflow:hidden;隐藏掉多余的高，这样可以让高度与最高的那一栏对齐；**而margin关乎模块布局，margin可以抵消掉padding撑开的盒子,使布局能够从内容部分开始**。
##### CSS代码
```
.middle-line{     // 父div需要设置overflow:hidden;
    float:left;
    width:10px;
    border-left: 1px dashed @primary-color;
    padding-bottom:1600px;  /*关键*/
    margin-bottom:-1600px;  /*关键*/
}
```
