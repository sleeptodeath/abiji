### 01.c语言开发环境配置
* 
* linux 安装gcc/g++

* windows 安装MinGW

* gcc 进行 c 语言编译分为四个步骤：
    * 常用：gcc [源文件名] -o [目标文件名]  
        例如：gcc test.c -o test.out
    1. 预处理，生成预编译文件（.i 文件）：  
        gcc –E hello.c –o hello.i
    2. 编译，生成汇编代码（.s 文件）：  
        gcc –S hello.i –o hello.s
    3. 汇编，生成目标文件（.o 文件）：  
        gcc –c hello.s –o hello.o
    4. 链接，生成可执行文件：  
        gcc hello.o –o hello
|
### 02.c语言的基本语法元素
```C
#include <stdio.h>  //头文件
|
int main(int argc, char *argv[]) {
    // parameter
    system("pause");      //仅限windows，暂停函数，请按任意键继续...
    return 0;
}
```
* 标识符
    * 由字母、数字和下划线组成。
    * 第一个字符必须是字母表中字母或下划线 _ 。
    * 区分大小写。
    * 不能用关键字
    * 标识符命名应做到"见名知意"

* 关键字

| 关键字      |    说明  |
|:--------|:----------|
auto	|声明自动变量|
break	|跳出当前循环|
case	|开关语句分支|
char	|声明字符型变量或函数返回值类型|
const	|声明只读变量|
continue	|结束当前循环，开始下一轮循环|
default	|开关语句中的"其它"分支|
do	|循环语句的循环体|
double	|声明双精度浮点型变量或函数返回值类型|
else	|条件语句否定分支（与 if 连用）|
enum	|声明枚举类型|
extern	|声明变量或函数是在其它文件或本文件的其他位置定义|
float	|声明浮点型变量或函数返回值类型|
for	|一种循环语句|
goto	|无条件跳转语句|
if	|条件语句|
int	|声明整型变量或函数|
long	|声明长整型变量或函数返回值类型|
register	|声明寄存器变量|
return	|子程序返回语句（可以带参数，也可不带参数）|
short	|声明短整型变量或函数|
signed	|声明有符号类型变量或函数|
sizeof	|计算数据类型或变量长度（即所占字节数）|
static	|声明静态变量|
struct	|声明结构体类型|
switch	|用于开关语句|
typedef	|用以给数据类型取别名|
unsigned	|声明无符号类型变量或函数|
union	|声明共用体类型|
void	|声明函数无返回值或无参数，声明无类型指针|
volatile	|说明变量在程序执行中可被隐含地改变|
while	|循环语句的循环条件|
* 注释
    1. /**/     多行注释 不能嵌套注释
    2. //       单行注释
* 预处理命令  
    #include<stdio.h>
* main函数  
    int main(int argc, char *argv[]) {   
        return 0;  
    }|
* 分号 ；
| A       |    B      |     c   |
|:--------|:----------|:------- |
a|b|c
