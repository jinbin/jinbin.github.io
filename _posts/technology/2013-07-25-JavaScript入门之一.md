---
layout: page
title: JavaScript入门之一
category: 技术
tags: Javascript
---
{% include JB/setup %}

####JS数据类型
#####五种基本类型： 

- Null   
- Undefined  声明变量但不赋值
- Boolean  有对应的对象类
- Number  有对应的对象类
- String  有对应的对象类

#####操作符：

== ：'12' == 12 true  
=== ：'12' === 12 false  

####函数
#####两种定义方法：  
var fn = function{  
     // ...  
}  
function fn(){  
     // ...  
}  

#####获取传递给函数的实际参数：
arguments   
arguments.callee  
     
#####匿名函数

####对象
var obj = new Object();  
obj.name = "jinbin";  
obj.age = 26;  

var obj = {  
   name : "jinbin";  
   age : 26;  
};  

function Person(name,age){    
  this.name = name;  
  this.age = age;  
  
  this.showName = function(){  
     alert(this.name);  
   }  
}  

