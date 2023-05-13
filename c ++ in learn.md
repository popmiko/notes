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

## 3.2字符串的输入

### 3.2.1cin.ge

cin.get(字符数组名，接收字符数)用来接收一行字符串，可以接收空格

cin.get(无参数)没有参数主要是用于舍弃输入流中的不需要的字符,或者舍弃回车,弥补cin.get(字符数组名,接收字符数目)的不足

```c++
#include <iostream>
using namespace std;
 
int main(void)
{
     
    char arr[10];
    cin.get(arr,10);
    cin.get();//用于吃掉回车，相当于getchar();
    cout<<arr<<endl;
    cin.get(arr,5);
    cout<<arr<<endl;
    system("pause");
    return 0;
}
 
输入abcdefghi
输出abcdefghi
输入abcde
输出abcd
请按任意键继续

```

### 3.2.2getline()

getline() // 接受一个字符串，可以接收空格并输出，需包含“#include<string>”

```c++
string str;
getline(cin,str);
cout<<str<<endl;

输入：jkljkljkl //VC6中有个bug,需要输入两次回车。
输出：jkljkljkl
//和cin.getline()类似，但是cin.getline()属于istream流，而getline()属于string流，是不一样的两个函数
```



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



### 3.3.1使用get方法输入字符串

读取一行可以使用istream& get ( char* s, streamsize n )或者istream& get ( char* s, size_t n, streamsize delim )。二者的区别是前者默认以换行符结束，后者可指定结束符。n表示目标空间的大小。
注：cin.get cin.getline 区别在于get会将分隔符也输入缓存区。

``` c++
getline()重载方式:
istream& getline ( istream& is, string& str);//默认以换行符结束
istream& getline ( istream& is, string& str, char delim);
```

### 3.3.2cin使用注意事项

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
注意事项：
1.如果用const定义整型常量，关键字可以省略。即 const in bufsize = 100 与 const bufsize = 100等价；
2.常量一旦被建立，在程序的任何地方都不能再更改。
3.与#define不同，const定义的常量可以有自己的数据类型。
4.函数参数也可以用const说明，用于保证实参在该函数内不被改动。

## 4.4 sizeof的注意事项

```c++
#include <iostream>
using namespace std;
int sum(int arr[]){
	int length = sizeof(arr)/sizeof(arr[0]);
    int sum = 0;
    for (int i = 0 ; i < length; i++){
        sum += arr[i];
    }
    return sum;
}
int main(){
    int arr[] = {1,3,5,7,9};
    //cout<<sizeof(arr)/sizeof(int);
    //使用'sizeof' on array function parameter 'a' will return size of 'int*' [-Wsizeof-array-argument]
    int summary = sum(arr);
    cout << summary << endl;
}

```

注意：数组作为参数传给函数时，是传给数组的地址，而不是传给整个的数组空间，因而sizeof(arr)这句话会报错.

# 5.类的定义

  C++中使用关键字 **class** 来定义类, 其基本形式如下:

```cpp
class 类名
{
    public:
        //公共的行为或属性
    private:
        //私有的行为或属性 类内的属性无法被外部d
};
//在外部继续写class内的方法
 类名::方法名(  )
 {
   
 }
```

说明:
     ①. 类名 需要遵循一般的命名规则;
     ②. **public** 与 **private** 为属性/方法限制的关键字, private 表示该部分内容是私密的, 不能被外部所访问或调用, 只能被本类内部访问; 而 public 表示公开的属性和方法, 外界可以直接访问或者调用。
       一般来说类的属性成员都应设置为private, public只留给那些被外界用来调用的函数接口, 但这并非是强制规定, 可以根据需要进行调整;
     ③. 结束部分的分号不能省略。

## C++类的实现

   在上面的定义示例中我们只是定义了这个类的一些属性和方法声明, 并没有去实现它, 类的实现就是完成其方法的过程。类的实现有两种方式, 一种是在类定义时完成对成员函数的定义, 另一种是在类定义的外部进行完成。
   1>. 在类定义时定义成员函数
     成员函数的实现可以在类定义时同时完成, 如代码:

```cpp
#include <iostream>
using namespace std;
class Point
{
    public:
        void setPoint(int x, int y) //实现setPoint函数
        {
            xPos = x;
            yPos = y;
        }
        void printPoint()       //实现printPoint函数
        {
            cout<< "x = " << xPos << endl;
            cout<< "y = " << yPos << endl;
        }
    private:
        int xPos;
        int yPos;
};
int main()
{
    Point M;        //用定义好的类创建一个对象 点M
    M.setPoint(10, 20); //设置 M点 的x,y值
    M.printPoint();     //输出 M点 的信息
    return 0;
}
```

运行输出:

```
	x = 10
  y = 20
```

与类的定义相比, 在类内实现成员函数不再是在类内进行声明, 而是直接将函数进行定义, 在类中定义成员函数时, 编译器默认会争取将其定义为 inline 型函数 2>. 在类外定义成员函数
     在类外定义成员函数通过在类内进行声明, 然后在类外通过作用域操作符 **::** 进行实现, 形式如下:

```
返回类型 类名::成员函数名(参数列表)
{
     //函数体
}
```



```cpp
#include <iostream>
using namespace std;
class Point
{
    public:
        void setPoint(int x, int y); //在类内对成员函数进行声明
        void printPoint();
    private:
        int xPos;
        int yPos;
};
void Point::setPoint(int x, int y) //通过作用域操作符 '::' 实现setPoint函数
{
    xPos = x;
    yPos = y;
}
void Point::printPoint()       //实现printPoint函数
{
    cout<< "x = " << xPos << endl;
    cout<< "y = " << yPos << endl;
}
int main()
{
    Point M;        //用定义好的类创建一个对象 点M
    M.setPoint(10, 20); //设置 M点 的x,y值
    M.printPoint();     //输出 M点 的信息
    return 0;
}
```

依 setPoint 成员函数来说, 在类内声明的形式为 **void setPoint(int x, int y);** 那么在类外对其定义时函数头就应该是 **void Point::setPoint(int x, int y)** 这种形式, 其返回类型、成员函数名、参数列表都要与类内声明的形式一致。

## 对象的作用域、可见域与生存周期

   类对象的作用域、可见域以及生存周期与普通变量的保持相同, 当对象生存周期结束时对象被自动撤销, 所占用的内存被回收, 需要注意的是, 如果对象的成员函数中有使用 **new** 或者 ***\*malloc\**** 申请的动态内存程序不会对其进行释放, 需要我们手动进行清理, 否则会造成内存泄露。

学不会了，时间来不及，不学了。
