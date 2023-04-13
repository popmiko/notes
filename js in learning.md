# 学习JavaScript学习笔记

[toc]

## 1.最基本的输出

**alert**("hello new man");//弹窗输入
document.write("hello new bog"); //作为body在HTML文件中输入
console.log("hello new bog,this is console"); //在控制台中输出

## 2.变量声明中let、var、const的区别

###2.1var

var使用var声明的变量，其作用域为整个script函数中，且存在变量提升现象；
举例说明var声明变量为全局变量

```javascript
for(var i=0;i<=10;i++){ 
var sum=0; 
sum+=i; 
} 
console.log(sum);//10
 变量提升
 console.log(a);//Uncaught ReferenceError: a is not defined  
 a = 1;  
 不进行用var声明，没有被提升到最前面，直接报错
 console.log(b);//undefined  
 var b = 2;  // var声明将var b=2解析为var b；b=2;并将var b提升到最前面，所以在出现时为空赋值，只是开辟了空间。

```



### 2.2let

let拥有块级作用域,一个{}就是一个作用域，也就是let声明块级变量，即局部变量；
 let在其作用域下面不存在变量提升；
 let在其作用域中不能被重复声明(函数作用域和块级作用域)；

### 2.3const

const用来声明常量，一旦声明，其值就不可以更改，而且必须初始化。如果你非得修改变量的值，js不会报错，只是默默表示失败(不起作用)。
