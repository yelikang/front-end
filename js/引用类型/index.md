# 引用类型

## Object 类型

创建 Object 类型的对象有两种方式:

1. new 操作符

    > var obj = new Object();  
    > obj.name ='ylk'

2. 字面量
    > var obj = {  
    >  name:'ylk'  
    > }

## Array 类型

创建 Array 类型的对象有两种方式:

1. 使用 Array 构造函数
    > var list = new Array()  
    > var list = Array('叶立康')
2. 字面量
    > var list = ['叶立康']  
    > var list = [1,2,]//在 IE8 及以前浏览器中 list 的值会是[1,2,undefined]；其他浏览器中，list 会是[1,2]。因为 IE8 之前版本的 ECMAScript 在数组字面量方面存在 bug。

### 数组的一些方法

1. 数组检查方法

    > var list = []  
    > Array.isArray(list)//true

2. 数组的转换(将数组转换成字符串)

    > var list = [1,2,3]  
    > list.toString();//'1,2,3' toString 方法
    > list.valueOf();//'1,2,3' valueOf 方法  
    > list.join();//'1,2,3' <font color="red">join</font> 方法,将数组以什么分隔符转换成字符串，不传参数或者传 undefined 默认是‘,’逗号作为分隔符  
    > list.join('|');//'1|2|3'

3. 栈方法(栈是一种 LIFO(Last-In-First-Out 后进先出)的数据结构)，为了让数组也实现栈的功能，专门为其提供了 push()和 pop()的方法

    > var list = [];  
    > list.push(1);//[1] <font color="red">push</font> 推入  
    > list.pop();//[] <font color="red">pop</font> 移除最后一个

4. 队列方法(队列是一种 FIFO(First-In-First-Out)先进先出的数据结构)，为了让数组也实现队列的功能，可以使用 push 在数据后面添加数据，用 shift 弹出数据的第一项，实现先进先出功能
    > var list = [1];  
    > list.push(2);//[1,2] push 推入  
    > list.shift();//[2] <font color="red">shift</font> 弹出第一项,实现先进先出

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;另外,ECMAScript 还为数组提供了 unshift(...args)方法，从单词字面上理解，可以知道它的作用应该与 shift 相反，也就是在数组的头部添加任意个对象，新的数组长度作为返回值；所以利用 unshift()和 pop()方法可以在数组的反方向来模拟队列 **(在数组的头部添加对象，在尾部移除对象)**

> var list = [1];  
> list.unshift(3,2);//[3,2,1] <font color="red">unshift</font>在头部添加对象  
> list.pop();//[3,2] 在尾部移除对象

5.  排序方法
    > var list =[1,2,3,4,5]  
    > list.reverse();//[5,4,3,2,1] <font color="red">reverse</font> 方法将数组进行反转  
    > list = [0,1,5,10,15]  
    > list.sort();//[0,1,10,15,5] <font color="red">sort</font> 方法按升序进行数组的重排，但是它默认比较的是将各个项调用 toString()方法之后的字符串,而字符串'10'位于字符串'5'的签名，所以就排在它的前面
    > list.sort(compare);//[0,1,5,10,15]  sort可以接受自定义的函数作为参数，进行对比
    > function compare(value1,value2){  
    > &nbsp;&nbsp; if(vaule1<value2){  
    > &nbsp;&nbsp; return -1;  
    > &nbsp;&nbsp; }else if (value1>value2){  
    > &nbsp;&nbsp; return 1;  
    > &nbsp;&nbsp; } else {  
    > &nbsp;&nbsp; return 0  
    > &nbsp;&nbsp;}

返回-1,就是让 value1 排在 value2 前面  
返回 1，就是让 value2 排在 value1 前面  
返回 0，保持原来 value 和 value2 的位置不变  

6. 操作数组，返回新数组的方法
* concat方法  
  concat方法会在当前数组的后面加上新的数组(或单个对象)，并将添加了新数组(或单个对象)的数组作为返回值
  > var list = [1,2]
  > var list2 =  list.concat(3)// [1,2,3] 添加单个对象  
  > var list3 = list2.concat([4,5])//[1,2,3,4] 添加数组  
  > console.log(list) //[1,2] 原数组不受影响