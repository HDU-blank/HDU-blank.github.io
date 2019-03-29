---
title: git 切换到指定的tag处代码
date: 2019-03-22 13:16:39
tags: [git]
---

### 1. git 切换到分支上指定tag处的代码

支持 push，pop，top，size，clear 操作，并能在常数时间内检索到最小元素的栈。

- push(x) -- 将元素 x 推入栈中。
- pop() -- 删除栈顶的元素。
- top() -- 获取栈顶元素。
- size() -- 获取栈深度（大小）。
- clear() -- 清空栈元素。
- getMin() -- 检索栈中的最小元素。

<!--more-->
  #### JS代码实现

  ```
  /**
   * initialize your data structure here.
   */
  var LinkedList = function() {
      var Node = function (element) {		// 新元素构造
          this.element = element;
          this.next = null; 				//指向链表中下一个节点项的指针
      };
  };

  /**
   * @param {number} x
   * @return {void}
   */
  MinStack.prototype.push = function(x) {
      this.array.push(x);
      if (this.minArray.length === 0 || x <= this.minArray[this.minArray.length-1]) {
          this.minArray.push(x);
      }
  };

  /**
   * @return {void}
   */
  MinStack.prototype.pop = function() {
      let item = this.array.pop();
      if (item === this.minArray[this.minArray.length-1]) {
          this.minArray.pop();
      }
      return item;
  };

  /**
   * @return {number}
   */
  MinStack.prototype.top = function() {
      return this.array[this.array.length - 1];
  };

  /**
   * @return {number}
   */
  MinStack.prototype.size = function() {
      return this.array.length;
  };

  /**
   * @return {void}
   */
  MinStack.prototype.clear = function() {
      this.array = [];
      this.minArray = [];
  };

  /**
   * @return {number}
   */
  MinStack.prototype.getMin = function() {
      return this.minArray[this.minArray.length-1];
  };

  /**
   * Your MinStack object will be instantiated and called as such:
   * var obj = new MinStack();
   * obj.push(x);
   * obj.pop();
   * var param_3 = obj.top();
   * var param_4 = obj.getMin();
   */
  ```

### 2. JS构建顺序栈

支持 push，pop，top，size，clear 操作，并能在常数时间内检索到最小元素的栈。

- push(x) -- 将元素 x 推入栈中。
- pop() -- 删除栈顶的元素。
- top() -- 获取栈顶元素。
- size() -- 获取栈深度（大小）。
- clear() -- 清空栈元素。
- getMin() -- 检索栈中的最小元素。

<!--more-->
  #### JS代码实现

  ```
  /**
   * initialize your data structure here.
   */
  var MinStack = function() {
      this.array = [];
      this.minArray = [];
  };

  /**
   * @param {number} x
   * @return {void}
   */
  MinStack.prototype.push = function(x) {
      this.array.push(x);
      if (this.minArray.length === 0 || x <= this.minArray[this.minArray.length-1]) {
          this.minArray.push(x);
      }
  };

  /**
   * @return {void}
   */
  MinStack.prototype.pop = function() {
      let item = this.array.pop();
      if (item === this.minArray[this.minArray.length-1]) {
          this.minArray.pop();
      }
      return item;
  };

  /**
   * @return {number}
   */
  MinStack.prototype.top = function() {
      return this.array[this.array.length - 1];
  };

  /**
   * @return {number}
   */
  MinStack.prototype.size = function() {
      return this.array.length;
  };

  /**
   * @return {void}
   */
  MinStack.prototype.clear = function() {
      this.array = [];
      this.minArray = [];
  };

  /**
   * @return {number}
   */
  MinStack.prototype.getMin = function() {
      return this.minArray[this.minArray.length-1];
  };

  /**
   * Your MinStack object will be instantiated and called as such:
   * var obj = new MinStack();
   * obj.push(x);
   * obj.pop();
   * var param_3 = obj.top();
   * var param_4 = obj.getMin();
   */
  ```

  ​

  ​
