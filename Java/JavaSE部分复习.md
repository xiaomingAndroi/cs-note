# JavaSE部分复习

## 类型转换

> <font color='cornflowerblue'>基本数据类型</font>
>
> <font color='red'>整形</font> :byte(1个字节),short（2个字节）,int（4个字节）,long（8个字节，默认值为0L）
>
> <font color='red'>浮点型</font>:float（4个字节）, double（8个字节）
>
> <font color='red'>字符型</font>:char（2个字节）
>
> <font color='red'>布尔型</font>:boolean（1个字节）
>
> <font color='cornflowerblue'>引用数据类型</font>
>
> <font color='red'>类</font>：class
>
> <font color='red'>接口</font>：interface
>
> <font color='red'>数组</font>：array
>
> 只是讨论七种基本数据类型,除了 boolean

C语言中占用字节数：

![image-20220304195345980](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220304195345980.png)

### 自动类型提升

> 当<font color='red'>容量小</font>的数据类型的变量和<font color='red'>容量大</font>的数据类型的变量做运算时，结果<font color='red'>自动提升</font>为<font color='red'>容量大</font>的数据类型。
>
> byte,char,short---->int---->long---->float---->double
>
> 特别的，当byte,char,short三种类型的变量做运算时，结果为int类型。
>
> <font color='cornflowerblue'>说明：此时的容量大小指的是，表示数的范围的大小，比如float容量要大于long的容量。</font>



```java
         //byte和int，能用int存
        byte b1 = 2;
        int i1 = 129;
        byte b2 = b1 + i1;//编译不通过，因为小的盒子不能装大的数据
        int i2 = b1 + i1;
        System.out.println(i2);//131

        //byte和int，能用long存
        long l1 = b1 + i1;//编译通过
        //int和byte，能用float存
        float f = b1 + i1;
        System.out.println(f);
        //short和double，能用double存
        short s1 = 123;
        double d1 = s1;
        System.out.println(d1);//123.0
        //char和int结果是int
        char c1 = 'a';
        int i3 = 10;
        int i4 = c1 + i3;
        //char和short结果是int
        short s2 = 10;
        int i5 = c1 + s2;
        //short 和 byte 结果是int
        byte b3 = 10;
        int c3=s2 +b3;
```



### 强制类型转换

> 自动类型提升的逆运算；
>
> 为什么是-128呢？
>
> 计算机存储数据都是以补码的形式存放的，存的时候是128，
>
> 原码即为10000000，补码是10000000，符号位为1，是负数。

```java
        double d1=12.3;
        int i1=(int)d1;
        System.out.println(i1);//12，截断操作
        double d2=12.9999;
        int i2=(int)d2;
        System.out.println(i2);//12，截断操作

        int i3=128;
        byte b=(byte) i3;
        System.out.println(b);//-128
```



![image-20220304135536539](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220304135536539.png)

### long加L和float加f问题

```java
       long l1=123123;
        System.out.println(l1);
        long l2=156464645645;//编译失败，如果不加f,就默认当int存放
        System.out.println(l2);

        float f1=12.3;//编译失败，如果不加f，默认当double存放
        float f2=12.3f;
```



![image-20220304210930454](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220304210930454.png)



## 数组

### 基本操作

#### 一维数组的初始化

> 静态初始化

![image-20220225155150985](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220225155150985.png)

> 动态初始化

![image-20220225155108995](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220225155108995.png)

#### 一维数组的默认初始化值

![image-20220225155205441](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220225155205441.png)

int arr[] 也行

![image-20220225155218554](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220225155218554.png)

![image-20220225155238283](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220225155238283.png)

![image-20220225155250736](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220225155250736.png)

![image-20220225155301437](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220225155301437.png)

#### 一维数组内存结构

> 栈中存放局部变量
>
> String的对象存放在常量池中，静态域中存放Static变量
>
> 堆中存放new出来的结构

![image-20220225155322209](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220225155322209.png)

#### 二维数组的初始化

> 静态初始化

![image-20220225155541863](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220225155541863.png)

![image-20220225155604633](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220225155604633.png)

![image-20220225155626690](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220225155626690.png)

#### 二维数组的默认初始化值

```java	
        int arr[][] = new int[4][3];
        System.out.println(arr[0]);//[I@50cbc42f,[代表的是以为数组的地址，I代表的Int类型
        System.out.println(arr[0][0]);//0

        float arr2[][]=new float[4][3];
        System.out.println(arr2[0]);
        System.out.println(arr2[0][0]);

        String [][] arr3=new String[4][3];
        System.out.println(arr3[1]);
        System.out.println(arr3[1][1]);

        String[] arr4[]=new String[4][];
        System.out.println(arr4[0]);//输出null，因为一维数组没有初始化，所以代表行的指针指不到列，指向空
        System.out.println(arr4[0][0]);//输出空指针，因为一维数组没有初始化
```

> 总结

![image-20220225172422637](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220225172422637.png)

#### 二维数组内存结构

![image-20220225172950224](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220225172950224.png)

![image-20220225173021784](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220225173021784.png)

![image-20220225173038152](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220225173038152.png)

![image-20220225173206956](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220225173206956.png)

### 简单算法

#### 杨辉三角

```java	
public class ArrayTest2 {
    public static void main(String[] args) {
        int[] arr[]=new int[10][10];
        for (int i = 0; i < arr.length; i++) {
            for (int j = 0; j <= i; j++) {
               if (i==j||j==0){
                   arr[i][j]=1;
               }else {
                   arr[i][j]=arr[i-1][j-1]+arr[i-1][j];
               }
                System.out.print(arr[i][j]);
            }
            System.out.println();
        }

    }
}
```

#### 数组随机赋值

> Math.random()的用法，该方法会生成一个0--1的随机数。所以需要一个强制类型转换（int）
>
> 如果想生成一个2--7的随机数应该怎么做呢？
>
> (int)(Math.random()*5)+2

```java	
public class ArrayTest3 {
    public static void main(String[] args) {
        int arr[] = new int[6];
        int length = arr.length;
        boolean flag = false;
        //System.out.println(length);//6
        //int num=new Random().nextInt(30);
        for (int i = 0; i < length; i++) {
            int num = (int) ((Math.random() * 6) + 1);
            arr[i] = num;
            while (true) {
                for (int j = 0; j < i; j++) {
                    if (arr[i] == arr[j]) {
                        flag = true;
                        break;
                    }
                    if (flag) {
                        arr[i] = (int) ((Math.random() * 6) + 1);
                        flag=false;
                        continue;
                    }
                }
                break;
            }
        }

        for (int i = 0; i < length; i++) {
            System.out.println(arr[i]);
        }
    }
}
```

#### 数组的反转

#### 数组的复制

##### 方式1：不叫真正的复制

```java	
public class ArrayCopy {
    public static void main(String[] args) {
        int[] array1 =new int[]{1,2,3,4,5,6};
        int[] array2;
        array2=array1;
        for (int i = 0; i <array2.length ; i++) {
            array2[1]=666;
        }
        for (int i = 0; i < array1.length; i++) {
            System.out.println(array1[i]);//1,666,2,3,4,5
        }
    }
}
```

##### 方式2：真正的复制

```java	
        int[] array1 =new int[]{1,2,3,4,5,6};
        int len=array1.length;
        int[] array2=new int[len];
        for (int i = 0; i < len; i++) {
            array2[i]=array1[i];
        }
        array2[1]=666;
        for (int i = 0; i < len; i++) {
            System.out.println(array1[i]);//1 2 3 4 5 6 
        }
```

#### 数组的反转

```java	
public class ArrayReverse {
    public static void main(String[] args) {
        int[] arr=new int[]{1,2,3,4,5,6};
        int len=arr.length;
        for (int i = 0; i < len/2; i++) {
            int temp=arr[i];
            arr[i]=arr[len-i-1];
            arr[len-i-1]=temp;
        }
        for (int i = 0; i < len; i++) {
            System.out.println(arr[i]);
        }
    }
}
```

#### 线性查找

```java	
public class ArrayFind {
    public static void main(String[] args) {
        String[] datas=new String[]{"AA","BB","CC","DD","EE"};
        String findData="EE";
        int len=datas.length;
        for (int i = 0; i < len; i++) {
            if (datas[i].equals(findData)){
                System.out.println(i+1);
                break;
            }
        }
    }
}
```

#### 二分查找

![image-20220330155050724](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330155050724.png)

> 首先定义一个首索引，一个末索引。循环条件是首索引小于末索引。
>
> 定义一个中间变量middle,
>
> 如果要查找的值小于Middle,那么end就左移到Middle左边一个位置去。
>
> 如果要查找的值大于Middle,那么head就右移到middle右边的一个位置去。

```java
public class ArrayBinary {
    public static void main(String[] args) {
        int[] arr=new int[]{-98,-34,2,34,54,66,79,105,210,333};
        int dest=4;//要寻找的变量
        int len=arr.length;
        int head=0;//首索引
        int end=len-1;//末索引
        boolean flag=true;
        while (head<=end){
            int middle=(head+end)/2;
            if (dest==arr[middle]){
                System.out.println("找到了，索引位置为:"+middle);
                flag=false;
                break;
            }else if (arr[middle]>dest){
                end=middle-1;
            }else {
                head=middle+1;
            }
        }
        if (flag){
            System.out.println("没找到");
        }
    }
}
```

#### 冒泡排序

![image-20220330183229120](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330183229120.png)

> 算法思想：
>
> 最外层的for循环是几大轮的意思。如果有len个元素需要多少轮呢？
>
> 答：需要len-1轮。因为剩下的最后一个元素肯定是最大或者是最小的了。
>
> 最外层循环是每一轮比较相邻的元素的意思。

```java	
public class ArrayBubble {
    public static void main(String[] args) {
        int[] arr=new int[]{1,3,5,8,5,2,6,7,8,6,10,22,33};
        int len=arr.length;
        for (int i = 0; i <len-1 ; i++) {
            for (int j = 0; j < len-i-1; j++) {
                if (arr[j]>arr[j+1]){
                    int temp=arr[j];
                    arr[j]=arr[j+1];
                    arr[j+1]=temp;
                }
            }
        }
    }
}
```

### Arrays工具类的使用

#### Arrays.equals();

> 判断两个数组是否相等

```java
public class ArraysUtilUse {
    public static void main(String[] args) {
        int[] arr1=new int[]{1,2,3,4};
        int[] arr2=new int[]{1,3,2,4};
        int[] arr3=new int[]{1,2,3,4};
        boolean isEquals= Arrays.equals(arr1,arr2);
        boolean isEquals2= Arrays.equals(arr1,arr3);
        System.out.println(isEquals);//false
        System.out.println(isEquals2);//true
    }
}
```

> equals源码

先看地址是不是一样？

如果地址都一样，那肯定一样

看看是不是空？

如果是空，那不一样

看看长度是不是一样？

如果长度都不一样，那就肯定不一样了。

如果都一样，就每个元素比较一下。

![image-20220330184852314](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330184852314.png)

#### Arrays.toString();

```java	
System.out.println(Arrays.toString(arr1));//[1, 2, 3, 4]
```

![image-20220330185210693](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330185210693.png)

#### Arrays.fill();

```java	
        Arrays.fill(arr1,10);//10,10,10,10
        System.out.println(Arrays.toString(arr1));//[10, 10, 10, 10]
```

![image-20220330185404212](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330185404212.png)

#### Arrays.sort();

> 底层是快排

```java
public class ArraysUtilUse {
    public static void main(String[] args) {
        int[] arr1=new int[]{1,2,3,4};
        int[] arr2=new int[]{1,3,2,4};

        Arrays.sort(arr2);
        System.out.println(Arrays.toString(arr2));// [1, 2, 3, 4]
    }
}
```

![image-20220330185618511](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330185618511.png)

#### Arrays.binarySearch();

```java	

public class ArraysUtilUse {
    public static void main(String[] args) {
        int[] arr1=new int[]{1,2,3,4};
        int i = Arrays.binarySearch(arr1, 88);
        System.out.println(i);//-5
    }
}
```

![image-20220330185826776](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330185826776.png)

### 数组使用的常见异常

> 数组越界
>
> 空指针

## 面向对象

> 面向过程

强调的是功能行为，以函数作为最小的单位，考虑怎么做。

> 面向对象

强调具备了功能的对象，以类和对象作为最小的单位，考虑谁来做。

### 对象的创建内存解析

堆：存放对象实例。

栈：存储局部变量

方法区：类信息，常量，静态变量，编译器编译后的代码数据

![image-20220330192243329](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330192243329.png)

局部变量是在栈空间中的，属性是在堆空间中的。

![image-20220330192649345](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330192649345.png)

### 对象数组

![image-20220330193022099](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330193022099.png)

![image-20220330193140616](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330193140616.png)

### 匿名对象

> 匿名对象：
>
> 创建的对象没有显式的赋给一个变量名。
>
> 特征：匿名对象只能调用一次。

![image-20220330193402818](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330193402818.png)

![image-20220330193450117](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330193450117.png)

![image-20220330193659692](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330193659692.png)

```java	
public class Anonymous {
    public static void main(String[] args) {
        PhoneMall phoneMall = new PhoneMall();
        phoneMall.show(new Phone());
    }
}
class PhoneMall{
    public void show(Phone phone){
        phone.playGame();
        phone.sendEmail();
    }
}

class Phone{
    double price;
    public void sendEmail(){
        System.out.println("发送邮件");
    }
    public void playGame(){
        System.out.println("玩游戏");
    }
    public void showPrice(double price){
        System.out.println("手机价格为："+price);
    }
}
```

### 方法的重载

> 在一个类中，允许存在一个以上的同名方法，但是参数个数和参数的类型不相同。
>
> 和权限修饰符，返回值类型，形参变量名，方法体都没有关系。

和权限修饰符没关系

![image-20220330195032233](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330195032233.png)

和返回值类型没关系

![image-20220330195110590](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330195110590.png)

和变量名没关系

![image-20220330195218755](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330195218755.png)

和方法体没关系

![image-20220330195237360](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330195237360.png)

### 方法的重写

![image-20220406120743220](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406120743220.png)

![image-20220406120939484](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406120939484.png)

### 可变个数的形参

> 能和多个实参相匹配的形参。

![image-20220330195609166](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330195609166.png)

![image-20220330200003334](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330200003334.png)

![image-20220330200014685](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330200014685.png)

![image-20220330200043996](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330200043996.png)

![image-20220330200346893](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330200346893.png)

### 值传递机制

如果变量是基本数据类型，此时赋值的变量是保存的数据值。

如果变量是引用数据类型，此时赋值的是变量保存的数据的地址值。

![image-20220330204834255](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330204834255.png)

#### 基本数据类型

因为形参和局部变量在栈空间中，相当于都是新的 变量

```java	
public class PassByValueTest {
    public static void main(String[] args) {
        int a=10;
        int b=20;
        swap(10,20);
        System.out.println(a+" "+b);//10 20
    }

    public static void swap(int  a,int b){
       int temp=a;
       a=b;
       b=temp;
    }
```

这样能换成功吗？答案也是不能的，因为int a,和int b是变量形参。在栈空间中，改变了栈空间的值。

```java	
public class ArrayBubble {
    public static void main(String[] args) {
        int[] arr = new int[]{1, 3, 5, 8, 5, 2, 6, 7, 8, 6, 10, 22, 33};
        int len = arr.length;
        for (int i = 0; i < len - 1; i++) {
            for (int j = 0; j < len - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                   swap(arr[j],arr[j+1]);
                }
            }
        }

    }
    public static void swap ( int a, int b){
        int temp = a;
        a = b;
        b = temp;
    }
}
```

![image-20220330210249546](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330210249546.png)

#### 引用数据类型

因为引用数据类型，创建的对象是在堆中的，在栈中创建两个变量，但是都指向堆中一块地址。

![image-20220330210453611](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330210453611.png)

```java	
public class ArrayBubble {
    public static void main(String[] args) {
        int[] arr = new int[]{1, 3, 5, 8, 5, 2, 6, 7, 8, 6, 10, 22, 33};
        int len = arr.length;
        for (int i = 0; i < len - 1; i++) {
            for (int j = 0; j < len - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
//                    int temp = arr[j];
//                    arr[j] = arr[j + 1];
//                    arr[j + 1] = temp;
                    swap(arr,j,j+1);
                }
            }
        }

    }
    public static void swap (int [] arr, int index1, int index2){
        int temp = arr[index1];
        arr[index1] = arr[index2];
        arr[index2] = temp;
    }
}

```

> 不会

![image-20220330210938337](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220330210938337.png)

```java	
public class PassByValueTest {
    public static void main(String[] args) {
        int a=10;
        int b=20;
        method(a,b);
        System.out.println(a+" "+b);//10 20
    }
    public static void method(int a,int b){
        a=100;
        b=200;
        System.out.println(a+" "+b);//
        System.exit(0);
    }
}
```

### 封装性

![image-20220406101158478](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406101158478.png)

![image-20220406101715930](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406101715930.png)

![image-20220406101414575](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406101414575.png)

![image-20220406101543748](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406101543748.png)

#### 类和类的成员

类和类的成员有属性，方法，构造器，这里讲解的是构造器的使用。

构造器是一个独立的结构，不是一个方法。

![image-20220406102109061](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406102109061.png)

#### JavaBean

![image-20220406102201625](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406102201625.png)

#### this关键字

##### this修饰属性

> 此时输出1

```java
public class ThisTest {
    public static void main(String[] args) {
        Person person = new Person();
        person.setAge(1);
        System.out.println(person.getAge());
    }
}

class  Person{
    private String name;
    private Integer age;

    public String getName() {
        return name;
    }

    public void setName(String n) {
        name = n;
    }

    public Integer getAge() {
        return age;
    }

    public void setAge(Integer n) {
        age = n;
    }
}

```

改成这样之后，发现输出的值是null。Idea编译器提示我们，是自己赋值给自己了。但是输出的是本类的age.

![image-20220406111352414](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406111352414.png)

```java	
public Integer getAge() {
        return age;
    }

    public void setAge(Integer age) {
        age = age;
    }
```

此时要引入this,表示当前对象的。

> 总结

![image-20220406114919543](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406114919543.png)

##### this调用构造器

![image-20220406115118027](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406115118027.png)

![image-20220406115221925](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406115221925.png)

![image-20220406115327675](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406115327675.png)

### 继承性

#### 继承性说明

![image-20220406115756224](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406115756224.png)

![image-20220406120133755](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406120133755.png)

![image-20220406120223115](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406120223115.png)

#### Object类

一个类没继承父类，但是还是有这么多功能，这些功能是谁的呢？

![image-20220406120344560](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406120344560.png)

![image-20220406120450140](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406120450140.png)

![image-20220406120520430](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406120520430.png)

#### super()

super的效率高，因为能直接找到父类

![image-20220406121120202](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406121120202.png)

![image-20220406121215496](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406121215496.png)

#### 子类对象实例化的过程

![image-20220406121354830](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406121354830.png)

![image-20220406121420697](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220406121420697.png)

### 多态性

![image-20220409104158547](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220409104158547.png)



> Person p=new Man();
>
> 编译看左边（编译的时候，看左边有没有定义你调用的方法）
>
> 运行看右边（如果子类和父类中同时含有一个方法，那调用的就是右边的）
>
> 你去帮我叫个人，然后我叫了个男人，那么这个男人就有男人的方法，吃得多。
>
> 对象的多态性只适用于方法，不适用于属性。

```java
public class People {
    int age=1;
    public void eat(){
        System.out.println("人吃...");
    }
    public void walk(){
        System.out.println("人走路...");
    }
}
```

```java

public class Man extends People{
   int age=2;
    public void earnMoney(){
        System.out.println("男人赚钱");
    }

    public void eat(){
        System.out.println("男人吃...");
    }
    public void walk(){
        System.out.println("男人走路...");
    }
}
```

```java
  @Test
    public void test5(){
        People people=new People();
        people.eat();

        People people1=new Man();
        people1.walk();//男人走路
        people1.earnMoney();
        people1.age;//1，为什么是1？因为对象的多态性，不适用于属性
    }
```

#### 多态性应用举例：虚拟方法调用

> 子类定义了父类同名同参数的方法，在多态情况下，父类的方法是虚拟方法。父类动态调用子类的方法。
>
> 简单的说：通过变量名去调用子父类的同名方法时，编译时我们认为调用的是父类的方法，解释运行的时候调用的是子类重写的方法。

![image-20220409110649015](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220409110649015.png)

##### 举例1

![image-20220409102826713](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220409102826713.png)

![image-20220409102815254](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220409102815254.png)

> 有了多态性，可以任意切换，子类的对象，只需要用一个Animal用来传参。至于new 谁那就随便挑个子类。

![image-20220409103203494](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220409103203494.png)

> 如果没有多态性，那就只能写两个重载的方法，很麻烦。

![image-20220409103004840](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220409103004840.png)

##### 举例2

![image-20220409103527428](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220409103527428.png)

![image-20220409103623689](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220409103623689.png)

![image-20220409103613139](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220409103613139.png)

##### 如何证明多态性是运行时行为？

> 什么是运行时行为，什么是编译时行为，编译时行为就是编译器直接就能知道的，比如说你没打分号，编译器直接就报错了，但是多态，父类的引用指向哪个子类的对象，不得而知。需要运行才知道。

可能我们用肉眼看 People p =new Man();一看就知道了，这肯定是编译时行为嘛！错了，是运行时行为，举个例子,这种情况如何知道呢？答：运行了才知道

```java	
public class ManyTaiTest {
    public static void main(String[] args) {
       Test test= getInstance();
    }

    static Test getInstance(){
        int i =new Random().nextInt(2);
        switch (i){
            case 0:
                return new TestSon();
            case 1:
                return new TestSister();
        }
        return  null;
    }
   static class Test{
    }
    static class TestSon extends Test{
        public TestSon() {
            System.out.println("TestSon");
        }
    }
  static   class TestSister extends Test{
      public TestSister() {
          System.out.println("TestSister");
      }
  }
}
```

![image-20220409110002035](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220409110002035.png)

#### 多态和重载重写

> 因为重写的方法参数不同，编译器一看就知道，肯定是确定调用了那个方法。
>
> 但是重载不一样，需要运行之后才知道，重载的是谁的方法。

![image-20220409110219827](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220409110219827.png)

#### 向下转型 和 instance of

![image-20220409111550648](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220409111550648.png)

![image-20220409111600762](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220409111600762.png)

![image-20220409111622982](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220409111622982.png)

![image-20220409111753716](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220409111753716.png)

> 有了对象的多态性之后，内存实际上是加载了子类特有的属性和方法，但是由于变量声明为父类导致编译时候，只能调用父类声明的属性和方法。子类特有的属性和方法不能调用

```java
 People people1=new Man();
        people1.walk();//男人走路
        /**
         * 此时people的引用people1，Man这个子类的对象赋值了这个子类。所以people1能使用people中和man同名的方法和属性
         *但是这个时候想用Man中的属性和方法，怎么办呢？只能强转，也可以叫做向下转型。
         */
        Man man=(Man) people1;
        man.earnMoney();
        Woman woman=(Woman) people1;//此时运行失败---java.lang.ClassCastException
        woman.goShopping();
```

使用instanceof，例如a instance of b,判断a 是不是 b 的一个实例。

```java	
  if (people1 instanceof Man){
            Man man=(Man) people1;
            man.earnMoney();
        }

        if (people1 instanceof Woman){
            Woman woman=(Woman) people1;
            woman.goShopping();
        }
```

![image-20220409122339347](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220409122339347.png)

### Object类的使用

![image-20220413104100926](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413104100926.png)

#### getClass()

```java	
public class ObjectTest {
    public static void main(String[] args) {
        System.out.println(new Order().getClass().getSuperclass());//class java.lang.Object
    }
}
class Order{

}
```

#### finalize()

finalize()--堆空间在栈空间没有任何引用实例，对堆空间的申请进行回收。

![image-20220413103036888](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413103036888.png)

![image-20220413103057440](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413103057440.png)

![image-20220413103111821](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413103111821.png)

![image-20220413103534134](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413103534134.png)

#### hashcode()

#### clone()

#### equals()

##### ==的使用

![image-20220413104632154](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413104632154.png)

> 基本数据类型：比较数值
>
> i会自动类型提升

![image-20220413104540937](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413104540937.png)



> 引用数据类型：比较地址

![image-20220413104730664](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413104730664.png)

##### equals()方法



> 第一行调用的是Object当中的equals()方法，和==是一样的
>
> 第二行调用的是String当中重写的equals()方法

![image-20220413110255427](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413110255427.png)

![image-20220413110404362](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413110404362.png)

![image-20220413110553776](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413110553776.png)

##### 重写equals()方法

> String 底层有个char 型数组，value[],比如输入Hello,就是char[5]

![image-20220413110831294](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413110831294.png)

![image-20220413110940163](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413110940163.png)

![image-20220413111045528](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413111045528.png)

> 自动生成的equals

![image-20220413111204821](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413111204821.png)

##### equals()和==的区别

![image-20220413111334119](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413111334119.png)

#### toString()

![image-20220413112241628](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413112241628.png)

![image-20220413111851433](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413111851433.png)

![image-20220413111910316](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413111910316.png)

> 为什么println和toString 输出结果是一样的？

![image-20220413112025213](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413112025213.png)

![image-20220413112050916](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413112050916.png)



![image-20220413112147230](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413112147230.png)

##### 重写toString()

![image-20220413112351796](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413112351796.png)

#### wait()

#### notify()

#### notifyAll()

### 包装类的使用

#### 为什么使用包装类？

> 为什么要包装类呢？
>
> 使得基本数据类型具有类的特征。
>
> 因为java是面向对象的，如果使用基本数据类型会显得很单薄。Object类也写了很多方法。比如equals方法，参数就是一个Object类，那你能用int扔进去嘛？不能，那就不能用equals方法了。

![image-20220413112930337](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413112930337.png)

![image-20220413112915094](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413112915094.png)

#### 基本数据类型转包装类

![image-20220413113258954](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413113258954.png)

![image-20220413113527775](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413113527775.png)

> 其他包装类可以写"123"这样的，但是不能写其他字符，比如"123ab",但是Boolean不一样，Boolean可以写，写了其他字符默认就是flase

![image-20220413113400585](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413113400585.png)

![image-20220413113415645](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413113415645.png)

![image-20220413113602102](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413113602102.png)

#### 包装类转换为基本数据类型

> xxx.xxxValue()

![image-20220413113753342](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413113753342.png)

#### 自动装箱和自动拆箱

> JDK5.0之后
>
> 本来基本数据类型赋值给包装类的时候，需要用new。但是现在不用new了，直接赋值，因为自动装箱。
>
> 以前包装类的转化成基本数据类型的时候需要xxxValue,现在不用了，直接把引用数据类型赋值给基本数据类型。因为能自动拆箱。

![image-20220413114040099](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413114040099.png)

#### 基本数据类型和String的转换

> 基本数据类型转换为String
>
> 方式1：连接运算。
>
> 方式2：调用String.ValueOf

![image-20220413114428990](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413114428990.png)

> String类型转基本数据类型
>
> parseXxx();

![image-20220413114631452](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413114631452.png)

#### 面试题

三元运算符的时候，会保持数据精度一致

![image-20220413114903104](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413114903104.png)

> Integer内部定义了IntegerCache结构，IntegerCache定义了Integer[],保存了-127-127范围的整数。

![image-20220413115816722](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413115816722.png)

![image-20220413115425503](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413115425503.png)

![image-20220413115511076](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/image-20220413115511076.png)

### static关键字	

#### 静态变量

![image-20220420100006109](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220420100006109.png)

![image-20220420103425811](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220420103425811.png)

```java
class Chinese {
   String name;
   int age;
   static String nation;
}

```

```java
       Chinese chinese=new Chinese();
        chinese.name="姚明";
        chinese.age=40;
        chinese.nation="中国";
        Chinese chinese2=new Chinese();
        chinese2.name="马龙";
        chinese2.age=30;
        System.out.println(chinese2.nation);//是中国，说明chinese给的值，chinese2也能读到
```

```java	
        Chinese chinese=new Chinese();
        chinese.name="姚明";
        chinese.age=40;
        chinese.nation="中国";
        Chinese chinese2=new Chinese();
        chinese2.name="马龙";
        chinese2.age=30;
        chinese2.nation="美国";
        System.out.println(chinese.nation);//是美国，说明chinese2给的值，chinese也被修改
```

static声明的随着类的加载而加载，在对象创建之前就加载好了

```java
Chinese.nation="zg";//不会报错，因为静态变量的加载早于对象的创建。
```

![image-20220420103513677](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220420103513677.png)

##### 类变量和实例变量内存解析

> nation随着类加载而加载，但是类只加载一次。

![image-20220420103801493](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220420103801493.png)

#### 静态方法

![image-20220420105226207](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220420105226207.png)

```java
class Chinese {
   String name;
   int age;
   static String nation;
   public void eat(){
       System.out.println("中国人吃中餐");
   }
    public void info(){
        name="";
        nation="";//不报错，省略是Chinese.nation,而Chinese.nation是随着类加载加载的，是一定在内存中存在的
        System.out.println("name:"+name+","+" age:"+age);
    }
    public static void show(){
        name="";//报错，name前面其实是this.name,但是类加载的时候还没有对象，所以不能使用this，super
        nation="";
        System.out.println("我是一个中国人");
    }
}
```

> 如何确定一个属性是否要声明为static的？
>
> 如何确定一个方法是否要声明为static的？

![image-20220420110218444](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220420110218444.png)

![image-20220420110828775](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220420110828775.png)



### 单例模式

![image-20220420111449674](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220420111449674.png)

![image-20220420152741292](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220420152741292.png)

![image-20220420153159264](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220420153159264.png)

> 私有化类的构造器
>
> 内部创建类的对象
>
> 提供静态方法，返回类的对象

#### 懒汉式

> 一开始不创建对象
>
> 线程不安全

```java
public class SingletonTest2 {
    public static void main(String[] args) {
        Bank2 bank2=Bank2.getInstance();
        Bank2 bank3=Bank2.getInstance();
        System.out.println(bank2 == bank3);//true
    }
}

class Bank2{
    private Bank2(){

    }
    private static Bank2 instance=null;

    public static Bank2 getInstance(){
        if (instance==null) instance=new Bank2();
        return  instance;
    }
}
```



#### 饿汉式

> 一开始就创建好对象，很饿

```java	
public class SingletonTest1 {
    public static void main(String[] args) {
        Bank bank=Bank.getInstance();
        Bank bank2=Bank.getInstance();
        System.out.println(bank == bank2);//true
    }
}

class Bank{
    private Bank(){

    }
    private static Bank instance =new Bank();

    public static Bank getInstance (){
        return instance;
    }
}
```

#### 线程安全的懒汉式

```java
class Bank{
    private Bank (){}
    private static Bank instance=null;
    public static synchronized Bank getInstance(){
        /**
         * 如果线程A，B同时到达，此时A进入到if语句代码块中，处理机调度到B，此时B也进入if语句里面，此时就会new 两份instance
         */
        if (instance==null){
            instance=new Bank();
        }
        return instance;
    }
}
```

```java
public static  Bank getInstance(){
        /**
         * 如果线程A，B同时到达，此时A进入到if语句代码块中，处理机调度到B，此时B也进入if语句里面，此时就会new 两份instance
         */
    synchronized(Bank.this){
         if (instance==null){
            instance=new Bank();
        }
        return instance;
    }
       
    }
```

上面这种方式，每次都会进入锁中，大可不必。下面来改进一波：在上面再写个if(instance==null)即可。

```java
public static  Bank getInstance(){
        /**
         * 如果线程A，B同时到达，此时A进入到if语句代码块中，处理机调度到B，此时B也进入if语句里面，此时就会new 两份instance
         */
    if(instance==null){
        synchronized(Bank.this){
         if (instance==null){
            instance=new Bank();
        }
        return instance;
    }
    }
    
    }
```



### 类中代码块的应用

类的成员之四：代码块（或初始化块）

属性，方法，构造器，代码块



通过输出我们可以发现，静态代码块和代码块和静态方法的第一个不同，就是静态代码块随着类的加载而加载，并且还随着类的执行而执行，但是静态方法虽然随着类的加载而加载，但是并没有随着类的执行而执行。

```java
class Person{
    String name;
    int age;
    static String desc="我是一个人";

    {
        System.out.println("Hello  block");
    }

    static {
        System.out.println("Hello static block");
    }
     public static void info(){
        System.out.println("我是一个快乐的人");
    }
}
```

```java
public class BlockTest {
    public static void main(String[] args) {
        String desc = Person.desc;//Hello static block
    }
}
```

发现new对象的时候，直接就执行了代码块。而且每次new对象，都执行了代码块。但是静态代码块只执行一次。

```java
public class BlockTest {
    public static void main(String[] args) {
        //先输出Hello  block
        new Person();//Hello  block
        new Person();//Hello  block
    }
}
```

![image-20220422144853368](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220422144853368.png)

![image-20220422144836860](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220422144836860.png)

#### 应用举例

![image-20220422144946185](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220422144946185.png)

![image-20220422145153756](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220422145153756.png)

### final关键字

final不能生孩子，abstract不能谈对象...

![image-20220422164933276](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220422164933276.png)

final修饰类的时候，说明类不能被继承。

final修饰方法的时候，说明方法不能被重写。

final修饰属性的时候，说明属性要随着对象创建而创建。

![image-20220422164632270](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220422164632270.png)

final修饰局部变量

```java
    public void show(){
        final int num=10;
        //num=11;报错，赋值玩就不能修改了
    }
```

final修饰局部变量形参

```java
 public void show2(final  int num){
     //num=20;报错，只能通过对象.去获取了。
    }
```

```java
  public void show2(final  int num){
        //num=10;报错
    }

    public static void main(String[] args) {
        FinalTest finalTest = new FinalTest();
        finalTest.show2(10);
       
    }
```

static能修饰变量，方法，代码块，内部类。final 能修饰 变量，方法。所以static final能修饰 方法和变量。

但是一般来说，static final 自己用来修饰方法的很少，大多用来修饰属性变成全局常量。

![image-20220422180531480](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220422180531480.png)

### 抽象类和抽象方法

![image-20220428163005974](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220428163005974.png)

<img src="https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220428163227291.png"/>

#### 抽象类

final不能生孩子，abstract不能谈对象...

abstract不能实例化。实例化是通过构造器去实例化的，那抽象类有没有构造器呢？答案是有的。

那构造器有什么用呢？

构造器是给子类实例化的时候用的，因为子类实例化会调用父类的构造器。

<img src="https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/FKJTDU)E(IHKVSBKGS24RI4.png"/>

#### 抽象方法

含有抽象方法的类，一定是抽象类。

<font color='cornflowerblue'>因为抽象方法没有方法体，不能直接通过类去调用。</font>

但是普通的类，能够直接实例化去调用方法。因为抽象类Abstract是不能实例化的，所以包含抽象方法的类一定是抽象类。但是抽象类可以没有抽象方法。

![image-20220428162859068](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220428162859068.png)

如果子类没重写直接父类和间接父类的所有抽象方法，说明子类也是抽象类。

#### 抽象类的匿名子类对象

非匿名类的非匿名对象

![image-20220428173132666](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220428173132666.png)

匿名对象

![image-20220428173052835](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220428173052835.png)

> 抽象类的匿名子类的对象

Person是一个抽象类，Person p的p是一个对象。

匿名子类，说明不知道谁是子类。但是抽象类不能实例化。这种方式的看起来像实例化，其实也算是一个子类。

![image-20220428173512844](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220428173512844.png)

>  匿名子类的匿名对象

![image-20220428173630081](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220428173630081.png)

### 模板方法设计模式

当功能内部==一部分是确定的==，==一部分是不确定的==。可以把``不确定的暴露出去``，让子类去实现。

在软件开发中实现一个算法，整体步骤固定，通用，这些步骤在父类中写好了。

但是某些部分易变，==易变部分可以抽象出来==，供不同子类实现，这就是一种模板模式。

![image-20220518093057723](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220518093057723.png)

实现如下：

```java
public class TemplateTest {
    public static void main(String[] args) {
        Template template=new SubTemplate();
        template.spendTime();
    }
}
abstract class Template{
    public  void spendTime(){
        long start=System.currentTimeMillis();
        code(); //易变的代码，不确定的部分，计算某段代码执行所需要花费的时间。
        long end=System.currentTimeMillis();
        System.out.println("花费的时间为："+(end-start));
    }
    public abstract void code();
}
class  SubTemplate extends Template{
    @Override
    public void code() {
        for (int i =2; i <=1000; i++) {
            boolean flag=true;
            for (int j = 2; j <= Math.sqrt(i); j++) {
                if (i%j==0){
                    flag = false;
                    break;
                }
            }
            if (flag) System.out.println(i);
        }
    }
}
```

比如这个银行的例子：

取号排队和反馈评分都是固定的，但是业务不一定都是一样的

![image-20220518094712145](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220518094712145.png)

有的业务是要取钱，有的业务是要理财

![image-20220518094804880](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220518094804880.png)

![image-20220518094849307](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220518094849307.png)

### 接口

#### 接口的理解

一方面：Java不支持多重继承，有了接口，可以得到多重继承的效果。

一方面：有时候必须从几个类抽取一些共同的行为特征，但是他们并不是is-a的关系，比如篮球运动员、跨栏运动员都是运动员，这就是is a的关系，大学生和中学生都是学生，这也是is-a的关系。

![image-20220518094947922](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220518094947922.png)

跨栏运动员的父类是运动员，大学生的父类是学生，但是大学生和跨栏运动员都有学习的功能，但是不能多继承，他们俩都有父类了，而且说大学生is a 技能 ，也不合适，跨栏运动员 is a 技能，也不合适。

所以这时候用接口。

![image-20220601111022958](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220601111022958.png)



![image-20220601111218012](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220601111218012.png)

#### 接口的定义和使用

##### JDK7及之前

![image-20220601112825477](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220601112825477.png)

``全局常量``

public static final

![image-20220601111719861](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220601111719861.png)

``抽象方法``

![image-20220601112407309](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220601112407309.png)

``构造器``

和抽象类不同的是，抽象类中可以有构造器，接口中不能有构造器

##### JDK8

越来越像类了

第三个是把public 省略了，但是权限还是public,不是default

![image-20220613013753225](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613013753225.png)

写一个实现类实现接口的时候，发现定义的静态方法和默认方法，子类都拿不到。

其实就是给接口自己用的：

![image-20220613014307385](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613014307385.png)

![image-20220613014043618](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613014043618.png)

> 知识点一：接口中定义的静态方法，只能通过接口来调用

![image-20220613014337129](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613014337129.png)

> 知识点二：接口越来越像类，也可以通过实例化的方式，通过子类的对象来调用接口的方法。可以免去实现了。
>
> 比如Collection接口中的这个方法：

![image-20220613015215754](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613015215754.png)

![image-20220613015432588](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613015432588.png)

> 知识点3：如果子类或者实现类，继承的父类和实现的接口声明了同名同参数的默认方法，那么子类在重写此方法的情况下，默认调用父类中的同名同参数的方法（类优先原则）

![image-20220613015727910](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613015727910.png)

调用method3（）就是父类的结果，因为SubClass同时是SuperClass和CompareA的子类。一个是类，一个是接口。类优先。

![image-20220613015820182](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613015820182.png)

> 知识点四：如果两个接口有同名方法，会报错
>
> 除非继承一个父类还有同名方法，因为父类优先级高。或者自己重写同名方法

![image-20220613015952996](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613015952996.png)

这个时候还是父类的

![image-20220613020025138](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613020025138.png)

这个时候就报错

![image-20220613020058723](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613020058723.png)

![image-20220613020129208](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613020129208.png)

> 知识点五：

![image-20220613020229968](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613020229968.png)

##### 接口的多实现、多继承

类和接口是实现

接口和接口是继承

![image-20220601113330114](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220601113330114.png)

``多实现``

![image-20220601113115203](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220601113115203.png)

``多继承``

CC就有两个抽象方法了

![image-20220601113414922](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220601113414922.png)

#### 接口的使用

接口的使用也满足多态性

![image-20220601115517503](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220601115517503.png)

驱动：接口的实现类的集合。

![image-20220601115638503](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220601115638503.png)



![image-20220601115817642](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220601115817642.png)

![image-20220601115848893](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220601115848893.png)

#### 代理模式

明星相当于是==被代理类==

经纪人相当于是==代理类==

都去实现一个接口，然后有一些方法被代理类去重写， 

本来一些明星要去做的事情，这时候都通过经纪人去完成，经纪人有一些操作，再去调用明星

##### 静态代理

![image-20220609214829269](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220609214829269.png)

 netWork.browse();就很传神了

```java	

public class NetWorkTest {
    public static void main(String[] args) {
        //没有看见代理类显示调用方法
        Server server = new Server();
        //server.browse();
        ProxyServer proxyServer = new ProxyServer(server);
        proxyServer.browse();
    }
}

interface NetWork{
    public void browse();
}
//被代理类
class Server implements NetWork{

    public void browse() {
        System.out.println("真实的服务器访问网络");
    }
}

//代理类
class ProxyServer implements NetWork{
    private NetWork netWork;
    public ProxyServer(NetWork netWork) {
        this.netWork = netWork;
    }

    public void check(){
        System.out.println("联网之前的检查工作");
    }
    public void browse() {
        check();
        netWork.browse();
    }
}

```



![](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220609214829269.png)

#### 工厂模式

![image-20220613010633523](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613010633523.png)

设计原则，一共有六个

![image-20220613010722176](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613010722176.png)

##### 无工厂模式

创建者和调用者没有分开

![image-20220613010950024](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613010950024.png)

##### 简单工厂模式

Factory体现了创建者

![image-20220613011139914](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613011139914.png)

这里体现调用者

![image-20220613011219022](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613011219022.png)

如果要多加产品，就要写一些if-else,对现有的代码进行修改了

![image-20220613011239678](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613011239678.png)

##### 工厂方法模式

先写一个接口

![image-20220613012432974](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613012432974.png)

写两个实现类

![image-20220613012515004](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613012515004.png)

再来一个工厂接口

![image-20220613012540513](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613012540513.png)

实现两个工厂类

![image-20220613012615349](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613012615349.png)

调用者

以前是Factory里面的代码要改，现在Factory是一个接口，不用修改接口内容。但是要造新车还是需要添加类和添加工厂。

![image-20220613012702874](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613012702881.png)

![image-20220613012941966](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613012941966.png)

##### 抽象工厂模式

![image-20220613013212840](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613013212840.png)

#### 笔试题

![image-20220613020349649](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613020349649.png)

接口和类是同一级别的，如果一个类的父类的父类也有x,那就是找直接父类的，此时就是2，如果父类没有x，那就找父类的父类。

接口和类是同一个级别，调用谁呢？答案：是不明确的，会报错，这和类优先不一样

![image-20220613020501976](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613020501976.png)

![image-20220613020757230](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613020757230.png)

> 笔试题2：
>
> ball有问题，属性是final的

![image-20220613020924859](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220613020924859.png)

### 内部类

![image-20220614004141601](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220614004141601.png)

![image-20220614004542793](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220614004542793.png)

#### 局部内部类

在方法，代码块以及构造器中的类，叫做局部内部类



![image-20220614004317992](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220614004317992.png)

>  如何使用？

![image-20220614005912956](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220614005912956.png)

![image-20220614010105669](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220614010105669.png)

#### 成员内部类

>  能做什么？

![image-20220614005238762](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220614005238762.png)

![image-20220614004451550](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220614004451550.png)

> 如何使用？

![image-20220614005438913](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220614005438913.png)

有重名的话怎么办？

![image-20220614005646428](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220614005646428.png)

## 异常

### 概述和体系结构

![image-20220518115935565](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220518115935565.png)

#### Error

JVM内部错误

![image-20220518120125135](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220518120125135.png)

#### Exception

编程错误或者偶然的外在因素

![image-20220518120231552](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220518120231552.png)

==顶级父类：Throwable==

![image-20220614010933788](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220614010933788.png)

![image-20220518120332639](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220518120332639.png)

##### 编译性异常

![image-20220518120451696](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220518120451696.png)

##### 运行时异常

<img src="https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220518120451696.png"/>

### 常见异常

![image-20220518120523103](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220518120523103.png)

InputMismathException，比如scanner.nextInt，你输入String

ArithmeticException:6/0

### 异常处理机制

``抓抛模型``

==抛==：程序在正常执行的过程中，一旦出现异常，在异常代码处生成一个对应的异常类的对象，将对象抛出，==一旦抛出对象之后，其后的代码就不再执行。==

==抓==：两种处理方式

![image-20220518121415291](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220518121415291.png)

#### 1:(==抓==)try-catch-finally

比如狼进羊村了，小牧羊人自己有能力解决，用石头扔，把狼赶走了，这就是第一种方式，try-catch-finally。

再比如看病，小医院能解决就解决了

![image-20220518120719012](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220518120719012.png)

![image-20220519161252348](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220519161252348.png)

##### finally

![image-20220519160819394](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220519160819394.png)

如果异常捕获对了，也就是catch对了，finally中的代码和不在finally的代码是一样执行的

我好帅啊这句话都能打印出来。

![image-20220519155933038](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220519155933038.png)

``第一种情况``:catch中还有错误没有捕获到

这时候finally也一定会执行，但是用sout语句，就==不能==执行了。

![image-20220519160159789](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220519160159789.png)

``第二种情况`:在没有异常的时候，在try里面就return了，或者程序在哪个地方return了，finally还是会执行

![image-20220519160414196](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220519160414196.png)

如果改一下，这样写：在finally里面return 3,那么输出几呢，答：输出3，因为在catch return 之前，先执行finally，执行finally的时候发现return了，这时候函数结束了，不执行catch里面的东西了

![image-20220519160500859](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220519160500859.png)

#### 2:(==抓==)throws

比如狼进羊村了，小牧羊人自己有能力解决，用石头扔，但是这个狼比较牛逼，赶不走，牧羊人就开始喊人，其他人就过来了。把异常往上抛，抛给成人，成人解决不了，就抛给军队。

再比如看病，小医院能解决就解决了，解决不了就throws给上面的大医院。

![image-20220519162121899](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220519162121899.png)

这个哈哈哈就不会执行

![image-20220519162407193](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220519162407193.png)

### 重写方法抛出异常规则

![image-20220614011445199](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220614011445199.png)

如果父类没抛异常，子类也就不能抛异常了

#### 选try...还是throws?

第一点是重写方法抛出异常规则

![image-20220614234522972](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220614234522972.png)

依次调用三个方法，三个方法是递进的关系，什么叫递进呢？比如A方法得出的结论，要给B方法用，B方法得出的结论给C方法用。

恰好三个方法都有可能出异常，这时候如何使用？

此时最好不要try-catch-finally,三个方法最好先throws抛出异常，最后再整体用try-catch。为什么呢？

比如A方法出现了异常，但是A方法的异常被处理掉了，但是A方法出现了异常，得出的结果，B不一定能用。

其实这时候都没必要往下运行了，因为反正也是错误的数据了，如果用try-catch-finally还会执行后面的代码，但是执行也是错的。

用throws就不会执行下面的代码了。

### (==抛==)手动抛出异常:throw

![image-20220614235155171](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220614235155171.png)

![image-20220614235223112](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220614235223112.png)

> 如果抛一个大的异常的话，因为Exception包含运行时异常和编译时异常，这时候就会提示你去处理。
>
> 要么就throws，要么就是try-catch

![image-20220614235414819](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220614235414819.png)

假设用throws抓

![image-20220614235556736](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220614235556736.png)

 e.getMessage就是自己输入的提示

![image-20220614235633406](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220614235633406.png)

### 用户自定义异常类

网络中传对象。对象有序列号。怎么证明A电脑传的对象给B，B接收的是A传的对象？答：通过比较序列号

![image-20220615000040219](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220615000040219.png)

## 多线程

### 基本概念

#### 线程和进程

![image-20220618133648865](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220618133648865.png)

堆和方法区是每一个进程一份，

虚拟机栈和程序计数器是每个线程一份。

但是一个进程有多个线程，这就意味着每个线程要共享==方法区==和==堆==。JVM调优也是针对于共享的模块进行调优的。

![image-20220618134344454](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220618134344454.png)

#### 并行和并发

![image-20220618134953500](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220618134953500.png)

#### 多线程优点

![image-20220618194903883](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220618194903883.png)

#### 何时需要多线程

比如手机，比如ListView网络加载Item,其实往下滑和图片下载，是两个线程在做的。为什么要两个线程呢？

如果是一个线程，如果图片没下载完的话，往下滑就划不动，卡顿。

两个线程就不会出现卡顿的情况。

![image-20220618195739924](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220618195739924.png)

### 线程的创建和使用

![image-20220618200008454](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220618200008454.png)

#### 方式一：继承Thread类

![image-20220618200910571](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220618200910571.png)

通过过下面的例子演示了主线程和子线程是有交互性的，执行顺序可能不一样。

同时也演示了线程创建过程。

```java	
package com.liaoqunfeng.Thread;


class  MyThread extends Thread{
    @Override
    public void run() {
        for (int i = 0; i <100 ; i++) {
            if (i%2==0) System.out.println(i);
        }
    }
}
public class ThreadTest {
    public static void main(String[] args) {
        MyThread myThread = new MyThread();
        myThread.start();
        for (int i = 0; i <100 ; i++) {
            if (i%2==0) System.out.println(i+"********************主线程*********************");
        }
    }
}

```

![image-20220618201059197](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220618201059197.png)

##### start()方法

两个作用：启动当前线程

调用当前线程的run()方法

将上面的代码改一下，不写start()方法，只写run()方法的话呢？

这时候就不会有上图的交互性了，永远只会有一个结果，那就是看代码执行顺序，先调用run()方法里面的语句，再执行main()方法。

因为此时压根没有两个线程了。线程没通过start()方法启动，仅仅是调用了run()方法。

```java
class  MyThread extends Thread{
    @Override
    public void run() {
        for (int i = 0; i <100 ; i++) {
            if (i%2==0) System.out.println(i);
        }
    }
}
public class ThreadTest {
    public static void main(String[] args) {
        MyThread myThread = new MyThread();
        myThread.run();
        for (int i = 0; i <100 ; i++) {
            if (i%2==0) System.out.println(i+"********************主线程*********************");
        }
    }
}
```

如何证明一下呢：使用Thread.currentThread().getName(),发现打印出来都是main的

```java
class  MyThread extends Thread{
    @Override
    public void run() {
        for (int i = 0; i <100 ; i++) {
            //if (i%2==0) System.out.println(i);
            if (i%2==0) System.out.println(i+Thread.currentThread().getName());
        }
    }
}
public class ThreadTest {
    public static void main(String[] args) {
        MyThread myThread = new MyThread();
        myThread.run();
        for (int i = 0; i <100 ; i++) {
            //if (i%2==0) System.out.println(i+"********************主线程*********************");
            if (i%2==0) System.out.println(i+Thread.currentThread().getName());
        }
    }
}

```

##### start()方法单个线程只能一次

start()方法只能让他start一次，不可以通过同一个线程再去start一次。

start一次之后，会改变threadStatus让他不等于0；之后会抛出异常。

```java
class  MyThread extends Thread{
    @Override
    public void run() {
        for (int i = 0; i <100 ; i++) {
            //if (i%2==0) System.out.println(i);
            if (i%2==0) System.out.println(i+Thread.currentThread().getName());
        }
    }
}
public class ThreadTest {
    public static void main(String[] args) {
        MyThread myThread = new MyThread();
        myThread.start();
        myThread.start();
        for (int i = 0; i <100 ; i++) {
            //if (i%2==0) System.out.println(i+"********************主线程*********************");
            if (i%2==0) System.out.println(i+Thread.currentThread().getName());
        }
    }
}
```

![image-20220618203038271](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220618203038271.png)

![image-20220618202844241](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220618202844241.png)

#### Thread类的常用方法

![image-20220622121719529](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220622121719529.png)

##### void start()

启动线程，并且执行对象的run()方法

##### run()

线程被调度时执行的操作

##### String getName()

返回线程的名称。

每次线程执行的时候，默认都会起一个名字，从0开始。

![image-20220622115842187](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220622115842187.png)

![image-20220622115852003](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220622115852003.png)

##### void setName()

设置线程名称.

在start之前设置名字。

```java	
public class ThreadMethodTest {
    public static void main(String[] args) {
        HelloThread helloThread = new HelloThread();
        helloThread.setName("线程一");
        helloThread.start();
        //给主线程起名字
        Thread.currentThread().setName("主线程");
        for (int i = 0; i <100 ; i++) {
            if (i%2==0) System.out.println(Thread.currentThread().getName()+":"+i);
        }
    }
}

class HelloThread extends Thread{
    @Override
    public void run() {
        for (int i = 0; i <100 ; i++) {
            if (i%2==0) System.out.println(Thread.currentThread().getName()+":"+i);
        }
    }
}
```

方式二：

![image-20220622120243837](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220622120243837.png)

```java
class HelloThread extends Thread{
    public HelloThread(String name) {
        super(name);
    }
}
 public static void main(String[] args) {
        HelloThread helloThread = new HelloThread("线程一");
        //helloThread.setName("线程一");
        helloThread.start();
        //给主线程起名字
        Thread.currentThread().setName("主线程");
        for (int i = 0; i <100 ; i++) {
            if (i%2==0) System.out.println(Thread.currentThread().getName()+":"+i);
        }
    }
```



##### static Thread currentThread()

返回当前线程。在Thread子类中就是this,通常用于主线程和Runnable实现类

##### static void yield()

线程让步。

暂停当前执行的线程，把执行机会让给优先级==相同==或者==更高==的线程。

若队列中没有同等优先级的线程，忽略此方法。

线程到能取模20的时候，就让出处理机，让出处理机之后，可能这时候主线程抢到了处理机。

也可能主线程还是没抢到，虽然让出了，但是HelloThread还是抢到了处理机。

就算主线程抢到了处理机，线程也会调度回来HelloThread。此时两个线程都是就绪态。

```java
class HelloThread extends Thread{
    public HelloThread(String name) {
        super(name);
    }

    @Override
    public void run() {
        for (int i = 0; i <100 ; i++) {
            if (i%2==0) System.out.println(Thread.currentThread().getName()+":"+i);
            if (i%20==0) yield();
        }

    }
}
```



##### join()

当某个程序执行流中调用其他线程的join()方法时，调用线程将被阻塞，直到join()方法加入的join线程执行完为止。

低优先级的线程也可以获得执行。

i==20哦，主线程到20的时候，就会让helloThread全部执行完！主线程会变成阻塞态。

```java	
public class ThreadMethodTest {
    public static void main(String[] args) {
        HelloThread helloThread = new HelloThread("线程一");
        //helloThread.setName("线程一");
        helloThread.start();
        //给主线程起名字
        Thread.currentThread().setName("主线程");
        for (int i = 0; i <100 ; i++) {
            if (i%2==0) System.out.println(Thread.currentThread().getName()+":"+i);
            if (i==20) {
                try {
                    helloThread.join();
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}
```



##### static void sleep()

指定时间：毫秒

令当前活动线程在指定时间段内放弃对CPU的控制，使其他线程有机会被执行， 时间到后重排队。

抛出InterrupuedException异常。

阻塞一秒钟。

```java
class HelloThread extends Thread{
    public HelloThread(String name) {
        super(name);
    }

    @Override
    public void run() {
        for (int i = 0; i <100 ; i++) {
            if (i%2==0) System.out.println(Thread.currentThread().getName()+":"+i);
            try {
                sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            // if (i%20==0) yield();
        }

    }
}
```

![image-20220622121637642](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220622121637642.png)

##### stop()

强制线程生命期结束，不推荐使用。

Deprecated，过时的意思。

![image-20220622121343108](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220622121343108.png)

##### boolean isAlive()

返回boolean，判断线程是否还活着

#### 线程调度

![image-20220622121906742](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220622121906742.png)

##### 线程优先级

![image-20220622122027318](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220622122027318.png)

![image-20220622122240618](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220622122240618.png)

#### 方式二：实现Runnable接口

![image-20220623190408749](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220623190408749.png)



```java
public class RunnableTest {
    public static void main(String[] args) {
        MThread mThread = new MThread();
        new Thread(mThread).start();
    }
}

class MThread implements Runnable {
    public void run() {
        for (int i = 0; i < 100; i++) {
            if (i % 2 == 0) System.out.println(i);
        }
    }
}
```

本来我们的start方法是能执行当前类的run方法，但是此时的类是Thread类，run方法按道理是空的，那是怎么执行到Runnable里面的run方法的呢？看看源码，再结合上一张图的构造器传了个target.答案显而易见了。

![image-20220623191939901](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220623191939901.png)

![image-20220623191951928](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220623191951928.png)

怎么启动两个线程呢？

```java
public class RunnableTest {
    public static void main(String[] args) {
        MThread mThread = new MThread();
        new Thread(mThread).start();
        new Thread(mThread).start();

    }
}
```

#### 两种创建方式的选择

Thread类也是先了Runnable接口

![image-20220623192917561](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220623192917561.png)

#### 卖票问题

##### Thread类

存在线程安全问题，待解决。

另外我们的ticket是使用static的，来保证三个线程用一份资源。

```java
public class WindowTest {
    public static void main(String[] args) {
        Window window = new Window();
        window.setName("窗口1:");
        Window window1 = new Window();
        window1.setName("窗口2:");
        Window window2 = new Window();
        window2.setName("窗口3:");
        window.start();
        window1.start();
        window2.start();
    }
}
class Window extends Thread{
   private static int ticket=100;

    @Override
    public void run() {
        while (true){
            if (ticket>0){
                System.out.println(getName()+"票号为："+ticket);
                ticket--;
            }else {
                System.out.println("票卖完了");
                break;
            }
        }
    }
}
```

会出现三个窗口在卖同一张票。

![image-20220622123445801](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220622123445801.png)

##### Runnable接口

Thread类需要static 修饰。但是Runnable接口方式不需要用static ,因为只有一个对象

```java
class Window1 extends Thread{
    private  int ticket=100;

    @Override
    public void run() {
        while (true){
            if (ticket>0){
                System.out.println(getName()+"票号为："+ticket);
                ticket--;
            }else {
                System.out.println("票卖完了");
                break;
            }
        }
    }
}

public class WindowTest {
    public static void main(String[] args) {
        Window1 window1 = new Window1();
        new Thread(window1).start();
        new Thread(window1).start();
        new Thread(window1).start();
    }
}

```



### 线程生命周期

![image-20220623195308175](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220623195308175.png)

```java
 public enum State {
        NEW,
        RUNNABLE,
        BLOCKED,
        WAITING,
        TIMED_WAITING,
        TERMINATED;
    }
```

suspend()线程挂起，但是过时了。

resume()，和suspend()搭配使用，结束挂起状态。

![image-20220623200300790](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220623200300790.png)

### 线程同步

#### 理解线程安全问题

![image-20220623200845189](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220623200845189.png)

#### 线程安全问题的举例和解决

![image-20220627112206089](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627112206089.png)

场景一：买票重票

![image-20220627110628801](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627110628801.png)

场景二：买票错票

加入线程休眠的代码ticket已经被别人改成了0了，但是此时窗口三已经执行到休眠的代码，if不起作用，继续往下执行。

![image-20220627110846829](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627110846829.png)

![image-20220627111819222](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627111819222.png)

![image-20220627111857589](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627111857589.png)

##### 同步机制解决Runnable

![image-20220627120204941](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627120204941.png)

###### 同步代码块

synchronized

每次都需要去New一个对象，太繁琐了。可以写成this,this代表的就是当前window2的对象

synchronized (this)

```java
class Window2 implements Runnable{
    private  int ticket=100;
    /**
     * 任何对象都能充当锁，因为是实现了Runnable接口，所以只有一个对象，所以三个线程是共用
     * 一把锁的，如果放在run方法里面，那情况就不一样了。那就是三个线程用三把锁，不能解决线程安全问题。
     * 比如在高铁上上厕所，大家都有共同的共识，厕所红灯就不能进去。如果每个人对厕所有没有人的标准都不一样，
     * 那就不能保证正在上厕所的人安全了
     */
    Object object=new Object();
    @Override
    public void run() {
        while (true){
            synchronized (object){
                if (ticket>0){
                    System.out.println(Thread.currentThread().getName()+"票号为："+ticket);
                    ticket--;
                }else {
                    System.out.println("票卖完了");
                    break;
                }
            }

        }
    }
}

public class WindowTest {
    public static void main(String[] args) {
        Window2 window2=new Window2();
        new Thread(window2).start();
        new Thread(window2).start();
        new Thread(window2).start();


        /*Window1 window1=new Window1();
        window1.start();
        Window1 window11=new Window1();
        window11.start();
        Window1 window12=new Window1();
        window12.start();*/


    }
}
}
```

三个线程去操作票，谁抢到了，就会进入run方法，并且加锁。

![image-20220627114748920](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627114748920.png)

每次执行完了一次run()方法，打印好了车票，就会自动释放同步代码块

![image-20220627114905314](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627114905314.png)

> 什么叫不能synchronized不能包多了，也不能包少了？

包少了肯定不行，包多了有两个问题，一个是性能会变低。本来有的代码是能并行的执行的。另外一个是代码逻辑都可能发生变化。

比如这个把while true包含进去了，此时就只会有一个进程把票卖完了。

![image-20220627120835893](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627120835893.png)

###### 同步方法

理解第二点看Thread使用同步方法

![](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627122016174.png)

如果一个方法完整的都是同步数据，就可以直接声明为同步方法。但是能像图中这样写吗？答案是不能的。因为这样就包多了。一进去就只能有一个线程while(true)

![image-20220627121216100](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627121216100.png)

```java
class Window3 implements Runnable{
   private  int ticket=100;

    @Override
    public void run() {
        while (true){
             show();
        }

    }
    private synchronized void show(){
        if (ticket>0){
            System.out.println(Thread.currentThread().getName()+"票号为："+ticket);
            ticket--;
        }
    }
}
```



##### 同步机制解决Thread

###### 同步代码块

1.此时能用上面同步代码块中任意一个对象吗？答案是不能的，因为继承的方式造了多个对象。

2.此时能用synchronized(this)吗？答案是不能的，因为当前对象有三个

那怎么办呢？能直接写成 synchronized (Window1.class).不是说synchronized 里面的锁是对象吗？为什么类也可以？

因为类也是对象。讲到反射的时候再说。

Class class=Windows1.class;

而且这个类是唯一的，类只会加载一次。

```java
class Window1 extends Thread{
    private static int ticket=100;
    private static Object object=new Object();
    @Override
    public void run() {
        synchronized (object){
            while (true){

                if (ticket>0){
                    System.out.println(getName()+"票号为："+ticket);
                    ticket--;
                }else {
                    System.out.println("票卖完了");
                    break;
                }
            }
        }
        
    }
}
```

###### 同步方法

![image-20220627122016174](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627122016174.png)

这时候安全吗？不安全。锁的问题。

为什么呢？因为同步方法的 synchronized 也就是this.这时候怎么办?

```java
class Window extends Thread{
   private static int ticket=100;

    @Override
    public void run() {
        while (true){
            show();
        }
    }

    private synchronized void show(){
        if (ticket>0){
            System.out.println(getName()+"票号为："+ticket);
            ticket--;
        }
    }
}
```

private static synchronized void show,这时候不是this是谁？是当前类。

```java
class Window extends Thread{
   private static int ticket=100;

    @Override
    public void run() {
        while (true){
            show();
        }
    }

    private static synchronized void show(){
        if (ticket>0){
            System.out.println(Thread.currentThread().getName()+"票号为："+ticket);
            ticket--;
        }
    }
}

```

##### Lock锁

![image-20220627160701033](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627160701033.png)

`面试题： `

```java
class Window6 implements Runnable{
    private  int ticket=100;
    /**
     * 一种有参数，一种没参数。
     * 不写参数默认是false，不公平
     * 有参数的是一个boolean类型的值，表示公平还是不公平，写true就是公平。
     */
    private ReentrantLock reentrantLock=new ReentrantLock();
    @Override
    public void run() {
        while (true){
            try {
                reentrantLock.lock();
                if (ticket>0){

                    System.out.println(Thread.currentThread().getName()+"票号为："+ticket);
                    ticket--;
                }
            }catch (Exception e){

            }finally {
                //解锁
                reentrantLock.unlock();
            }

        }

    }

}
```

![image-20220627160649548](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627160649548.png)

#### 死锁问题

![image-20220627154447689](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627154447689.png)

```java
public class DeadLockTest {
    public static void main(String[] args) {
        StringBuffer s1=new StringBuffer();
        StringBuffer s2=new StringBuffer();
        new Thread(){
            @Override
            public void run() {
                synchronized (s1){
                    s1.append("a");
                    s2.append("1");
                    try {
                        Thread.sleep(100);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                    synchronized (s2){
                        s1.append("b");
                        s2.append("2");
                        System.out.println(s1);
                        System.out.println(s2);
                    }
                }
            }
        }.start();


        new Thread(new Runnable() {
            @Override
            public void run() {
                synchronized (s2){
                    s1.append("b");
                    s2.append("3");
                    try {
                        Thread.sleep(100);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                    synchronized (s2){
                        s1.append("d");
                        s2.append("4");
                        System.out.println(s1);
                        System.out.println(s2);
                    }
                }
            }
        }).start();
    }
}
```



### 线程通信

![image-20220627165153106](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627165153106.png)

交替打印

```java	
public class CommunicationTest {
    public static void main(String[] args) {
        Number number = new Number();
        Thread thread1=new Thread(number);
        Thread thread2=new Thread(number);
        thread1.start();
        thread2.start();
    }
}

class Number implements Runnable{
    private int number=1;

    @Override
    public void run() {
        while (true){
            synchronized (this){
                /**
                 * 这里是两个线程，交替打印，所以用Notify()即可。就是唤醒一个进程
                 *如果有三个进程，要唤醒两个进程的话，那就notifyAll()
                 */
                notify();
                if (number<100){
                    System.out.println(Thread.currentThread().getName()+":"+number);
                    number++;
                    try {
                        /**
                         * 调用wait()方法的线程阻塞,wait会释放锁，
                         * 和sleep不一样。sleep比如你在厕所睡着了，但是锁你还是不会释放
                         * 虽然都是在阻塞状态，但是wait会释放锁，sleep不会释放锁
                         */
                        wait();
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }else {
                    break;
                }
            }

        }
    }
}

```

![image-20220627164746477](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627164746477.png)

#### wait()和sleep()的异同

`面试题`

wait()会释放锁，sleep()不会释放锁

![image-20220627165604102](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627165604102.png)

#### 生产者消费者问题

![image-20220627165901278](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627165901278.png)

```java	
public class ProductTest {
    public static void main(String[] args) {
        Clerk clerk = new Clerk();
        Producer producer = new Producer(clerk);
        producer.setName("生产者1");
        Consumer consumer = new Consumer(clerk);
        consumer.setName("消费者1");
        producer.start();
        consumer.start();
    }
}

class Producer extends Thread {
    private Clerk clerk;

    public Producer(Clerk clerk) {
        this.clerk = clerk;
    }

    @Override
    public void run() {
        while (true) {
            System.out.println(getName() + "开始生产产品.....");

            clerk.produceProduct();

        }
    }
}

class Consumer extends Thread {
    private Clerk clerk;

    public Consumer(Clerk clerk) {
        this.clerk = clerk;
    }

    @Override
    public void run() {
        System.out.println(getName() + "开始生产产品.....");

        clerk.consumeProduct();

    }
}


class Clerk {
    private int productCount=0;
    //此时synchronized是Clerk的，所以就一个对象。很nice
    public synchronized void produceProduct() {
        if (productCount<20){
            productCount++;
            System.out.println(Thread.currentThread().getName()+"开始生产第"+productCount+"个产品");
            //唤醒消费者
            notify();
        }else {
            //wait必须写在同步代码块
            try {
                wait();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }

    public synchronized void consumeProduct() {
        if (productCount>0){
            System.out.println(Thread.currentThread().getName()+"开始消费第"+productCount+"个产品");
            productCount--;
            //提醒生产者能生产了
            notify();
        }else {
            try {
                wait();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}
```



### JDK5新增线程创建方式

#### 实现Callable接口

![image-20220627172414428](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627172414428.png)

![image-20220627171359770](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627171359770.png)

```java
public class CallableTest {
    public static void main(String[] args) {
        Number1 number1 = new Number1();
        FutureTask futureTask = new FutureTask(number1);
        FutureTask<Integer> futureTask1 = new FutureTask<Integer>(number1);
        //因为FutureTask实现了Runnable,这里也用到了多态
        new Thread(futureTask).start();
        try {
            //get()方法的返回值就是call()的返回值,如果futureTask不写泛型，就还是返回Object
            Object sum = futureTask.get();
            //如果写泛型就能是泛型规定的
            Integer sum2 = futureTask1.get();
            System.out.println(sum);
        } catch (InterruptedException e) {
            e.printStackTrace();
        } catch (ExecutionException e) {
            e.printStackTrace();
        }
    }
}
class Number1 implements Callable<Integer>{

    @Override
    public Integer call() throws Exception {
        int sum=0;
        for (int i = 0; i <100 ; i++) {
            sum+=i;
            if (i%2==0) System.out.println(i);
        }
        return sum;
    }
}
```



#### 使用线程池

好玩的例子：比如要出去玩，但是这个时候没有车，那这个时候是造一辆车还是？做公交车呢？以前的方式就是要出去的时候，自己造一辆车。

##### 背景

![image-20220627173350383](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627173350383.png)

##### API

![image-20220627173823761](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627173823761.png)

##### 使用

![image-20220627175250871](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627175250871.png)

![image-20220627174340674](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627174340674.png)

```java
public class ThreadPool {
    public static void main(String[] args) {
        ExecutorService executorService = Executors.newFixedThreadPool(10);
        /**
         * 为什么要ExecutorService要变成ThreadPoolExecutor？
         * 因为ThreadPoolExecutor是一个类。你要设置一些属性的话，肯定是用类。不能用接口
         * 因为接口的属性都是public static final的常量
         */
        ThreadPoolExecutor executorService1 = (ThreadPoolExecutor) executorService;
        //设置一些属性...
        //executorService1.setKeepAliveTime(1000);
        executorService1.setCorePoolSize(15);
        //适合Callable
       // executorService.submit();
        //适合Runnable

        executorService.execute(new NumberThread());
        executorService.execute(new NumberThread1());
        executorService.shutdown();
    }
}
class  NumberThread implements Runnable{
    @Override
    public void run() {
        for (int i = 0; i <100 ; i++) {
            if (i%2==0) System.out.println(i);
        }
    }
}

class  NumberThread1 implements Runnable{
    @Override
    public void run() {
        for (int i = 0; i <100 ; i++) {
            if (i%2!=0) System.out.println(i);
        }
    }
}

class  NumberThread2 implements Callable {
    @Override
    public Object call() throws Exception {
        return null;
    }
}
```



## Java常用类

### 字符串

#### String

![image-20220627194351951](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627194351951.png)

![image-20220627195456439](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627195456439.png)

##### 不可变性

![image-20220627195937980](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627195937980.png)

![image-20220627200243050](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627200243050.png)

> 1。char[] value

此时如果

s1="Hello";会怎么样？

答：因为String底层是一个public static final 的一个 char[] value,他是不可变的，不可能会从abc扩容成Hello.此时只会新造一个常量地址。

![image-20220627195413446](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627195413446.png)

![image-20220627195754097](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627195754097.png)

> 2. +=

如果用+=

![image-20220627195900604](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627195900604.png)

> replace

之前是因为数组长度变了，不行。现在连对数组内容修改都不行了。如果要修改就只能重新造。

![image-20220627200114957](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627200114957.png)

![image-20220627200304808](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627200304808.png)

##### 不同创建方式

![image-20220627200353832](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627200353832.png)

![image-20220627201114998](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627201114998.png)

![image-20220627201215119](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627201215119.png)

![image-20220627201343222](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627201343222.png)

![image-20220627201628881](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627201628881.png)

`面试题`

![image-20220627201546082](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627201546082.png)

##### 不同拼接方式

![image-20220627202427061](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627202427061.png)

只要有对象参与，就是在堆空间。

只要都是字面量，就是在方法区的常量池。

![image-20220627201950312](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627201950312.png)

intern()方法。intern()方法的返回值都是常量池的。

![image-20220627202204309](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627202204309.png)

##### 面试题

说好的，引用地址类型是地址传递呢？为什么此时变成了值传递，因为String是不可变类。

str把地址传给change里面的str了。此时change里的str是good，但是后面又字面量的形式改成了test ok,所以就是两个地址了。一个指向堆空间，一个指向栈空间。

![image-20220627203039675](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627203039675.png)

##### 常用方法1

![image-20220627203529265](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627203529265.png)

```java
@Test
    public void test(){
        String s1="helloWorld";
        //1.length()
        System.out.println(s1.length());//10
        //2.charAt()
        System.out.println(s1.charAt(0));//下标从0开始，h
        System.out.println(s1.charAt(0));//下标从0开始，d
        //3.isEmpty()
        System.out.println(s1.isEmpty());//false
        //4.toLowerCase()
        String s2 = s1.toLowerCase();////String不可变，s1仍然是原来的字符串，s2是修改后的
        System.out.println(s2);
        String s3="   he  ll o Wor  ld    ";
        //5.trim()
        String s4 = s1.trim();//去除首尾的空格
        System.out.println(s3);//   he  ll o Wor  ld
        System.out.println(s4);//he ll o Wor ld
        //6.concat,等价“+”

        //7.compareTo
        String s5="abc";//c:99
        String s6="abe";//e:101
        System.out.println(s5.compareTo(s6));//就是s5去减s6

        String s7="北京尚硅谷教育";
        String s8 = s7.substring(2);
        System.out.println(s8);//尚硅谷教育
        //两个参数是左闭右开的
        String s9 = s7.substring(2,5);
        System.out.println(s9);//尚硅谷

    }
```

##### 常用方法2

![image-20220627205500298](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627205500298.png)

```java
@Test
    public void test1(){
        String s1="helloWorld";
        //1.endsWith()
        boolean ld = s1.endsWith("ld");
        System.out.println(ld);//true
        //2.startWith()
        boolean ll = s1.startsWith("ll");
        System.out.println(ll);//false
        //3.startWith(),从第二个开始
        boolean ll1 = s1.startsWith("ll", 2);
        System.out.println(ll1);//true

        String s2="woR";
        boolean contains = s1.contains(s2);
        System.out.println(contains);//false

        //4.indexof()
        System.out.println(s1.indexOf("ll"));//2

        System.out.println(s1.indexOf("ll",5));//从w开始往后找ll，-1

        String str3="hellorWorld";
        System.out.println(str3.lastIndexOf("or"));//从左边往右边找，找到最后一个or.//7
        System.out.println(str3.lastIndexOf("or",6));//从6开始往左边找，找or----4 
```

##### 常用方法3

![image-20220627210431082](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627210431082.png)

### 日期

### 比较器

### System类

### Math类

### BigInteger和BigDecimal

## 枚举类

## 集合

### Collection接口

单列数据

![image-20220627210728685](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627210728685.png)

![image-20220627210826913](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627210826913.png)

### Map接口

双列数据

![image-20220627211314480](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627211314480.png)

LinkedHashMap是HashMap的一个实现类。

Properties是HashTable的一个实现类。

![image-20220627214552790](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627214552790.png)

`面试题`

![image-20220627214748532](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627214748532.png)

#### Map存储特点

Key是用Set存储的，无序。不能重复---Set

Value可以重复，无序。因为Key是无序。---Collection

键值对就是Entry。因为Key不能重复，所以Entry肯定也不能重复。因为Key无序，Entry肯定也无序。所以可以用Set装。

![image-20220627215356026](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220627215356026.png)

## 泛型与File

## IO流

## 反射



