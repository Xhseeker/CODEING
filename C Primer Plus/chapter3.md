# 数据和C
## 主要内容
关键字 -int short long unsigned char float double  _Bool _Complex _Imaginary
运算符 _sizeof
函数 scanf（）
整数类型和浮点数类型
## 关键字
_Bool布尔类型 _Complex复数类型 _Imaginary虚数类型
- 3.16E7表示 3.16×10^7^,浮点数运算比整数运算慢，但现在很多CPU都包含浮点数计算器
- %d，10进制
- 使用printf要确保转换说明的数量和待打印值的数量相等
- 十进制数16表示成16进制是0x10，表示成八进制是020

|进制|10进制|16进制|8进制|
|---|---|---|---|
|转换说明符|%d|%x|%o|
|显示前缀|/|0x|0|
|前缀显示字符|/|%#o|%#x|
### 整数类型
1. short int （short）有符号类型
2. long int （long） 有符号类型
3. int 有符号类型，==long类型占用存储空间≥int的≥short的==
4. long long int（long long）有符号类型
---
5. unsigned int（unsigned）只用于非负值场合，16位unsigned int取值范围是0-65535
6. unsigned long
7. unsigned short
8. unsigned long long int（unsigned long long）
- 通常，long long 占64位
- long 32位
- int 16或32位
- short 16位
- 如果在long类型和int类型占用空间相同的机器上编写代码，当确实需要32位整数时，应使用long类型而不是int类型，以便把程序移植到16位机后仍然可以正常工作
- 要把一个较小的常量作为long类型对待，可以在值的末尾 ==+l或者L后缀==
- 用ll或者LL来表示long long类型的值
- 用ull或者ULL或者LLU表示unsigned long long类型的值
---
- h和l前缀都可以和u一起使用，来表示无符号类型
==unsigned 对应 %u==
==short 对应 %hd %ho==
==unsigned long 对应 %lu==
- 在给函数传递参数时，C编译器把short类型的值自动转换成int类型的值
### char类型
char用于存储字符，char类型占用空间一个字节，8bit。标准ASCII码范围0~127，只需7位二进制数
#### 字符常量初始化
``` c
char grade='A';//单引号括起来的是字符常量
char grade=65；//可以，是因为他在0~127范围内，但不好
定义一个字符常量'FATE',把它赋给char类型变量grade，只有最后8位有效
```
## 非打印字符
|转义序列|含义|
|---|---|
|`\n`|换行|
|`\r`|回车|
|`\t`|水平制表|
|`\v`|垂直制表|
|`\\`|反斜杠（\）|
|`\'`|单引号|
|`\"`|双引号|
|`\?`|?|
- `scanf("%c",&ch); 用%c对应字符`
## _Bool类型
==true 1==
false 0
_Bool是整数类型，只占用1位
## 头文件

---
limits.h

---
stdint.h
int32_t 表示整数宽度类型正好为32位

---
inttypes.h
