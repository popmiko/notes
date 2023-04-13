[toc]



# 1.定义命名空间

用到一个新的关键字namespace,这个关键字后是命名空间的名字，然后用一个{}，{}内的是命名空间的成员。

例如：
## 1.1 命名空间可以定义部分变量 也可以是一个函数

```c++
// 关键字 名字
namespace u1
{
    int a; // 一个普通的int型变量
    // 也可以是一个函数
    int add(int a,int b)
    {
        return a + b;
    }
}
```





## 1.2 命名空间可以嵌套

```c++
namespace u2
{
    // 命名空间里面也可以嵌套命名空间
    namespace u3
    {
        int d1;
        int d2;
    }
}
<<<<<<< HEAD

## 1.3
```



**同命名空间名不用文件系统会自动整合最终内容**

 **如果说同一个工程下的不同文件，都有相同的命名空间，编译器最后会将其合并**

```c++
=======
1.3 同命名空间名不用文件系统会自动整合最终内容
// 如果说同一个工程下的不同文件，都有相同的命名空间，编译器最后会将其合并


// test1.cpp
namespace u4
{
    int add(int a,int b)
        return a + b; 
}

// test2.cpp
namespace u4
{
    int mul(int a,int b)
        return a * b;
}
```



**注意： 命名空间其实相当于一个作用域，命名空间{}内的内容都是在这个空间里面，我们c++的标准库都在std这个命名空间下，**
**如果想使用c++标准库的函数，容器，需要在前面加上用std这个命名空间。**
**也可以在开头声明空间表示就不用再用std开头。**
例如 `uising namespace std；`
注：这样会直接暴露整个标准库；
也可以这样使用
例：`using namespace std::cin；`
// 最后这两个函数都是在u4这个命名空间下，不会冲突

------




# 2.命名空间的使用

##2.1直接使用

```c++
pringtf{"%d",u1::a};
namespace u1{int a;}
```



##2.2将变量或者整个命名空间展开

```c++
using namespace u1::a;
//using namespace u1;
pringtf{"%d",a};
```



# 3.输入和输出

cin cout都来源于标准库iOSstream命名空间std中，所以在进行输入输出时，要先加上展开命名空间和引入标准库

```c++
include <iostream>
using namespace std;
```



在进行输入和输出的时候，我们经常使用 << 和 >> 符号。

**例3.1.1如：cout << “ x+y = ” << 5 << endl;**

<< 是流插入运算符；>> 是流提取运算符；
例题3.1.1中的x+y=传入到cout中5传入x+y=中直到endl结束
**注意：cout和cin都为自适应参数输出和输入，但它每次只能穿入一个参数，不能一次性传入多个变量；**
**cin的分隔符号一般为enter**

------



## 3.1标准输入输出的控制符

dec 设置整数的基数为10（即多少进制输出）
hex 设置整数的基数为16
oct 设置整数的基数为8
setbase(n) 设置整数的基数为n(n只能是16，10，8之一)
setfill© 设置填充字符c，c可以是字符常量或字符变量
setprecision(n) 设置实数的精度为n位。在以一般十进制小数形式输出时，n代表有效数字。在以fixed(固定小数位数)形式和scientific(指数)形式输出时，n为小数位数。
setw(n) 设置字段宽度为n位。
setiosflags(ios::fixed) 设置浮点数以固定的小数位数显示。
setiosflags(ios::scientific) 设置浮点数以科学计数法(即指数形式)显示。
setiosflags(ios::left) 输出数据左对齐。
setiosflags(ios::right) 输出数据右对齐。
setiosflags(ios::shipws) 忽略前导的空格。
setiosflags(ios::uppercase) 在以科学计数法输出E和十六进制输出字母X时，以大写表示。
setiosflags(ios::showpos) 输出正数时，给出“+”号。
resetiosflags 终止已设置的输出格式状态，在括号中应指定内容。

##3.2输出格式的输出
precision(n) setprecision(n) 设置实数的精度为n位。
width(n) setw(n) 设置字段宽度为n位。
fill© setfill© 设置填充字符c。
setf( ) setiosflags( ) 设置输出格式状态，括号中应给出格式状态，内容与控制符setiosflags括号中内容相同。
ubsetf( ) resetiosflags( ) 终止已设置的输出格式状态。

## 3.3cin的进一步使用

（1）cin>>等价于cin.operator>>()，即调用成员函数operator>>()进行读取数据。
（2）当cin>>从缓冲区中读取数据时，若缓冲区中第一个字符是空格、tab或换行这些分隔符时，cin>>会将其忽略并清除，继续读取下一个字符，若缓冲区为空，则继续等待。但是如果读取成功，字符后面的分隔符是残留在缓冲区的，cin>>不做处理。
（3）不想略过空白字符，那就使用 noskipws 流控制。比如cin>>noskipws>>input;
cin.get():该函数有有多种重载形式，分为四种格式：无参，一参数，二参数，三个参数。常用的的函数原型如下：

``` c++
int cin.get();
istream& cin.get(char& var);
istream& get ( char* s, streamsize n );
istream& get ( char* s,  streamsize(c语言中的long long)  n, char delim );
```



### 3.3.1

读取一行可以使用istream& get ( char* s, streamsize n )或者istream& get ( char* s, size_t n, streamsize delim )。二者的区别是前者默认以换行符结束，后者可指定结束符。n表示目标空间的大小。
注：cin.get cin.getline 区别在于get会将分隔符也输入缓存区。

``` c++
getline()重载方式:
istream& getline ( istream& is, string& str);//默认以换行符结束
istream& getline ( istream& is, string& str, char delim);
```



### 3.3.2

在输入时缓存区未读取完会造成输入异常，可以通过clear清除异常状态。
同样的cin.ignore(numeric_limits< std::streamsize>::max()); 会清除cin中所以的内容。

# 4.常量指针

c++中使用const来定义常量。const可以与指针一起使用，它们的组合情况复杂，可归纳为3种：指向常量的指针、常指针和指向常量的常指针。
指向常量的指针：一个指向常量的指针变量。

## 4.1指向常量的指针

const char* pc = "abcd";
该方法不允许改变指针所指的变量，即
    pc[3] = ‘x';   是错误的，
但是，由于pc是一个指向常量的普通指针变量，不是常指针，因此可以改变pc所指的地址，例如
    pc = "ervfs";
该语句付给了指针另一个字符串的地址，改变了pc的值。
常指针：将指针变量所指的地址声明为常量

## 4.2常指针

`char* const pc = "abcd";`
创建一个常指针，一个不能移动的固定指针，可更改内容，如
    `pc[3] = 'x';`
但不能改变地址，如
    `pc = 'dsff'`;  不合法

## 4.3指向常量的常指针

指向常量的常指针：这个指针所指的地址不能改变，它所指向的地址中的内容也不能改变。
const char* const pc="abc";

**1.如果用const定义整型常量，关键字可以省略。即 const int bufsize = 100 与 const bufsize = 100等价；**
=======
**1.如果用const定义整型常量，关键字可以省略。即 const in bufsize = 100 与 const bufsize = 100等价；**


**2.常量一旦被建立，在程序的任何地方都不能再更改。**
**3.与#define不同，const定义的常量可以有自己的数据类型。**
**4.函数参数也可以用const说明，用于保证实参在该函数内不被改动**。

====

=======
注意事项：
1.如果用const定义整型常量，关键字可以省略。即 const in bufsize = 100 与 const bufsize = 100等价；
2.常量一旦被建立，在程序的任何地方都不能再更改。
3.与#define不同，const定义的常量可以有自己的数据类型。
4.函数参数也可以用const说明，用于保证实参在该函数内不被改动。

