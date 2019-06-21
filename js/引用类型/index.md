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
    > var list = [1,2,]//在IE8及以前浏览器中list的值会是[1,2,undefined]；其他浏览器中，list会是[1,2]。因为IE8之前版本的ECMAScript在数组字面量方面存在bug。