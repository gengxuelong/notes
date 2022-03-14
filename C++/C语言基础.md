C语言基础

## 第一天： helloworld

诞生时间是1971年

### 计算机硬件介绍

服务器90%都是拿C写的。利用高速度优点

黑客用的也是C语言，很少的用汇编语言

CPU（中央处理器）： 运算器，控制器，寄存器

CPU运算的数据来自于内存（内存储器）

内存和硬盘的本质是一样的，不过内存的读取和存储的速度快。

CPU运算的数存在寄存器中。

#### 计算机系统的组成

- 硬件系统

  - 主机

    - 中央处理器
      - 运算器
      - 控制器

    - 内存器
      - 只读存储器（ROM）
      - 随机存储（RAN)

  - 外部设备

    - 输入设备
    - 输出设备
    - 外存储器

- 软件系统

  - 系统软件
    - 操作系统
    - 语言处理系统
    - 系统服务程序
    - 数据库管理系统
  - 应用软件
    - 文字处理软件
    - 表格处理器
    - 辅助设计软件
    - 实时控制系统

Java80%的库都是拿C语言封装的

### C语言的关键字

32个关键字

1. auto 
2. break
3. case 
4. char
5. const
6. continue
7. default
8. do
9. couble 
10. else
11. enum
12. extern
13. float
14. for
15. goto
16. if
17. int
18. long
19. register
20. return 
21. short
22. signed
23. sizeof
24. static 
25. struct
26. switch
27. typedef
28. unsigned
29. union
30. void 
31. volatile
32. whil

9中控制语句

1. if  else
2. for 
3. while 
4. do    while
5. continue
6. break
7. switch
8. goto
9. return

34中运算符：

1. 算术运算符(7)：+ - * /   %   ++   --
2. 关系运算符(6)：<   <=  ==  >  >=  !=
3. 逻辑运算符(3)： !     &&    ||  
4. 位运算符(6)：<<    >>    ~    |    ^    &  
5. 赋值运算符  ： =
6. 条件运算符（三目运算符）：？  ： 
7. 都好运算符：,
8. 指针运算符： *   &  
9. 求字节数运算符： sizeof
10. 强制类型转换运算符： （）
11. 分量运算符(2)：  .     ->
12. 下标运算符： []
13. 其他： （  ）  

### 第一个程序：

```c
//# 表示引入头文件，include是引入头文件的关键字
//stdio.h 是系统标准输入、输出对应的头文件，给printf服务的
//<>表示使用系统库的函数，自己写的库用双引号""
#include <stdio.h>
//int 表示函数返回值；main表示一个函数名，是程序的唯一入口，必须有且只能又一次
//void指，函数调用无需传参
int main(void)
{
    //\n是回车换行
    printf("hello world\n");
    //调用system函数，实现暂停功能
    system("pause");
    retrun 0;
}
```

> 解决小黑框一闪而过的问题：（vs)
>
> 原因： 闪黑框是因为在执行printf()语句，黑框消失是因为执行return 0 语句
>
> 解决：
>
> 1.  在return 0 前添加：system（“pause")
>
> 2.  更改VS的设置，让他在控制台打印，具体方法百度解决

（第八个视频起始）

### 记事本helloworld

新建一个记事本文件，将扩展名改为.c

点击打开，打开方式仍为记事本

在记事本中书写代码：

```c
#include<stdio.h>
int main(void){
    printf("hello world\n");
    return 0;
}
```

如何运行这个C语言文件，这就要借助gcc编译工具

：在文件夹里，点击并选中目录，输入cmd，就会进入该文件目录的命令行

输入：

> gcc -v

判断是否有编译工具

编译语句：

> gcc helloworld.c -o helloworld.exe

回车后，当前目录就会多出一个helloworld.exe 文件。这个就是可执行二进制文件

然后，在命令行里输入：helloworld.exe按回车键就可以运行了

> .obj 文件，汇编文件

gcc.exe 在minGW 的bin目录中。该bin目录也已经放在path环境变量了

### 总结helloworld的写法

两种编写helloworld的方法

1. 借助VS编辑工具编写
2. 借助记事本，gcc编译工具编写

## system函数

system函数： 执行系统命令（命令均为字符串）

如：

- pause： 暂停
- cmd ： 开启命令行
  - 所在位置为当前.c 文件所在的目录
- calc : 调用计算器
- mspaint:  画图工具
- nodepad:  记事本
- cls :  清屏命令，清理命令行或者console界面

```c
#include <stdio.h>
#include <Windows.h>
int main(void){
    println("-------hello world\n");
    Sleep(2000);
    system("cls");
    return 0;
}
```

#### 休眠函数

>  Sleep(2000): 休眠函数
>
> 在：  Windows.h 头文件里

#### 注释：

1. //   单行注释
2. /*    */   多行注释

### gcc编译4步骤

hello.c  -------->hello.exe

>  gcc hello.c -o hello.exe   （**-o重命名的意思**）

其中的四个步骤：

1. 预处理
2. 编译
3. 汇编
4. 链接

hello.c   预处理后 (-E)  得： hello.i (预处理文件)

hello.i   编译  (-S)         得： hello.s(汇编文件)

hello.s    汇编  (-c)      得 ： hello.o 文件（目标文件，二进制，但不可直接运行）

hello.o   链接(无参数)     得  ： hello.exe

![](D:\截图\C++\QQ截图20220121225027.png)

> gcc  -E hello.c  -o  hello.i
>
> gcc  -S hello.i -o hello.s
>
> gcc -c hello.s -o hello.o
>
> gcc hello.o  -o hello.exe

###  午后回顾

####  编写C语言代码：hello.c 

```c
#include <stdio.h>
int main(void){//void可以不写
    printf("hello world");
    return 0;
    /*
    这是多行注释
    */
}
```

#### system 函数的介绍

参数：为系统命令

#### gcc 命令

-v   查看版本

-o  重命名

##### 注释

#### Sleep（）函数。

在Windows.h中

#### gcc编译四步骤

1. 预处理 -E      .i   预处理文件
2. 编译   -S        .s  汇编文件
3. 汇编    -c         .o  目标文件
4. 链接    无         .exe  可执行文件 

### 预处理

> gcc  -E  hello.c  -o hello.i

预处理文件：将头文件展开，不检查语法错误，也就是说可以展开任何文件

```c
#include <sss.txt>
int main(void){
    printf("niaho");
    return 0;
}

gcc -E hello.c -o hello.i -I.
会发现预处理文件只是我乱写的sss.txt 文件和hello.c 正文的结合拼接
    -I.  是指明sss.txt 在.c文件所在牡目录，用于指明位置
```

 预处理做的事：

1. 头文件展开（不检查语法错误）
2. 宏定义的替换---将宏名替换成宏值
3. 替换注释----将注释替换成了空行
4. 展开条件编译----更具宏定义将结果展示出来，根据条件来展开指令

```c
#include <stdio>

#define PI 3.24
int main(void){
    printf("hello world");
    #ifdef  PI 
    printf("------------666\n");
    #endif//条件编译
    printf("%d\n",PI);
    //我是一个单行注释
    /*
    我是一个多行注释
    */
}
```

### 编译：

> gcc -E  hello.i -o hello.s

得到一个汇编语言

干的事：

1. 将C语言翻译成汇编语言
2. 在编译过程，会逐行检查语法错误【重点】，整个流程中最耗时的

### 汇编：

> gcc -c hello.s -o hello.o

二进制的文件，打开显示时以16进制的形式显示

做的事：

1. 翻译，将汇编指令翻译成对应的二进制编码

### 链接

> gcc  hello.o   -o  hello.exe

做的事：

1.  数据段的合并
2. 数据地址回填
3. 库引入
   - 引入第三方库，比如stdio.h 就对应了一个库，得把第三方库导进来才能运行

### gcc编译四步骤总结

预处理：

- 展开头文件
- 展开宏定义
- 替换注释
- 展开条件编译

编译：

- 逐行检查语法锁雾
- 翻译成汇编语言

汇编：

- 翻译成二进制机器指令

链接

- 数据段合并
- 数据地址回填
- 库引用

**注意**：

> 可以跨步骤运行，被跨的步骤默认调用相应指令，但只得到相应得一个结果

### Windows程序依赖dll库

在链接的时候需要引入库，Windows系统中所有的库都是以.dll结尾的

在资料中depend.exe 软件可以查看一个.c文件都要依赖那些dll库，直接将.c 文件拖入该程序的界面中间就行了

### 汇编和加法运算

#### CPU:内部结构与寄存器：

寄存器是CPU内部最基本的存储单元

CPU对外是通过总线来和外界设备进行交互的，总线的宽度是32位，同时寄存器也是32位的，那么这个CPU就是32位的CPU

如果一种CPU内部的寄存器是64,位的， 但总线是32位的，那么成为准64位CPU

所有的64位的CPU兼容32位的指令

如果在64Wie的CPU架构上运行64位的软件操作系统，那么这个系统就是64位的

在64位的CPU架构上，运行32位的软件操作系统，那么这个系统解释32位的

64位的软件不能运行在32位的CPU上

#### 寄存器。缓存和内存之间的信息

缓存是内存和寄存器之间的一个设置，用于一些经常操作内存中统一地址的数据

#### 汇编语言

C语言中可以嵌套汇编语言

```c
#include <stdio.h>
int main(void)
{
    int a = 3;
    int b = 5;
    int c ;
    c = a+ b;
    printf("%d\n",c);
   
}


#include <stdio.h>
int main(void)
{
    int a;
    int b;
    int c;
    _asm
    {
        mov a,3//3的值放在a 对应的内存位置
        mov b,4//4的值放在b对应的内存位置
        mov eax,a//把a的值放入eax寄存器
        add eax,b//eax和b相加，结果放入eax
        mov c,eax;//eax的值放入c中
    }
    printf("%d\n",c);
   
}
```

### printf的格式化输出

> printf("%d\n",c);
>
> printf("c = %d\n",c);
>
> printf("%d + %d = %d\n",a,b,a+b);

### 编写程序中常见的错误

语法的错误：编译器会提示

- 中文标点符号
- 写错字符

逻辑错误

- 得调试

### VS下的调试

1. 设置断点，开始调试
2. 指向的行还没有执行
3. '逐语句'按钮：会进入函数内部，进行逐条语句跟踪
4. 添加监视：调试：-》窗口-》监视窗口
   - 监视器需要自己写要监视的变量
5. '逐过程'按钮：不仅如此函数内部
6. '跳出'按钮：跳出进入函数内的标识点 
7. vs有对应性的反汇编功能:
   - 调试-》窗口-》反汇编

> QT creator 也是一个IDE

## 第二天，变量与数据类型

### 复习：

第一个程序：

```c
#include <stdio.h>
int main(){
    
    printf("hello world\n");
    return 0;
}
```

格式化打印：

```c
printg("%d + %d =%d",10,5,10+4);
```

gcc编译四步骤

- 预处理
- 编译
- 汇编
- 链接

### 常量和圆的周长和面积

C的三十二个关键字：

- 数据类型关键字：
  - char short int long float double unsigned  signed  struct  union  enum  void 
- 控制语句关键字
  - if  else  switch   case   defult  for   do  while   break   continue   goto   return 
- 存储类型的关键字
  - auto  extern   register   static   const    
- 其他关键字：
- sizeof   typedef   volatile

常量：

#### 不会变化的数据

1. "hello"   ----->字符串常量

   - 'A'  ---------->

   - -10

   - 3.1415

2. #define  PI 3.1415

   - 宏定义，PI为宏定义常量

3. const int a  = 10;

   - const关键字，被该关键字修饰的变量为只读变量。不推荐以这种方式定义常量，推荐宏定义的方式。应为用const 定义的常量可以借助指针把值改掉

```c
#include <stdio.h>

#define PI 3.1415//宏定义语句不以分号结尾

int main(void){
    //圆的面积
    //圆的周长
    int r = 3;
    
    float s = PI * r * r;
    float l = 2 * PI * r;
    
    printf("圆的周长为:%f\n",l);
    printf("圆的面积为:%f\n",s);
    
    //指定小数点后两位，并对第三位进行四舍五入
    printf("圆的周长为:%.2f\n",l);
    printf("圆的面积为:%.2f\n",s);
    
}
```

### 变量总结

1. 宏定义不以分号结尾

2. %.2f 中需要四舍五入

### 变量和内存存储

变量：会变化的数据

定义的语法：

> 类型名   变量名  =  变量值；

变量三要素：类型名  变量名  变量值（缺一不可）

定义个一个变量后：int r = 3;

在内存中开辟一个空间：

里面放的一个3，这个空间有个名字叫 人，同时有一个唯一标识的地址值

空间的大小由类型决定

### 变量和变量声明

int a;没有变量值得变量定义，叫做变量声明

extern int a; 带有extern的声明

声明不开辟内存空间

当编译器编译程序是，在变量使用之前，必须看到变量定义，如果没有边浪定义，编译器会自动寻找一个变量声明提升为定义

如果该变量的声明前有extern关键字，则无法提升

标识符是变量和常量的总称

```c
#include <stdio.h>

int main(void){
    int a = 40;
    a = 56;
    return 0;
}

int main(){
    a = 56;//报错，未找到标识符
    int a = 40;
}
int main(){
    int a;
    a = 56;
}
int main(){
    extern int a;
    a = 56;//报错，无法解释尾部符号a
    return 0;	
}
```

建议： 定义变量时，尽量不要重名。

### 标识符

标识符是变量和常量的总称

#### 命名规则：

1. 通常 常量使用大写，变量使用小写，大小写严格区分
2. 只能使用数数字，字母，下划线命名标识符，且数字不能开头
3. 禁止使用关键字和系统函数作为标识符

### 整型变量

int a ;

1. int 类型
2. short 类型
3. long类型
4. long long 类型
   - long long llen = 70;

### sizeof关键字

sizeof不是函数，他是一个关键字。但用法和函数差不多

```c
printf("%d\n",sizeof(short));//2字节
printf("%d\n",sizeof(int));//4字节
printf("%d\n",sizeof(long));//4字节
printf("%d\n",sizeof(long long));//8字节
```

int size = sizeof(int);

printf("%d\n",size);

int a = 20;

int size = sizeof(a);

printf("%d\n",size);

### 问题总结

1. 定义宏常量
   - #define N1024
2. 定义变量
   - int a = 10;

### sizeof总结：

- 不是函数，用来求一个变量、类型的大小
- sizeof(类型名)
- sizeof(变量名)
- 了解： 括号可以去掉，，sizeof  a;

### 无符号整型

一般的整型都是有符号整型。：signed int

无符号整型：unsigned int；；；unsigned short；；unsigned long；；unsigned long long

无符号整型： 只表示数据量，而没有方向（正负）

```c
int main(){
    int a = 3;
    short b = 4;
    long c = 5;
    long long d = 6;
    printf("sizeof(int) = %d\n",sizeof(int));
    printf("----------");
    unsigned int aun = 3;
    unsigned short bun = 4;
    unsigned long cun = 5;
    unsigned long long dun = 6;
    printf("sizeof(unsigned int) = %d\n",sizeof(unsigned int));
}
```

关于long ：

> Windows系统中：32 和64 位操作系统都是4字节
>
> Linux系统时，32位的是4字节，64位的是8字节

### 无符号数据的格式匹配符：

- 有符号
  - int         %d
  - float       **%hd**
  - long           %ld
  - long long   %lld
- 无符号
  - unsigned int %u
  - unsigned float **%hu**
  - unsigned long  %lu
  - unsigned long long   %llu

long c = 5;//将一个int类型的常量值赋值给long型变量c

long c  = 5L ;long c = 5l;//将一个long型的常量值赋值给long型的变量c

long long c = 5LL;5ll

unsigned int aun = 3u;//无符号int类型的常量

unsigned long bun = 3lu;

unsigned long long dun = 6llu;

### 午后复习：

#### 常量：

不会变化的数据，不好能被修稿

- 数值常量
- 宏定义常量
- 只读变量const

#### 变量：

会变化的数据。能被修改

变量声明，

变量定义

变量三要素

定义语法

建议：定义变量时，尽量不要重名

#### 标识符：

变量和常量的统称

命名规则

#### sizeof关键字：

不是函数

#### 有符号整型

#### 无符号整型

：只表示数据值，不表示方向

### 无符号数据类型的使用

unsigned int a = 10u;//可以不加u，加上更标准

unsigned short b = 20u;

unsigned long c = 30Lu;

unsigned long long d = 40LLu;

printf("unsigned int 型数据值为：%u/n",a);

unsigned short :%hu

unsigned long :%lu

unsigned long long :%llu

sizeof 关键字 不是函数，所以不需要保函任何头文件，他的功能就是计算一个数据类型的大小，单位为字节

sizeof的返回值为size_t，

size_t类型在32 位操作系统下是unsigned int ，是一个无符号整数

### 字符类型。

char，

存储一个字符

用带引号引起来的单字符称作一个字符

格式匹配符：%c

> int  main(){
>
> char ch = 'A';
>
> printf("ch = %c\n",ch);
>
> ch = 97;
>
> printf("che = %c\n",ch);//打印a
>
> ch = 'a' ;
>
> printf("%d\n",ch);//打印97
>
> }
>
> 大小写转换
>
> int main(){
>
> char ch= 'M';
>
> printf("%c\n",ch + 32);
>
> }

 'A'  : 65

'a' : 97

'0' : 48

'\n' : 10

'\0' : 0     -------\0 作为字符串结束的方式，无显示内容

>printf("'\n'的值为%d",'\n');//   \n 真的起到了换行的作用二我们的需求确实输出'\n'

转义字符：'\'

将特使字符转为特殊意，将特殊字符转为本身意

> printf("'\ \\n'的值为%d",'\n');

\\  \ 就是将特殊意的字符转为普通意

### 实型：float double

浮点数，小数

float 单进度浮点型     4字节

double：双精度浮点型   8字节

常数小数某人是double类型

> float m = 3.145;
>
> double n = 4.344332;
>
> printf("%f\n",m);
>
> printf("%f\n",n); 
