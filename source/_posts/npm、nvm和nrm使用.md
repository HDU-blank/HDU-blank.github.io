---
title: npm、nvm和nrm使用
date: 2019-03-18 12:56:31
tags: [npm, nvm, nrm]
---
### 1. npm -- node package manage
> npm是随同NodeJS一起安装的包管理工具，能解决NodeJS代码部署上的很多问题

**Node.js安装**
从[Node.js官网](https://nodejs.org/en/)下载对应平台的安装程序
在Windows上安装时务必选择全部组件，包括勾选`Add to Path`。
安装完成后，在Windows环境下，请打开命令提示符，然后输入`node -v`，如果安装正常，可以类似的输出：

```
C:\Users>node -v
v8.11.1
```
此时npm已经在Node.js安装的时候顺带装好了。我们在命令提示符或者终端输入`npm -v`，应该看到类似的输出：
```
C:\Users>node -v
5.6.0
```
<!--more-->
### 2. nvm
> node版本管理器，可切换不同版本的node
安装方法参考网上

nvm常用命令
```
nvm ls                  // 列出所有安装的版本
nvm install             // 安装指定版本，可模糊安装
nvm use                 // 切换使用指定的版本node
nvm uninstall           // 删除已安装的指定版本，语法与install类似
nvm ls-remote           // 列出所以远程服务器的版本（官方node version list）
nvm current             // 显示当前的版本
nvm alias               // 给不同的版本号添加别名
nvm unalias             // 删除已定义的别名
nvm reinstall-packages  // 在当前版本node环境下，重新全局安装指定版本号的npm包
```
### 3. nrm
> npm下载地址的管理器，可随意切换

全局安装 nrm：
```
npm install nrm -g
```
安装完后就可以立即使用了,用`nrm ls`命令查看npm源，带*号即为当前使用的源
```
 npm ---- https://registry.npmjs.org/
 cnpm --- http://r.cnpmjs.org/
*taobao-- https://registry.npm.taobao.org/
 nj ----- https://registry.nodejitsu.com/
 npmMirror https://skimdb.npmjs.com/registry/
 edunpm - http://registry.enpmjs.or
```
nrm常用命令，其中`reigstry`为源名，`url`为源的路径
```
nrm ls                          // 查看源列表
nrm add <registry> <url>        // 增加源
nrm use <registry>              // 切换源
nrm del <registry>              // 删除源
```
