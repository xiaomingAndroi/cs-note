# 基本数据类型



## 变量的表数范围和存储形式

![image-20221001181236823](D:\ALQF\Typora图片\image-20221001181236823.png)

# 基本算数运算

## 自动类型转换

![image-20221001181417703](D:\ALQF\Typora图片\image-20221001181417703.png)

![image-20221001181435169](D:\ALQF\Typora图片\image-20221001181435169.png)

> 纵向代表必然的转换
>
> 

![image-20221001181528372](D:\ALQF\Typora图片\image-20221001181528372.png)

### 强制类型转换

![image-20221001182037793](D:\ALQF\Typora图片\image-20221001182037793.png)

![image-20221001182055438](D:\ALQF\Typora图片\image-20221001182055438.png)

# 键盘输入和屏幕输出(有牛客)

## 数据的格式化屏幕输出

### %d,%u,%f,%e

![image-20221001182158860](D:\ALQF\Typora图片\image-20221001182158860.png)

### %c

![image-20221001182233091](D:\ALQF\Typora图片\image-20221001182233091.png)

### %ld,%hd

![image-20221001182536474](D:\ALQF\Typora图片\image-20221001182536474.png)

### %mf

![image-20221001182600952](D:\ALQF\Typora图片\image-20221001182600952.png)

![image-20221001182637599](D:\ALQF\Typora图片\image-20221001182637599.png)

### %.nf

![image-20221001182702910](D:\ALQF\Typora图片\image-20221001182702910.png)

### %m.nf

![image-20221001182719937](D:\ALQF\Typora图片\image-20221001182719937.png)

![image-20221001182732323](D:\ALQF\Typora图片\image-20221001182732323.png)

### 输出 %

![image-20221001182747763](D:\ALQF\Typora图片\image-20221001182747763.png)

## `例(牛客生日日期输入输出)`

C语言中%d %.2d %2d %02d的区别

https://gaixin.blog.csdn.net/article/details/78333338?spm=1001.2101.3001.6650.4&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-4-78333338-blog-76484669.pc_relevant_multi_platform_whitelistv4&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-4-78333338-blog-76484669.pc_relevant_multi_platform_whitelistv4&utm_relevant_index=9

![image-20221001183923243](D:\ALQF\Typora图片\image-20221001183923243.png)

```c
#include <stdio.h>

int main() {
    int year, month, date;
    scanf("%4d%2d%2d", &year, &month, &date);
    printf("year=%d\nmonth=%02d\ndate=%02d\n", year, month, date);
    return 0;

}
```



```c
#include <stdio.h>

int main() {
    int birthData;
    scanf("%d", &birthData);
    printf("year=%d\nmonth=%02d\ndate=%02d\n", birthData / 10000,
           (birthData / 100) % 100, birthData % 100);
}
```

## 数据的格式化键盘输入

![image-20221001191600247](D:\ALQF\Typora图片\image-20221001191600247.png)

### %md

![image-20221001191453667](D:\ALQF\Typora图片\image-20221001191453667.png)

![image-20221001191513439](D:\ALQF\Typora图片\image-20221001191513439.png)

### 常见错误

![image-20221001191541994](D:\ALQF\Typora图片\image-20221001191541994.png)

### 用lf读入双精度实数,用%f输出

![image-20221001191649380](D:\ALQF\Typora图片\image-20221001191649380.png)

### %*nd

![image-20221001191711615](D:\ALQF\Typora图片\image-20221001191711615.png)

## 字符的输入输出

![image-20221001191821938](D:\ALQF\Typora图片\image-20221001191821938.png)

### (putchar的坑)

不能写成双引号，因为putchar只能输出单个字符，不能输出字符串。

![image-20221001191856243](D:\ALQF\Typora图片\image-20221001191856243.png)

### scanf和getchar的区别

![image-20221001192100536](D:\ALQF\Typora图片\image-20221001192100536.png)

#### getchar()的问题

```c
#include <stdio.h>
int main()
{
	char ch1, ch2;
	ch1 = getchar();
	printf("ch1=%c\n", ch1);
	ch2 = getchar();
	printf("ch2=%c\n", ch2);
	return 0;
}
```

这个代码的运行结果是：

输入1,然后换行。ch2读入的就是换行 \n,ASCII码是10.

![image-20221001194750220](D:\ALQF\Typora图片\image-20221001194750220.png)

输入 ab ,ch2就会变成b

![image-20221001195016064](D:\ALQF\Typora图片\image-20221001195016064.png)

#### 问题的原因

![image-20221001195639371](D:\ALQF\Typora图片\image-20221001195639371.png)

![image-20221001195932413](D:\ALQF\Typora图片\image-20221001195932413.png)

### 用%c输入数据存在的问题

![image-20221001200130478](D:\ALQF\Typora图片\image-20221001200130478.png)

#### 问题解决

![image-20221001200203126](D:\ALQF\Typora图片\image-20221001200203126.png)

空白字符：包括空格，tab键，和换行

![image-20221001200217992](D:\ALQF\Typora图片\image-20221001200217992.png)

#### 问题举例

![image-20221001200330528](D:\ALQF\Typora图片\image-20221001200330528.png)

![image-20221001200426301](D:\ALQF\Typora图片\image-20221001200426301.png)

![image-20221001200459194](D:\ALQF\Typora图片\image-20221001200459194.png)

![image-20221001200528836](D:\ALQF\Typora图片\image-20221001200528836.png)

![image-20221001200606460](D:\ALQF\Typora图片\image-20221001200606460.png)

## `例 大小写转换`

![image-20221001203058915](D:\ALQF\Typora图片\image-20221001203058915.png)

```c
#include <stdio.h>

int main() {
    char bigChar;
    while (scanf(" %c", &bigChar) != EOF) { // 注意 while 处理多个 case
        // 64 位输出请用 printf("%lld")
        printf("%c\n", bigChar+32);
    }
    return 0;
}
```



```c
    #include <stdio.h>

    int main() {
        int  bigChar;
        while ((bigChar=getchar()) != EOF) { // 注意 while 处理多个 case
            // 64 位输出请用 printf("%lld")
            getchar();
            printf("%c\n", bigChar+32);
        }
        return 0;
    }
```



# 选择控制结构

## 数值溢出和精度损失问题

### 自动类型转换

![image-20221001200927784](D:\ALQF\Typora图片\image-20221001200927784.png)

![image-20221001201034551](D:\ALQF\Typora图片\image-20221001201034551.png)

### 整数的值溢出(上溢)

![image-20221001200841379](D:\ALQF\Typora图片\image-20221001200841379.png)

![image-20221001201202858](D:\ALQF\Typora图片\image-20221001201202858.png)

![image-20221001201352222](D:\ALQF\Typora图片\image-20221001201352222.png)

借1当2

![image-20221001201444159](D:\ALQF\Typora图片\image-20221001201444159.png)

### 浮点数的溢出

![image-20221001201637795](D:\ALQF\Typora图片\image-20221001201637795.png)

### 危害

![image-20221001201647029](D:\ALQF\Typora图片\image-20221001201647029.png)

### 解决对策

![image-20221001201700169](D:\ALQF\Typora图片\image-20221001201700169.png)

# 循环控制结构

# 函数

# 数组和算法基础

# 指针

# 字符串

# 指针和数组

# 结构体和数据结构

# 文件