# 分支和跳转
## 主要内容
关键字 if、else、switch、continue、break、case、default、goto 
关系运算符 && || ？：
getchar() putchar() ctype.h
## if else
```c
if(expression)
    statement1
else
    statement2
```
## getchar() putchar()
```c
ch=getchar();           scanf("%c",&ch);
putchar(ch);            printf("%c",ch);
都定义在stdio.h文件中
while((ch=getchar())!='\n')
{

}
putchar()接受int类型的参数，这个函数根据最后一个字节确定显示哪个字符
```
## ctype.h的系列字符函数
|字符测试函数|功能|
|---|---|
|isalpha()|字母|
|isdigit()|数字|

|字符映射函数|功能|
|---|---|
|tolower()|如果是大写字符，该函数返回小写字符；否则返回原始参数|
|toupper()|否则返回原始参数|
```c
tolower(ch);//不影响ch的值
ch=tower(ch);//把ch转换成小写字母
```
## else和if配对
==如果没有花括号，else和离它最近的if配对，除非离它最近的if被花括号括起来==
`for(div=2,isPrime=true ; (div*div)<=num ; div++);`
`for(div=2,isPrime=true ; div<根号下num ; div++);`
## 逻辑运算符
&&  ||   ！
优先级   ！  大于   &&    大于  ||
求值顺序    C保证逻辑表达式的求值顺序是从左往右。&&和||运算符都是序列点，所以程序从一个运算对象执行到下一个运算对象之前，所有副作用都会生效
`if(range>=90 && range<=100)`
经典例题[^1]
[^1]:单词统计程序
## 条件运算符?:
`expression ? expression2 : expression3`
## continue和break
- continue语句，会跳过本次迭代的剩余部分，并开始下一轮迭代。如果continue语句在嵌套循环内，则只会影响内层循环。
```c
while(getchar()!='\n')
    continue;//循环读取并丢弃输入的数据，直到遇到换行符；跳过输入剩余部分

while((ch=getchar())!='\n')
{
    if(ch=='\t')
        continue;
    putchar(ch);
}//意思是跳过制表符，并遇到换行符时退出循环

while((ch=getchar())!='\n')
{
    if(ch!='\t')
    putchar(ch);
}//这样更清楚，把if测试条件反过来可避免使用continue

```
### continue何处开始继续循环
- 对于while和do while，执行完continue语句后的下一个行为是对循环的测试表达式求值
- 对于for语句，执行continue后，先对 ==更新表达式求值，再对循环测试表达式求值==
### break
- 若break位于嵌套循环内，只会影响包含它的当前循环
- 执行完break语句后会直接执行循环后面的第一条语句，连更新部分也跳过。
- 嵌套循环内层的break只会让程序跳出内层循环，想跳出外层循环，还需要一个break
## switch和break
- break可以用在循环和switch语句中，但continue只能用在循环中
```c
switch(整型表达式)
{
    case 常量1:
        语句
    case 常量2:
        语句
    default :
        语句
}
```
```c
//多重case标签
switch(整型表达式)
{
    case 'A'
    case 'a':语句
            break;

    case 'B'
    case 'b':语句
            break;
    default :
        语句
}
```
### 何时用switch
有限可列整型数(或者char类型也可以)
## goto语句
- 出现问题时从一组嵌套循环中跳出（一条break语句只能跳出当前循环）
```c
以下语句在三层嵌套循环中
if(问题)
    goto help;
以上语句在三层嵌套循环中


循环外 help: 语句
```
