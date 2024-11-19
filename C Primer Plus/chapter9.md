
<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [函数](#函数)
  - [主要内容](#主要内容)
  - [声明、定义、调用](#声明-定义-调用)
    - [函数定义](#函数定义)
    - [函数类型](#函数类型)
    - [函数声明](#函数声明)
  - [递归-函数调用自己](#递归-函数调用自己)
  - [编译多源代码文件的程序](#编译多源代码文件的程序)
  - [指针简介](#指针简介)

<!-- /code_chunk_output -->


# 函数
## 主要内容
关键字return * & 函数 参数和返回值 指针用于函数参数 递归
## 声明、定义、调用
>> void starbar(void);
第一个void是函数类型，void函数类型表明函数没有返回值
第二个void表明函数不带参数
---
>>starbar();这是调用void类型函数的一种形式
程序把starbar()和main（）放在一个文件中，也可以把它们分别放在两个文件中
---
>starbar（）函数中的变量count是局部变量，该变量只属于starbar（）函数。
可以在程序中其他对方（包括main（）函数中）使用count，这不会引起名称冲突，它们是同名不同变量。
---
>和定义在函数内的变量一样，形式参数也是局部变量，属于函数私有
---
> void show_n_char(char ch,int num)
虽然接受main（）的值，但它没有返回值，所以类型是void
---
### 函数定义
```c
void show_n_char(char ch,int num)
void show_n_char(char,int)
```
被调函数的值是从主调函数中拷贝过来的，所以无论被调函数对拷贝数据进行什么操作，都不会影响主调函数中的原始数据
```c
int imin(int n,int m)
{
    int min;

    return min;
}
因为返回的min是int类型的变量，所以imin函数的类型也是int
```
- 返回值不仅可以赋给变量，也可以被用作表达式的一部分
- 如果函数返回值是double类型的1.1525，函数的类型是int，则返回值是1
- 若return在printf（）之前执行，会导致printf（）语句永远也不会执行
- ```return;```这条语句会导致终止函数，只有在void函数中才会用到这种形式，或者不写return
### 函数类型
- 声明函数必须声明函数的类型，带返回值的函数类型应该与其返回值类型相同，而没有返回值的类型应该声明为void类型
- 函数类型是指的其返回值类型，不是参数类型
- sqrt返回double类型
### 函数声明
```c
void show_n_char(char ch,int num)；
void show_n_char(char,int)；
```
- 为了表明函数确实没有参数，应该在圆括号内使用void
```c
int printf(const char *,...);
C库通过stdarg.h定义（形参数量不固定的）函数的方法
```
## 递归-函数调用自己
- 如果递归代码中没有终止递归的条件测试部分，一个调用自己的函数会无限递归
- %p  对应  &n
- 递归 先进后出，后进先出
---
- 假设有一条函数调用链——fun1（）调用fun2（）、fun2（）调用fun3（）、fun3（）调用fun4（）。当fun4（）结束时，控制传回fun3（），当fun3（）结束时，控制传回fun2（），当fun2（）结束时，控制传回fun1()
---
1. 每级函数调用都有自己的变量
2. 每次函数调用都会返回一次
3. 递归函数中位于递归调用之前的语句，均按被调函数的顺序执行
4. 递归函数中位于递归调用之后的语句，均按被调函数相反的顺序执行
5. 递归函数必须包含能让递归调用停止的语句。通常，递归函数都使用if或其他等价的测试条件在函数形参等于某特定值时终止递归
---
```c
//循环
for(ans=1;n>1;n--)
    ans*=n;
//递归
if(n>0)
    ans=n*rfact(n-1);
else
    ans=1;
```
- 递归可以提供简单的算法，缺点是会快速消耗计算机自愿，不方便阅读和维护
- 所以的C函数皆平等，都可以调用其他函数或者被其他函数调用
## 编译多源代码文件的程序
- UNIX cc file1.c file2.c
  cc file1.c file2.o
- LINUX gcc file1.c file2.c
- DOS .obj
- WINDOWS集成开发环境编译器面向项目，==把函数原型和已定义的字符常量放在头文件==
- #include "hotel.h"，双引号代表当前工程目录
- ``scanf("%*s");``跳过一个字符串
## 指针简介
- 指针，值为内存地址的变量
- `ptr=&pooh;   ptr指向pooh，ptr是变量，&pooh是常量`
- 间接运算符，val=*ptr；*后跟一个指针名或地址时，*给出存储在指针指向地址上的值
- 声明指针int *pi；char *pc；float *pf，*pg；
- 在声明时用空格，在解引用变量时省略空格
- void interchange(int *u,int *v)
- void interchange(int *u,int *v)；
- function1（&x）；
- int function1（int * ptr）
- scanf（"%d",&num）scanf读取一个值，把值存储到指定的地址上

