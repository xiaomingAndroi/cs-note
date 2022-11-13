# 初识C语言

## 什么是C语言





![image-20220924115255521](D:\ALQF\Typora图片\image-20220924115255521.png)

![image-20220924115459896](D:\ALQF\Typora图片\image-20220924115459896.png)

> C语言是一门通用计算机编程语言，广泛应用于底层开发。C语言的设计目标是提供一种能以简易
> 的方式编译、处理低级存储器、产
> 生少量的机器码以及不需要任何运行环境支持便能运行的编程语言。
> 尽管C语言提供了许多低级处理的功能，但仍然保持着良好跨平台的特性，以一个标准规格写出的
> C语言程序可在许多电脑平台上进
> 行编译，甚至包含一些嵌入式处理器（单片机或称MCU）以及超级电脑等作业平台。
> 二十世纪八十年代，为了避免各开发厂商用的C语言语法产生差异，由美国国家标准局为C语言制
> 定了一套完整的美国国家标准语
> 法，称为ANSI C，作为C语言最初的标准。 [1] 目前2011年12月8日，国际标准化组织（ISO）和
> 国际电工委员会（IEC）发布的C11
> 标准是C语言的第三个官方标准，也是C语言的最新标准，该标准更好的支持了汉字函数名和汉字
> 标识符，一定程度上实现了汉
> 字编程。
> C语言是一门面向过程的计算机编程语言，与C++，Java等面向对象的编程语言有所不同。
> 其编译器主要有Clang、GCC、WIN-TC、SUBLIME、MSVC、Turbo C等。

## 第一个C语言程序

![image-20220924115944845](D:\ALQF\Typora图片\image-20220924115944845.png)

```c
#include <stdio.h>
int main()
{
printf("hello bit\n");
printf("he he\n");
return 0;
}
//解释：
//main函数是程序的入口
//一个工程中main函数有且仅有一个
```





## 数据类型

double a;
scanf("%f",&a); //应用scanf("%lf",&a);
执行上面语句时，发现double类型的输入不能使用%f进行输入，得用%lf才能正常得到a的值。
而在输出double类型时却可以用%f，这是因为printf("%f",a);在执行时C自动将float型的参数转换成double型。

故double型的输入输出形式如下：

double a;
scanf("%lf",&a);
printf("%f",a);

```c
char //字符数据类型
short //短整型
int //整形
long //长整型
long long //更长的整形
float //单精度浮点数
double //双精度浮点数
//C语言有没有字符串类型？
```

### 占用字节数

```c
int main()
{
printf("%d\n", sizeof(char));
printf("%d\n", sizeof(short));
printf("%d\n", sizeof(int));
printf("%d\n", sizeof(long));
printf("%d\n", sizeof(long long));
printf("%d\n", sizeof(float));
printf("%d\n", sizeof(double));
printf("%d\n", sizeof(long double));
return 0;
```

![image-20221001003147521](D:\ALQF\Typora图片\image-20221001003147521.png)

> long占用的字节可能是4，可能是8，在64位机下就是8

![image-20221001005054556](D:\ALQF\Typora图片\image-20221001005054556.png)

int是4个字节，能表达2^32-1的范围。4294967296，一共10位数

![image-20221001004226945](D:\ALQF\Typora图片\image-20221001004226945.png)

short int 是2个字节，能表达2^16-1的范围。即65535。

*short* *int*简写为*short* 

![image-20221001004237381](D:\ALQF\Typora图片\image-20221001004237381.png)

### float和double的区别

小数默认double.如果使用float表示小数，用95.6f这种类型表示。

![image-20221001004824218](D:\ALQF\Typora图片\image-20221001004824218.png)

![image-20221001004717847](D:\ALQF\Typora图片\image-20221001004717847.png)

## 变量、常量

### 变量

C语言中的常量和变量的定义的形式有所差异。
C语言中的常量分为以下以下几种：

- 字面常量
- const 修饰的常变量
- #define 定义的标识符常量
- 枚举常量

#### 定义变量的方法

![image-20221001010535575](D:\ALQF\Typora图片\image-20221001010535575.png)

#### 变量的分类

- 局部变量
- 全局变量

```c
#include <stdio.h>
int global = 2019;//全局变量
int main()
{

//下面定义的global会不会有问题？
int global = 2020;//局部变量
printf("global = %d\n", global);
return 0;
```

> 上面的局部变量global变量的定义其实没有什么问题的！
> 当局部变量和全局变量同名的时候，局部变量优先使用

#### 变量的使用

```c
#include <stdio.h>
int main()
{
int num1 = 0;
int num2 = 0;
int sum = 0;
printf("输入两个操作数:>");
scanf("%d %d", &num1, &num2);
sum = num1 + num2;
printf("sum = %d\n", sum);
return 0;
}
//这里介绍一下输入，输出语句
//scanf
//print
```

#### 变量作用域和生命周期

- 作用域

> 作用域（scope）是程序设计概念，通常来说，一段程序代码中所用到的名字并不总是有效/可用
> 的
> 而限定这个名字的可用性的代码范围就是这个名字的作用域。

1. 局部变量的作用域是变量所在的局部范围。
2. 全局变量的作用域是整个工程。

- 生命周期

> 变量的生命周期指的是变量的创建到变量的销毁之间的一个时间段

1. 局部变量的生命周期是：进入作用域生命周期开始，出作用域生命周期结束。

2. 全局变量的生命周期是：整个程序的生命周期

#### extern关键字的

这也是一个全局变量

![image-20221001011003755](D:\ALQF\Typora图片\image-20221001011003755.png)

如何在test.c用呢？

![image-20221001011057802](D:\ALQF\Typora图片\image-20221001011057802.png)

### 常量

C语言中的常量和变量的定义的形式有所差异.

C语言中的常量分为以下以下几种:

- 字面常量
- const 修饰的常变量
- #define 定义的标识符常量
- 枚举常量



```c
#include <stdio.h>
//举例
enum Sex
{
MALE,
FEMALE,
SECRET
};
//括号中的MALE,FEMALE,SECRET是枚举常量
int main()
{
//字面常量演示
3.14;//字面常量
1000;//字面常量
    
//const 修饰的常变量
const float pai = 3.14f; //这里的pai是const修饰的常变量
pai = 5.14;//是不能直接修改的！
    
//#define的标识符常量 演示
#define MAX 100
printf("max = %d\n", MAX);
    
//枚举常量演示
printf("%d\n", MALE);
printf("%d\n", FEMALE);
printf("%d\n", SECRET);
//注：枚举常量的默认是从0开始，依次向下递增1的


```

#### const修饰的常变量



注：

> 上面例子上的 pai 被称为 const 修饰的常变量， const 修饰的常变量在C语言中只是在语法层面限制了
> 变量 pai 不能直接被改变，但是 pai 本质上还是一个变量的，所以叫常变量。

如何证明？这说明n是变量，但是具有常属性(n的值不能被改变)。

![image-20221001011918420](D:\ALQF\Typora图片\image-20221001011918420.png)

#### enum修饰的枚举类型

![image-20221001012253824](D:\ALQF\Typora图片\image-20221001012253824.png)

![image-20221001012455240](D:\ALQF\Typora图片\image-20221001012455240.png)

## 字符串、转义字符、注释

### 字符串

```c
"hello bit.\n"
```

![image-20221001012632611](D:\ALQF\Typora图片\image-20221001012632611.png) 

 这种由双引号（Double Quote）引起来的一串字符称为字符串字面值（String Literal），或者简称字符
串。

#### \0的作用

  注：字符串的结束标志是一个 \0 的转义字符。在计算字符串长度的时候 \0 是结束标志，不算作字符串
内容。

![image-20221001012753560](D:\ALQF\Typora图片\image-20221001012753560.png)

![image-20221001012920380](D:\ALQF\Typora图片\image-20221001012920380.png)

```c
#include <stdio.h>
//下面代码，打印结果是什么？为什么？（突出'\0'的重要性）
int main()
{
char arr1[] = "bit";//默认会有 \0
char arr2[] = {'b', 'i', 't'};
char arr3[] = {'b', 'i', 't'， '\0'};
char arr4[] = {'b', 'i', 't'， 0};//和 3 是一样的
printf("%s\n", arr1);//
printf("%s\n", arr2);//
printf("%s\n", arr3);//
return 0;
}
```

#### \0不算字符串内容

第二种其实是个随机值。因为找不到\0

![image-20221001013246838](D:\ALQF\Typora图片\image-20221001013246838.png)

![image-20221001013351986](D:\ALQF\Typora图片\image-20221001013351986.png)

### 转义字符

加入我们要在屏幕上打印一个目录： c:\code\test.c

\t  就是 tab.

```c
#include <stdio.h>
int main()
{
printf("c:\code\test.c\n");
return 0;
}
```

![image-20221001013520859](D:\ALQF\Typora图片\image-20221001013520859.png)



#### 三字母词

![image-20221001013846192](D:\ALQF\Typora图片\image-20221001013846192.png)

![image-20221001013746472](D:\ALQF\Typora图片\image-20221001013746472.png)

![image-20221001013804227](D:\ALQF\Typora图片\image-20221001013804227.png)

![image-20221001013811253](D:\ALQF\Typora图片\image-20221001013811253.png)

#### \ \表示一个反斜杠，防止被解释为一个转义序列符

\t 会被转义成 tab ,那么\ \t就会防止解释为转义序列符。

![image-20221001014109100](D:\ALQF\Typora图片\image-20221001014109100.png)

#### 想打印' '怎么办

![image-20221001014240623](D:\ALQF\Typora图片\image-20221001014240623.png)

![image-20221001014313989](D:\ALQF\Typora图片\image-20221001014313989.png)

![image-20221001014326750](D:\ALQF\Typora图片\image-20221001014326750.png)

#### \32(\ddd)是什么意思？

![image-20221001014632942](D:\ALQF\Typora图片\image-20221001014632942.png)

![image-20221001014715077](D:\ALQF\Typora图片\image-20221001014715077.png)

#### \\(xdd)

![image-20221001014820463](D:\ALQF\Typora图片\image-20221001014820463.png)

![image-20221001014835015](D:\ALQF\Typora图片\image-20221001014835015.png)



## 操作符

简单介绍为主，后面课件重点讲。

### 算术操作符

```c 
    +
    - 
    * 
    /:取整
    %:取模(取余数)
```

输出1

![image-20221001103555843](D:\ALQF\Typora图片\image-20221001103555843.png)

### 移位操作符

```c
>> ：右移：x2
<< ：左移：/2
```

![image-20221001103725561](D:\ALQF\Typora图片\image-20221001103725561.png)

### 位操作符

```c
    & ：按位与 (有一个为假，则为假的)
    ^ ：按位异或(相同则为0，不同则为1)
    | ：按位或(有一个为真，则为真的)
```

![image-20221001104139669](D:\ALQF\Typora图片\image-20221001104139669.png)

![image-20221001104214707](D:\ALQF\Typora图片\image-20221001104214707.png)

![image-20221001104321008](D:\ALQF\Typora图片\image-20221001104321008.png)

### 赋值操作符

```c
    = 
    += ：加等
    -= ：减等
    *= ：乘等
    /= ：除等 
    &= ：与等 
    ^= ：异或等 
    |= ：或等 
    >>= ：右移等 
    <<= ：左移等
```

### 单目操作符

只跟一个操作数的，叫做单目操作符。&a  (取a地址)

跟两个操作数的，叫双目操作符。a+b.  a&b;(a与b)

```c
! 逻辑反操作
- 负值
+ 正值
& 取地址
sizeof 操作数的类型长度（以字节为单位）
~ 对一个数的二进制按位取反
-- 前置、后置--
++ 前置、后置++
* 间接访问操作符(解引用操作符)
(类型) 强制类型转换
```

#### sizeof省略左括号

![image-20221001105957709](D:\ALQF\Typora图片\image-20221001105957709.png)

![image-20221001110051436](D:\ALQF\Typora图片\image-20221001110051436.png)

#### ~ 按位取反(原，反，补)

![image-20221001112105703](D:\ALQF\Typora图片\image-20221001112105703.png)

![image-20221001110834370](D:\ALQF\Typora图片\image-20221001110834370.png)

![image-20221001111048510](D:\ALQF\Typora图片\image-20221001111048510.png)

```c
#include<stdio.h>
int main() {
	int a = 0;
	int b = ~a;
	printf("%d", b);
}
```

### 关系操作符

```c
>
>=
<
<=
!= 用于测试“不相等”
== 用于测试“相等”
```

### 逻辑操作符

```c
&& 逻辑与
|| 逻辑或
```

#### &&

![image-20221001111533444](D:\ALQF\Typora图片\image-20221001111533444.png)

### ||

![image-20221001111549842](D:\ALQF\Typora图片\image-20221001111549842.png)

### 条件操作符

```c
exp1 ? exp2 : exp3
```

![image-20221001111626078](D:\ALQF\Typora图片\image-20221001111626078.png)

### 逗号表达式

```c
exp1, exp2, exp3, …expN
```



### 下标引用、函数调用和结构成员

```c
[] () . ->
```



## 常见关键字

```c
auto break case char const continue default do double else enum
extern float for goto if int long register return short signed
sizeof static struct switch typedef union unsigned void volatile while
```

###  typedef

> typedef 顾名思义是类型定义，这里应该理解为类型重命名

```c
//将unsigned int 重命名为uint_32, 所以uint_32也是一个类型名
typedef unsigned int uint_32;
int main()
{
//观察num1和num2,这两个变量的类型是一样的
unsigned int num1 = 0;
uint_32 num2 = 0;
return 0;
}
```



### static

> 在C语言中：
> static是用来修饰变量和函数的
> 1. 修饰局部变量-称为静态局部变量
> 2. 修饰全局变量-称为静态全局变量
> 3. 修饰函数-称为静态函数

#### 修饰全局变量

```c
//代码1
//add.c
int g_val = 2018;
//test.c
int main()
{
    extern int g_val;
	printf("%d\n", g_val);
	return 0;
}
//代码2
//add.c
static int g_val = 2018;
//test.c
int main()
{
    extern int g_val;
	printf("%d\n", g_val);
	return 0;
}
```

代码1正常，代码2在编译的时候会出现连接性错误。

> 一个全局变量被static修饰，使得这个全局变量只能在本源文件内使用，不能在其他源文件内使
> 用。

#### 修饰局部变量

```c
//代码1
#include <stdio.h>
void test()
{
	int i = 0;
	i++;
	printf("%d ", i);
}
int main()
{
	int i = 0;
	for (i = 0; i < 10; i++)
	{
		test();
	}
	return 0;
}
//代码2
#include <stdio.h>
void test()
{
	//static修饰局部变量
	static int i = 0;
	i++;
	printf("%d ", i);
}
int main()
{
	int i = 0;
	for (i = 0; i < 10; i++)
	{
		test();
	}
	return 0;
}
```

> static修饰局部变量改变了变量的生命周期
> 让静态局部变量出了作用域依然存在，到程序结束，生命周期才结束。

#### 修饰函数



```c
//代码1
//add.c
int Add(int x, int y)
{
    return c + y;
}
//test.c

extern int Add(int ,int );//声明外部函数
int main()
{
    printf("%d\n", Add(2, 3));
    return 0;
}
//代码2
//add.c
static int Add(int x, int y)
{
    return c + y;
}
//test.c
int main()
{
    printf("%d\n", Add(2, 3));
    return 0;
}
```

代码1正常，代码2在编译的时候会出现连接性错误.

> 一个函数被static修饰，使得这个函数只能在本源文件内使用，不能在其他源文件内使用。



### register

![image-20221001112221232](D:\ALQF\Typora图片\image-20221001112221232.png)

如果a频繁使用，那么建议把a放到寄存器变量。

![image-20221001112303438](D:\ALQF\Typora图片\image-20221001112303438.png)

## define定义常量和宏

```c
//define定义标识符常量
#define MAX 1000
//define定义宏
#define ADD(x, y) ((x)+(y))
#include <stdio.h>
int main()
{
	int sum = ADD(2, 3);
	printf("sum = %d\n", sum);
	sum = 10 * ADD(2, 3);
	printf("sum = %d\n", sum);
	return 0;
}
```

![image-20221001113743319](D:\ALQF\Typora图片\image-20221001113743319.png)

## 指针

### 内存

内存是电脑上特别重要的存储器，计算机中程序的运行都是在内存中进行的 。
所以为了有效的使用内存，就把内存划分成一个个小的内存单元，``每个内存单元的大小是1个字节``。
为了能够有效的访问到内存的每个单元，就给内存单元进行了编号，这些编号被称为该内存单元的地
址。

![image-20221001113942166](D:\ALQF\Typora图片\image-20221001113942166.png)

![image-20221001122917582](D:\ALQF\Typora图片\image-20221001122917582.png)

变量是创建内存中的（在内存中分配空间的），每个内存单元都有地址，所以变量也是有地址的。
取出变量地址如下：

```c++
#include <stdio.h>
int main()
{
	int num = 10;
	&num;//取出num的地址
	//注：这里num的4个字节，每个字节都有地址，取出的是第一个字节的地址（较小的地址）
	printf("%p\n", &num);//打印地址，%p是以地址的形式打印
	return 0;
}
```

![image-20221001123127327](D:\ALQF\Typora图片\image-20221001123127327.png)

指针的使用实例：

```c
#include <stdio.h>
int main()
{
int num = 10;
int *p = &num;
*p = 20;
return 0;
}
```

以整形指针举例，可以推广到其他类型，如：

```c
#include <stdio.h>
int main()
{
char ch = 'w';
char* pc = &ch;
*pc = 'q';
printf("%c\n", ch);//q
return 0;
}
```



### 指针变量大小

32位平台下，指针就是4B.

64位平台下，指针就是8B.

```c
#include <stdio.h>
//指针变量的大小取决于地址的大小
//32位平台下地址是32个bit位（即4个字节）
//64位平台下地址是64个bit位（即8个字节）
int main()
{
	printf("%d\n", sizeof(char*));
	printf("%d\n", sizeof(short*));
	printf("%d\n", sizeof(int*));
	printf("%d\n", sizeof(double*));
	return 0;
}
```

> 结论：指针大小在32位平台是4个字节，64位平台是8个字节。

## 结构体

结构体是C语言中特别重要的知识点，结构体使得C语言有能力描述复杂类型。
比如描述学生，学生包含： 名字+年龄+性别+学号 这几项信息。
这里只能使用结构体来描述了。
例如：

```c
struct Stu
{
char name[20];//名字
int age; //年龄
char sex[5]; //性别
char id[15]； //学号
};
struct Stu s = {"张三"， 20， "男"， "20180101"};

//.为结构成员访问操作符
printf("name = %s age = %d sex = %s id = %s\n", s.name, s.age, s.sex, s.id);
//->操作符
struct Stu *ps = &s;
printf("name = %s age = %d sex = %s id = %s\n", ps->name, ps->age, ps->sex, ps-
>id);
```

# 分支语句和循环语句

> 分支语句

- if
- switch

> 循环语句

- while
- for
- do while

> goto语句

## 什么是语句

C语句可分为以下五类：
1. 表达式语句

2. 函数调用语句

3. 控制语句

4. 复合语句

5. 空语句

  **本周后面介绍的是`控制语句`。**

**控制语句**用于控制程序的执行流程，以实现程序的各种结构方式，它们由特定的语句定义符组成，C语
言有**九种控制语句**。
可分成以下三类：

1. 条件判断语句也叫分支语句：if语句、switch语句

2. 循环执行语句：do while语句、while语句、for语句；

3. 转向语句：break语句、goto语句、continue语句、return语句。

## 分支语句

### if语句

判断一个数是否为奇数

```c

int main()
{
	int num;
	scanf("%d", &num);
	if (num % 2 != 0)
	{
		printf("num:%d为奇数\n", num);
	}
	else
	{
		printf("num:%d为偶数\n", num);
	}
	return 0;
}
```

输出1-100之间的奇数

```c
int main()
{
	int num;

	for (int i = 1; i <= 100; i++)
	{
		if (i % 2 != 0)
		{
			printf("%d ", i);
		}

	}

	return 0;
}
```

### switch语句

#### break

- 不使用break时：

![image-20221001130310773](D:\ALQF\Typora图片\image-20221001130310773.png)

![image-20221001130347438](D:\ALQF\Typora图片\image-20221001130347438.png)

```c
#include <stdio.h>
int main()
{
	int day = 1;
	switch (day)
	{
	case 1:
			printf("星期一\n");
			
		case 2:
			printf("星期二\n");
			
		case 3:
			printf("星期三\n");
			
		case 4:
			printf("星期四\n");
			
		case 5:
			printf("星期五\n");
			
		case 6:
			printf("星期六\n");
			
		case 7:
			printf("星期天\n");
			
	}
	return 0;
}
```

- 在switch语句中，我们没办法直接实现分支，搭配break使用才能实现真正的分支。

```c
#include <stdio.h>
int main()
{
	int day = 1;
	switch (day)
	{
	case 1:
			printf("星期一\n");
			break;
		case 2:
			printf("星期二\n");
			break;
		case 3:
			printf("星期三\n");
			break;
		case 4:
			printf("星期四\n");
			break;
		case 5:
			printf("星期五\n");
			break;
		case 6:
			printf("星期六\n");
			break;
		case 7:
			printf("星期天\n");
			break;
	}
	return 0;
}
```



#### default子句

如果表达的值与所有的case标签的值都不匹配怎么办？
其实也没什么，结构就是所有的语句都被跳过而已。
程序并不会终止，也不会报错，因为这种情况在C中并不认为是个错误。
但是，如果你并不想忽略不匹配所有标签的表达式的值时该怎么办呢？
你可以在语句列表中增加一条default子句，把下面的标签
default：
写在任何一个 case 标签可以出现的位置。
当 switch 表达式的值并不匹配所有 case 标签的值时，这个 default 子句后面的语句就会执行。
所以，每个switch语句中只能出现一条default子句。
但是它可以出现在语句列表的任何位置，而且语句流会像执行一个case标签一样执行default子句。

**编程好习惯**

> 在每个 switch 语句中都放一条default子句是个好习惯，甚至可以在后边再加一个 break 。



```c
#include <stdio.h>
int main()
{
	int n = 1;
	int m = 2;
	switch (n)
	{
	case 1:
		m++;//m=3
	case 2:
		n++;
	case 3:
		switch (n)
		{//switch允许嵌套使用
		case 1:
			n++;//n=2
		case 2:
			m++;//m=4
			n++;//n=3
			break;
		}
	case 4:
		m++;//m=5
		break;
	default:
		break;
	}
	printf("m = %d, n = %d\n", m, n);//m=5,n=3
	return 0;
}
```

## 循环语句

### while循环

#### while语句中的break和continue

##### break介绍

到 5 直接退出循环

```c
//break 代码实例
#include <stdio.h>
int main()
{
	int i = 1;
	while (i <= 10)
	{
		if (i == 5)
			break;
		printf("%d ", i);//1 2 3 4 
		i = i + 1;
	}
	return 0;
}
```

##### continue介绍

> 使用continue，continue后面的语句不会执行。直接执行下一次循环。

```c
#include <stdio.h>
int main()
{
	int i = 1;
	while (i <= 10)
	{
		if (i == 5)
			continue;//死循环，continue后面的语句不会执行，输出1，2，3，4又会到 while ,i不会执行++
		printf("%d ", i);
		i = i + 1;
	}
	return 0;
}
```



```c
#include <stdio.h>
int main()
{
	int i = 1;
	while (i <= 10)
	{
		i = i + 1;
		if (i == 5)
			continue;
		printf("%d ", i);//输出2 3 4 6 7 8 9 10 11
		
	}
	return 0;
}
```

**总结:**

continue在while循环中的作用就是

> continue是用于终止本次循环的，也就是本次循环中continue后边的代码不会再执行，
> 而是直接跳转到while语句的判断部分。进行下一次循环的入口判断。

getchar接收\n的讲解

https://blog.csdn.net/u012900233/article/details/126377633



疑问：为什么getchar函数的返回的是字符的ASCII码值，那为什么要放在int类型的变量中呢？不是应该放在一个char类型的变量中吗？

> getchar返回了字符的ASCII码值，ASCII码值是整数，存放在整型变量中没有任何问题。
>
> 这一点也是最重要的一点，getchar函数读取失败的时候返回EOF，EOF的本质是-1，是一个整型值，在一个char类型的变量中，是存储不下的。
>
> 再结合一下getchar函数的原型，getchar的返回类型被定义为int，那么返回的数据就应该存放在int变量中。

```c
//代码什么意思？
//代码1
#include <stdio.h>
int main()
{
	int ch = 0;
	while ((ch = getchar()) != EOF)
		putchar(ch);
	return 0;
}
```

```c
//代码2
#include <stdio.h>
int main()
{
	char ch = '\0';
	while ((ch = getchar()) != EOF)
	{
		if (ch < '0' || ch > '9')//如果不是数字，就不会执行后面的putchar
			continue;
		putchar(ch);
	}
	return 0;
}
```



### for循环

### do...while()循环

## goto语句

C语言中提供了可以随意滥用的 goto语句和标记跳转的标号。
从理论上 goto语句是没有必要的，实践中没有goto语句也可以很容易的写出代码。
但是某些场合下goto语句还是用得着的，最常见的用法就是终止程序在某些深度嵌套的结构的处理过
程。
例如：一次跳出两层或多层循环。
多层循环这种情况使用break是达不到目的的。它只能从最内层循环退出到上一层的循环。

goto语言真正适合的场景如下：

```c
for(...)
for(...)
{
for(...)
{
if(disaster)
goto error;
}
}
…
error:
if(disaster)
// 处理错误情况
```



## 作业

### 输出三个数中最大数

```c
#include<stdio.h>
int main() {
	int num1=0, num2=0, num3=0;
	scanf("%d %d %d", &num1, &num2, &num3);
	if (num1<num2)
	{
		int temp = num1;
		num1 = num2;
		num2 = temp;
	}
	if (num1 < num3)
	{
		int temp = num1;
		num1 = num3;
		num3 = temp;
	}
	if (num2 < num3)
	{
		int temp = num2;
		num2 = num3;
		num3 = temp;
	}
	
	printf("%d %d %d",num1,num2,num3);
	
	return 0;
}

```

### 打印3的倍数

```c
#include<stdio.h>
int main() {
	for (int i = 1; i <= 100; i++)
	{
		if (i % 3 == 0) {
			printf("%d ", i);
		}
	}
}
```

### 求最大公约数

> 公约数是什么?
>
> 就比如18/24，约分成最简的，3/4，除以的6就是最大公约数

这是我自己写的方法：

```c
#include<stdio.h>
int main() {
	int num1, num2,length;
	scanf("%d %d",&num1,&num2);
	num1 > num2 ? length = num2 : length = num1;
	for (int i = length; i >= 2; i--)
	{
		if (num1 % i == 0 && num2 % i == 0) {
			printf("%d ",i);
			break;
		}
	}
}
```

> 辗转相除法：
>
> 假设m=24,n=18。第一次让r=24%18=6;r不为0
>
> 再让r=18%6=0;循环结束。
>
> 

```c
#include<stdio.h>
int main() {
	int num1, num2;
	int r;
	scanf("%d %d", &num1, &num2);
	while (r = num1 % num2)//r=24%18=6
	{
		num1 = num2;//num1=18
		num2 = r;//num2=6
	}
	printf("%d ", num2);//6
}
```

### 求闰年

> 闰年怎么算?
>
> 1.能被400整除的年份就是闰年
>
> 2.能被4整除并且不能被 100整除

```c
#include<stdio.h>
int main() {
	int sum = 0;
	for (int i = 1000; i <= 2000; i++)
	{
		if ((i%4==0&&i%100!=0)|| i % 400 == 0)
		{
			sum++;
			printf("%d ", i);
		}
		
	}
	printf("\n%d ", sum);//一共243个闰年
}
```

### 求素数

> 素数是什么？
>
> *素数*又叫*质数*。*素数*，指的是“大于1的整数中，只能被1和这个数本身整除的数”。2、*素数*也可以被等价表述成：“在正整数范围内，大于1并且只有1和自身两个约数的数”。

这是我自己写的：

```c
#include<stdio.h>
#include<math.h>
int main() {
	int sum = 0;
	for ( int i = 100;  i <=200;  i++)
	{
		int divide = sqrt(i);
		for (int k = 2; k <= divide; k++) {
			if (i % k == 0) break;
			//如果最后一次循环，都没有找到i%k的情况，看作是素数。
			if (divide == k )
			{
				sum++;
				printf("%d ",i);
				
			}
		}
		
	}
	printf("\nsum=%d", sum);//21
	return 0;
}
```

优化：偶数不可能是素数

```c
#include<stdio.h>
#include<math.h>
int main() {
	int sum = 0;
	for ( int i = 101;  i <=200;  i+=2)
	{
		int divide = sqrt(i);
		int k = 0;
		for(k= 2; k <= divide; k++) {
			if (i % k == 0) break;
		}
       //
		if (k>divide)
		{
			++sum;
			printf("%d ", i);
		}
		
	}
	printf("\nsum=%d", sum);
	return 0;
}
```



```c
#include<stdio.h>
#include<math.h>
int main() {
	int sum = 0;
	for (int i = 101; i <= 200; i+=2)
	{
		int divide = sqrt(i);
		for (int k = 2; k <= divide; k++) {
			if (i % k == 0) break;
			//如果最后一次循环，都没有找到i%k的情况，看作是素数。
			if (divide == k)
			{
				sum++;
				printf("%d ", i);
			}
		}
	}
	printf("\nsum=%d", sum);//21
	return 0;
}
```

### 数9的个数

![image-20221013172106790](D:\ALQF\Typora图片\image-20221013172106790.png)

> 如果个位为9的话，取模10，就要余9
>
> 如果十位为9的话，取 / 10，就要商9

```c	
#include<stdio.h>
int main() {
	int sum = 0;
	for (int i = 1; i <= 100; i++)
	{
		if (i%10==9||i/10==9)
		{
			++sum;
		}
	}
	printf("%d ", sum);//19.答案是错的，因为还有99的情况。这样只会累加一次
}
```



```c
#include<stdio.h>
int main() {
	int sum = 0;
	for (int i = 1; i <= 100; i++)
	{
		if (i%10==9)
		{
			++sum;
		}
		if (i / 10 == 9)
		{
			++sum;
		}

	}
	printf("%d ", sum);
}
```



### 分数求和

![image-20221013172651532](D:\ALQF\Typora图片\image-20221013172651532.png)

> 这里注意两个地方：
>
> 第一个地方是：sum要是double类型的，不然算出来的结果是不对的。答案是1，就只有1/1.
>
> 第二个地方是：double除的时候，要注意至少要有个地方的小数类型。不然也不行。

```c
#include<stdio.h>
int main() {
	double sum = 0.0;
	for (int i = 1; i <= 100; i++)
	{
		if (i % 2 == 0) {
			sum -= 1.0 / i;
		}
		else
		{
			sum += 1.0 / i;
		}
	}
	printf("%f ", sum);
}
```



### 求10个数中的最大值



```c
#include<stdio.h>
int main() {
	int arr[] = { 100,2,3,8989,798,6,7,8,9,10 };
	int max=0;
	for (int i = 0; i < 10; i++)
	{
		if (arr[i]>max)
		{
			max = arr[i];
		}
	}
	printf("%d ", max);
}
```



### 乘法口诀表

```c
#include<stdio.h>
int main() {
	for (int i = 1; i <= 9; i++)
	{
		for (int j = 1; j <= i; j++)
		{
			printf("%d*%d=%d ",i,j,i*j);
		}
		printf("\n");
	}
}
```

### 二分查找

```c
#include<stdio.h>
int main() {
	int arr[] = {1,2,3,4,5,6,7,8,9,10};
	int length = sizeof arr / sizeof arr[0];
	int findData;
	scanf("%d", &findData);
	int low = 0, high = length, mid;
	while (low<=high)
	{
		mid = (low + high) / 2;
		if (findData>arr[mid])
		{
			low = mid + 1;
		}
		else if (findData < arr[mid])
		{
			high = mid - 1;
		}
		else if (arr[mid]==findData)
		{
			printf("你要找的元素在%d位", mid);
			return 0;
		}
	}
}
```

### 猜数字游戏

如果写成这样，会出现这样的情况：

![image-20221103200647572](D:\ALQF\Typora图片\image-20221103200647572.png)

每次重启程序，效果都一样

![image-20221103200614058](D:\ALQF\Typora图片\image-20221103200614058.png)

在rand之前，要先设置一个srand()函数

![image-20221103200737081](D:\ALQF\Typora图片\image-20221103200737081.png)

![image-20221103200816853](D:\ALQF\Typora图片\image-20221103200816853.png)

这时候会出现什么效果呢？每次都一样，所以srand()里面的参数要一直变。那怎么办？

![image-20221103200849700](D:\ALQF\Typora图片\image-20221103200849700.png)

![image-20221013182323178](D:\ALQF\Typora图片\image-20221013182323178.png)

![image-20221013182448121](D:\ALQF\Typora图片\image-20221013182448121.png)

不要频繁用srand，不然时间差距不大，还是不够随机。srand在代码中用一次即可。

```c
#include<stdio.h>
#include<stdlib.h>
#include<time.h>
void menu();

void menu() {
	printf("**********************************\n");
	printf("*****1.play     0 .exit***********\n");
	printf("**********************************\n");
}

void game() {
	
	int ret=rand()%99+1;//生成一个随机数,0~RAND_MAX(0X7FFF-32767)
	int guess; 
	while (1)
	{
		printf("猜数字:\n");
		scanf("%d", &guess);
		if (guess>ret)
		{
			printf("猜大了\n");
		}
		else if (guess<ret)
		{
			printf("猜小了\n");
		}
		else {
			printf("恭喜你，猜对了\n");
			break;
		}

	}
}
int main() {
	int input = 0;
	srand((unsigned int)time(NULL));//srand在这里用一次计科
	do
	{
		menu();
		printf("请选择->：");
		scanf("%d", &input);
		switch (input)
		{
		case 1:
			game();
			break;
		case 0:
			printf("退出游戏！\n");
			break;
		default:
			printf("选择错误！\n");
			break;
		}
	} while (input);
}
```

# 函数

1. 函数是什么
2. 库函数
3. 自定义函数
4. 函数参数
5. 函数调用
6. 函数的嵌套调用和链式访问
7. 函数的声明和定义
8. 函数递归

## 函数是什么？

数学中我们常见到函数的概念。但是你了解C语言中的函数吗？
维基百科中对函数的定义：子程序

> - 在计算机科学中，子程序（英语：Subroutine, procedure, function, routine, method,
>   subprogram, callable unit），是一个大型程序中的某部分代码， 由一个或多个语句块组
>   成。它负责完成某项特定任务，而且相较于其他代 码，具备相对的独立性。
> - 一般会有输入参数并有返回值，提供对过程的封装和细节的隐藏。这些代码通常被集成为软
>   件库。

## C语言中函数的分类

1. 库函数
2. 自定义函数

### 库函数

为什么会有库函数？

1. 我们知道在我们学习C语言编程的时候，总是在一个代码编写完成之后迫不及待的想知道结果，想
    把这个结果打印到我们的屏幕上看看。这个时候我们会频繁的使用一个功能：将信息按照一定的格
    式打印到屏幕上（printf）。
2. 在编程的过程中我们会频繁的做一些字符串的拷贝工作（strcpy）。
3. 在编程是我们也计算，总是会计算n的k次方这样的运算（pow）。
    像上面我们描述的基础功能，它们不是业务性的代码。我们在开发的过程中每个程序员都可能用的到，
    为了支持可移植性和提高程序的效率，所以C语言的基础库中提供了一系列类似的库函数，方便程序员
    进行软件开发。
    那怎么学习库函数呢？
    这里我们简单的看看：www.cplusplus.com

简单的总结，C语言常用的库函数都有：

- IO函数
- 字符串操作函数
- 字符操作函数
- 内存操作函数
- 时间/日期函数
- 数学函数
- 其他库函数

我们参照文档，学习几个库函数：(教会学生怎么使用文档来学习库函数)。

> strcpy
> memset
> 注：
> 但是库函数必须知道的一个秘密就是：使用库函数，必须包含 #include 对应的头文件。
> 这里对照文档来学习上面几个库函数，目的是掌握库函数的使用方法。

#### strcpy

把source拷贝到destination，把数据源拷贝到目的地。

```c	
char * strcpy ( char * destination, const char * source );
```

```c
#include<stdio.h>
#include<string.h>
int main() {
	char arr1[] = "bit";
	char arr2[20] = "########";
	//现在我们将arr1中的内容拷贝到arr2,那么谁应该写右边？答:arr1;
	//strcpy拷贝的时候是连着'\0'一起去拷贝的。
	strcpy(arr2,arr1);
	printf("%s",arr2);//输出bit
	return 0;
}
```

这是刚开始的内存情况：

![image-20221103204106670](D:\ALQF\Typora图片\image-20221103204106670.png)

这是之后的：

![image-20221103204124420](D:\ALQF\Typora图片\image-20221103204124420.png)

值得注意的是：

![image-20221103204602628](D:\ALQF\Typora图片\image-20221103204602628.png)

#### memset

```c
void * memset ( void * ptr, int value, size_t num );
```

把ptr，的前 num 变成 vlalue值，为什么int value传参可以写成 *？因为是ASCII码存的

```c
char arr[] = "hello world";
	memset(arr, '*', 5);
	printf("%s", arr);
```



### 如何学会使用库函数？

需要全部记住吗？No
需要学会查询工具的使用：
MSDN(Microsoft Developer Network)
www.cplusplus.com
http://en.cppreference.com（英文版）
http://zh.cppreference.com（中文版）
英文很重要。最起码得看懂文献。

### 自定义函数

## 作业

### 用函数输出素数(质数)

```c
bool isPrime(int num) {
	int divid = sqrt(num);
	for (int i = 2; i <= divid; i++)
	{
		if (num% i==0)return false;		
	}
	return true;
}
int main() {
	int sumPrime = 0;
	for (int i = 101; i <= 200; i += 2)
	{
		if (isPrime(i)) {
			printf("%d ", i);
			sumPrime++;
		}	
	}
	printf("\nsum=%d", sumPrime);
	return 0;
}
```

### 用函数输出闰年(能被400整除或者能被4整除且不能被100整除)

```c
bool isRunYear(int year) {
	//能被400整除，并且能被4整除且不能被100整除
	if (year % 400 == 0 || (year % 4 == 0 && year % 100 != 0)) return true;
	return false;
}

int main() {
	int sumRunNian = 0;
	for (int i = 1000; i <=2000; i++)
	{
		if (isRunYear(i)) {
			printf("%d ",i);
			sumRunNian++;
		}
	}

	printf("\n%d", sumRunNian);
	
}
```

### 用函数二分查找

![image-20221106215424498](D:\ALQF\Typora图片\image-20221106215424498.png)

```c
int binarySearch(int datas[], int length, int findNum) {
	int midData = length>>2;
	for (int i = 0; i < length; i++)
	{
		if (findNum == datas[midData]) return midData;
		else if (findNum > datas[midData]) midData++;
		else midData--;
	}
	return 0;
}
```

```c
	int arr[] = { 1,2,3,4,5,6,7,8,9,0 };
	int length = sizeof arr / sizeof arr[0];
	if (int result=binarySearch(arr, length, 9)) printf("您要找的数据在第 %d 个位置 ", ++result);
	else printf("没找到");
```

形参是实参的一份临时拷贝。

```c
int binarySearch2(int datas[], int length, int findNum) {
	//length这样赋值行不行？答：不行，因为用形参传参的时候，是实参的一份临时拷贝，但是如果拷贝一个数组，空间太大了，所以拷贝的是数组的第一个元素的地址，win32编译出来就是4字节。4/4=1
	length = sizeof datas / sizeof datas[0];
	int left = 0;
	int right = length - 1;
	int midNum = (left+right) >> 2;
	while (left<=right)
	{
		if (datas[midNum] == findNum) return midNum;
		else if (datas[midNum] > findNum) right=--midNum;//从12345 中 找1，右边的指针就左移
		else left=++midNum;
		
	}
}
```

### 编写一个函数，调用一次函数num+1

```c
	int addNum=0;
	addFuction(&addNum);

	for (int i = 0; i < 10; i++)
	{
		addFuction(&addNum);

	}
```



```c

void addFuction(int* addNum) {
	printf("调用了 %d 次\n", (*addNum)++);
}
```

## 分模块写函数

> 在头文件中新建 add.h

写这个，一般都是add.h这个文件名，前面后面都有 __（两个下划线）

```c
#ifndef __ADD_H__
#define __ADD_H__
int add(int x,int y);
#endif //  
```

![image-20221107105823408](D:\ALQF\Typora图片\image-20221107105823408.png)

然后再写add的定义，也就是再新建add.c

```c
int add(int x,int y ) {
	return x + y;
}
```

再新建 测试的c文件

```c
#include<stdio.h>
#include "add.h"
int main() {
	int a = 10;
	int b = 30;
	int sum = add(a,b);
	printf("%d ",sum);
}
```

![image-20221107110610244](D:\ALQF\Typora图片\image-20221107110610244.png)

# 递归

## 内存划分与栈溢出

![image-20221107112414493](D:\ALQF\Typora图片\image-20221107112414493.png)

## 练习

### 顺序输出数

倒序输出

```c
#include<stdio.h>
int main() {
	unsigned int num = 1234;
	while (num>10)
	{
		int res = num % 10;
		num /= 10;
		printf("%d", res);
	}
	printf("%d", num);
}
```

![image-20221107165908926](D:\ALQF\Typora图片\image-20221107165908926.png)

```c
void printNum(int num) {
	if (num>9)
	{
		printNum(num / 10);
	}
	printf("%d ",num%10);
}
int main() {
	unsigned int num = 1234;
	printNum(num);
}
```

### 不创建变量，求出字符串长度

这是有中间变量的方式。

```c

int myStrLen(char str[]) {
	int length = 0;
	while (str[length]!='\0')
	{
		++length;
	}
	return length;
}
int main() {
	char str[] = "bit";
	int length = myStrLen(str);
	printf("%d ", length);
}
```



不创建中间变量

```c
int myStrLen2(char* str){
	if (*str != '\0') 	return 1 + myStrLen2(str + 1);
	else return 0;
}
```

![image-20221107172539196](D:\ALQF\Typora图片\image-20221107172539196.png)

### 求n的阶乘

```c
int jiecheng(int num) {
	int result = 1, sum = 0;
	for (int i = 1; i <=num; i++)
	{
		result = result * i;
	}
	return result;
}
```



```c	
int jiecheng2(int num) {
	if (num==1)
	{
		return 1;
	}
	else {
		return num * jiecheng2(num-1);//注意别写成num--,别改变num自身的值
	}
}
int main() {
	int n;
	scanf("%d",&n);
	printf("%d ", jiecheng2(n));
	
}
```

### 求第N个斐波那契数



```c
#include<stdio.h>
int fab(int n) {
	if (n==1||n==2)  return 1;
	else return fab(n - 1) + fab(n - 2);
}
int main() {
	int n=0;
	scanf("%d", &n);
	printf("斐波那契数是：%d",fab(n));
	return 0;
}
```



```c

int fab2(int n) {
	int result = 1;
	int index1 = 1;
	int index2 = 1;
	if (n==1||n==2)
	{
		return result;
	}
	for (int i = 3; i <=n; i++)
	{
		result = index1 + index2;
		index1 = index2;
		index2 = result;
	}
	return result;
}
```

# 数组

## 一维数组创建初始化(sizeof,strlen)

```c
#include<stdio.h>
#include<string.h>
int main() {
	int arr[10] = { 1,2,3 };//不完全初始化，剩下元素默认初始化为0
	char arr2[5] = { 'a',98 };//a,b,剩下三个默认初始化为0
	char arr3[5] = "ab";//放进去ab以及第三个放的是\0,后面两个默认初始化为0
	char arr4[] = "abcdef";//7个元素
	printf("%d", sizeof(arr4));//7,计算所占空间大小
	printf("%d", strlen(arr4));//6,计算字符串长度，\0不算字符串长度
}
```



```c
char arr5[] = "abc";
	char arr6[] = { 'a','b','c' };

	printf("%d", sizeof(arr5));//4,计算所占空间大小，有\0占一个空间
	printf("%d", sizeof(arr6));//3,计算所占空间大小
	printf("%d", strlen(arr5));//3,计算字符串长度，\0不算字符串长度
	printf("%d", strlen(arr6));//随机值，没有\0,计算出来是随机值
```

## 二维数组创建初始化

![image-20221111174916822](D:\ALQF\Typora图片\image-20221111174916822.png)

## 二维数组存储

通过结果我们可以分析到，其实二维数组在内存中也是连续存储的。

![image-20221111175121291](D:\ALQF\Typora图片\image-20221111175121291.png)

![image-20221111175151501](D:\ALQF\Typora图片\image-20221111175151501.png)
