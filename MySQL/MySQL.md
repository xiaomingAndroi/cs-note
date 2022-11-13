# MySQL

# 基础部分

## MySQL概述

### 数据库相关概念

SQL为操作关系型数据库提供了一套统一的标准

![image-20220606000116364](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606000116364.png)

``主流的关系型数据库管理系统``

![image-20220606000359335](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606000359335.png)

![image-20220606000423949](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606000423949.png)

### 准备MySQL数据库

#### 版本

![image-20220606000848863](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606000848863.png)

#### 下载

[MySQL :: Download MySQL Installer](https://dev.mysql.com/downloads/windows/installer/8.0.html)

![image-20220606001151982](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606001151982.png)

或者进入官网下载社区版

[MySQL :: MySQL Downloads](https://www.mysql.com/downloads/)

![image-20220606001111408](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606001111408.png)

社区版的在这里：

[MySQL :: MySQL Community Downloads](https://dev.mysql.com/downloads/)

MYSQL SUSE Repository 是Linux版本的

![image-20220606001411580](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606001411580.png)

一直点next

![image-20220606002101459](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606002101459.png)

到这里点击Execute

![](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606002223072.png)

看见了端口号等信息，不用任何修改，直接点击Next

![image-20220606002310923](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606002310923.png)

到这里也是Next

![image-20220606002400167](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606002400167.png)

这样就到了账户和角色的页面，设置一下账户和密码

![image-20220606002456499](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606002456499.png)

这里我们能看见，MySQL会注册一个服务，服务名称是MySQL80，并且会随着系统开机自启

直接点击Next即可

![image-20220606002619176](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606002619176.png)

到了应用配置的页面，等待一会儿，点击Finish即可

![image-20220606002650626](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606002650626.png)

这里点击Cancle即可

![image-20220606002738661](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606002738661.png)

#### 启动与停止

`win+R之后`

输入services.msc

![image-20220606003011822](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606003011822.png)

也可以在``cmd``中输入

注意这个80是什么东西，刚才我们安装的时候，直接有的MYSQL80的噢，但是不一定每个MYSQL服务的名字都是MYSQL80

![image-20220606003213992](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606003213992.png)

#### 客户端连接

方式1

![image-20220606003344242](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606003344242.png)

方式2

![image-20220606003439121](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606003439121.png)

#### 配置环境变量

![image-20220606003502159](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606003502159.png)

在系统变量里面

![image-20220606003543380](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606003543380.png)

#### MySQL数据模型

![image-20220606003707192](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606003707192.png)

![image-20220606003757167](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606003757167.png)

![image-20220606003843142](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606003843142.png)

## SQL

### SQL通用语法

![image-20220606004118220](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606004118220.png)

### SQL分类

![image-20220606004303629](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606004303629.png)

#### DDL-数据定义

##### 数据库操作

在MySQL数据库中，设置数据库的字符集不建议设置成UTF-8,UTF8存储的长度就是3个字节，一个汉字就是三个字节，但是数据库中一些特殊的字符是占四个字节的，所以这时候使用utf8mb4,是支持四个字节的。

![image-20220606004459395](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606004459395.png)

##### 表操作-创建&查询

create table

desc

![image-20220606012219656](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606012219656.png)

![image-20220606012421971](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606012421971.png)

```mysql
 create table tb_user(
     id int comment '编号',
     name varchar(50) comment '姓名',
     age int comment '年龄',
     gender varchar(1) comment '性别'
     ) comment '用户表';
```

```mysql
DESC tb_user
```

![image-20220606013232134](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606013232134.png)

```mysql
	show CREATE TABLE tb_user
```

![image-20220606013403514](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220606013403514.png)

##### 数据类型

###### `数值类型`

![image-20220607004532652](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220607004532652.png)

Decimal中什么是精度，什么是标度，比如123.45，精度是5，标度是2

double和float:

![image-20220607005210449](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220607005210449.png)

举例子：比如要描述年龄和分数

年龄可以用占用一个字节的tinyInt,但是年龄不会有负数，所以是 age tinyint unsignd

score可能有小数，0~100，可以指定两个参数，一个是最长长度，一个是允许出现几位小数？

double(4,1),表示最长四位数，比如100.0,最长允许出现一位小数。

###### `字符类型`

除了CHAR,VARCHAR之外，带BLOB的是描述二进制数据（视频，音频）的，带TEXT的是描述文本数据的

![image-20220607005814718](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220607005814718.png)

现在来详细看看char和varchar，都可以用后面的参数指定最大的空间，超出就会报错

char:定长字符串，比如char(10)，不足10个字节长度的话，会用空格补齐。---》性能好

varchar:变长字符串，比如varchar(10),会根据你存储的内容去计算当前所占用的空间。---》性能不好，因为要计算

场景：

比如用户名，username是用varchar还是char?因为用户名不知道用户输入的长度是多少，所以用varchar,因为这样更省空间。

比如性别，gender不是男就是女，就可以用char(1)

###### `日期类型`

一般来说，用DATE,TIME,DATETIME会更多一些，TIMESTAMP范围到2038年

![image-20220607010731790](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220607010731790.png)

 比如描述生日： birthday用哪个类型最准确？很显然是DATE类型

`下面来看一个案例`

![image-20220607010940336](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220607010940336.png)

![image-20220607011853317](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220607011853317.png)

```mysql
	create table tb_employee(
		id INT UNSIGNED COMMENT '编号',
		workno VARCHAR(10) COMMENT '员工工号',
		name VARCHAR(10) COMMENT '员工姓名',
		gender CHAR(1) COMMENT '员工性别',
		age  TINYINT UNSIGNED COMMENT '员工年龄',
		idcard CHAR(18) COMMENT '员工身份证',
		entrydate DATE COMMENT '入职时间'
	
	)COMMENT '员工表';
  DESC tb_employee
```



##### 表操作-修改

###### `在表中添加字段`

​	ALTER TABLE ==表名== ADD ==字段名== ==字段类型==      [COMMENT]   

```mysql
	ALTER TABLE tb_employee ADD nickname VARCHAR(20) COMMENT '昵称'
```

![image-20220607012334127](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220607012334127.png)

###### `修改数据类型`

```mysql
ALTER TABLE tb_employee MODIFY nickname  VARCHAR(30)  	
```

![image-20220607012935540](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220607012935540.png)

###### `修改字段名和字段类型`

```mysql
ALTER TABLE tb_employee CHANGE nickname username VARCHAR(30)  COMMENT '昵称' 
```

![image-20220607012951477](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220607012951477.png)

###### `删除字段`

```mysql
ALTER TABLE tb_employ DROP username;
```

![image-20220607013414117](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220607013414117.png)

###### `修改表名`

```mysql
ALTER TABLE tb_employee RENAME TO employee;
```

![image-20220607013701011](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220607013701011.png)

###### `删除表`

![image-20220607013748805](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220607013748805.png)

##### 总结

![image-20220607014956466](https://raw.githubusercontent.com/xiaomingAndroi/picture-bed/master/typoraTest/image-20220607014956466.png)

#### DML-数据操作

#### DQL-数据查询

#### DCL-数据控制

## 函数

## 约束

## 多表查询

## 事务

# 进阶

## 存储引擎

## Linux上安装

## 索引

## SQL优化

## 视图

## 存储过程

## 触发器

## 锁

## InnoDB

## MySQL管理

# 运维

## 日志

## 主从复制

## 分库分表

## 读写分离

