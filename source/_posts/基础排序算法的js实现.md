---
title: 八种基础排序算法的js实现
date: 2018-03-06 11:05:00
tags: [js, 排序]
---
### 1、快速排序
```
function quickSort(arr){
  //如果数组<=1,则直接返回
  if(arr.length<=1){
    return arr;
  }
  var pivotIndex=Math.floor(arr.length/2);
  //找基准，并把基准从原数组删除
  var pivotkey=arr.splice(pivotIndex,1)[0];
  //定义左右数组
  var left=[];
  var right=[];
  //比基准小的放在left，比基准大的放在right
  for(var i=0;i<arr.length;i++){
      if(arr[i]<=pivotkey){
          left.push(arr[i]);
      }
      else{
          right.push(arr[i]);
      }
  }
  //递归
  return quickSort(left).concat([pivotkey],quickSort(right));
}
var elements=[55,45,62,8,12,7,4,65,3,98];
quickSort(elements);
```
<!--more-->
### 2、简单排序
```
function simpleSort(arr){
    console.time('排序耗时');
    for(var i=0;i<arr.length;i++){
        var min=arr[i];
        var index=i;
        for(var j=i+1;j<arr.length;j++){
            if(arr[j]<min){
                min=arr[j];
                index=j;
            }
        }
        if(index!=i){
            arr[index]=arr[i];//arr.splice(index,1,arr[i]);
            arr[i]=min;//arr.splice(i,1,min);
        }
    }
    console.timeEnd('排序耗时');
    return arr;
}
var array=[55,45,62,8,12,7,4,65,3,98];
simpleSort(array);
```
### 3、直接插入排序
```
function insertSort(arr){
    console.time('排序耗时');
    for(var i=0;i<arr.length;i++){
        for(var j=i;j>0;j--){
            if(arr[j]<arr[j-1]){
                var min=arr[j];
                arr[j]=arr[j-1];//arr.splice(j,1,arr[j-1]);
                arr[j-1]=min;//arr.splice(j-1,1,min);
            }
        }
    }
    console.timeEnd('排序耗时');
    return arr;
}
var array=[55,45,62,8,12,7,4,65,3,98];
insertSort(array);
```
### 4、冒泡排序
```
function bubbleSort(arr){
    console.time('排序耗时');
    for(var i=arr.length-1;i>0;i--){
        for(var j=1;j<=i;j++){
            while(arr[j-1]>arr[j])
            {
                var min=arr[j];
                arr[j]=arr[j-1];//arr.splice(j,1,arr[j-1]);
                arr[j-1]=min;//arr.splice(j-1,1,min);
            }
        }
    }
    console.timeEnd('排序耗时');
    return arr;
}
var array=[55,45,62,8,12,7,4,65,3,98];
bubbleSort(array);
```
### 5、希尔排序
```
var mid=Math.floor(array.length/2);
function shellSort(arr,m){
    console.time('排序耗时');
    for(var i=m-1;i<arr.length;i++){
        for(var j=i;j>m-1;j-=m){
            if(arr[j]<arr[j-m]){
                var min=arr[j];
                arr[j]=arr[j-m];//arr.splice(j,1,arr[j-m]);
                arr[j-m]=min;//arr.splice(j-m,1,min);
            }
        }
    }
    var s_array=arr;
    var s_mid=m;
    if(s_mid==1){
        console.timeEnd('排序耗时');
        return array;
    }else {
        return shellSort(s_array,Math.floor(s_mid/2));
    }
}
var array=[55,45,62,8,12,7,4,65,3,98];
shellSort(array,mid);
```
### 6、归并排序
```
function mergeSort(array){
  if(array.length == 1) return array;
  /* 首先将无序数组划分为两个数组 */
  var mid = Math.floor(array.length / 2);
  var left = array.slice(0, mid);
  var right = array.slice(mid);
  /* 递归分别对左右两部分数组进行排序合并 */
  return merge(mergeSort(left), mergeSort(right));
}


function merge(left, right) {
  var re=[];
  while(left.length>0&&right.length>0)
  {
    if(left[0]<right[0])
    {
      re.push(left.shift());
    }
    else
    {
      re.push(right.shift());
    }
  }
  /* 当左右数组长度不等.将比较完后剩下的数组项链接起来即可 */
  return re.concat(left).concat(right);
}

var array = [23, 47 ,81 ,95 ,7, 14, 39, 55, 62, 74]
mergeSort(array);
```
### 7、堆排序
```
//调整函数
function headAdjust(elements, pos, len){
  var swap=elements[pos];
  var child=pos*2+1;
  while(child<len){
    if(child+1<len&&elements[child+1]>elements[child]){
      child+=1;
    }
    if(elements[pos]<elements[child]){
        elements[pos]=elements[child];
        pos=child;
        child=pos*2+1;
    }
    else{
      break;
    }
    elements[pos]=swap;
  }
}

//构建堆
function buildHeap(elements){
  /*从最后一个拥有子节点的节点开始，将该节点连同其子节点进行比较，将最大的数交换与该节点,交换后，再依次向前节点进行相同交换处理，直至构建出大顶堆（升序为大顶，降序为小顶）*/
  for(var i=elements.length/2; i>=0; i--){
    headAdjust(elements, i, elements.length);
  }
}

function heapSort(elements){
  console.time('排序耗时');

  buildHeap(elements);

  //从数列的尾部开始进行调整
  for(var i=elements.length-1; i>0; i--){
    //堆顶永远是最大元素，故，将堆顶和尾部元素交换，将最大元素保存于尾部，并且不参与后面的调整
    var swap = elements[i];
    elements[i] = elements[0];
    elements[0] = swap;

    //进行调整，将最大）元素调整至堆顶
    headAdjust(elements, 0, i);
  }
  console.timeEnd('排序耗时');
}

var elements=[55,45,62,8,12,7,4,65,3,98];
heapSort(elements);
console.log(' after: ' + elements);
```
### 8、基数排序
```
function baseSort(array){
  var maxNum=0;
  var countArray=[];
  var bits=0;
  countArray=steArray();
  for(var i=0;i<array.length;i++){
    if(maxNum<array[i]){
      maxNum=array[i];
    }
  }
  while (maxNum>0) {
    bits+=1;
    maxNum=Math.floor(maxNum/10);
  }
  for(var posNum=1;posNum<=bits;posNum++){
    for(var i=0;i<array.length;i++){
      var index=get_num_pos(array[i],posNum);
      countArray[index].push(array[i]);
    }
    array=steamroller(countArray);
    countArray=steArray();
  }
  return array;
}

function steamroller(arr) {
  var newArr=[];
  for(var i=0;i<arr.length;i++){
  if(Array.isArray(arr[i])){
     newArr=newArr.concat(steamroller(arr[i]));
  }
    else {
      newArr.push(arr[i]);
    }
}
  return newArr;
}

function steArray(){
  for(var j=0;j<10;j++){
  countArray[j]=new Array();
  }
  return countArray;
}

function get_num_pos(num,pos){
  return (parseInt(num/Math.pow(10,(pos-1))))%10;
}

var array=[55,45,62,8,12,7,4,65,3,98,5];
baseSort(array);
```
