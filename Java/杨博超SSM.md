# MyBatis

## MyBatis简介

### MyBatis历史

### MyBatis特性

### MyBatis下载

## 搭建MyBatis

### 开发环境

IDE：idea 2019.2

构建工具：maven 3.5.4

MySQL版本：MySQL 8

MyBatis版本：MyBatis 3.5.7

MySQL不同版本的注意事项

> 1、驱动类driver-class-name
> MySQL 5版本使用jdbc5驱动，驱动类使用：com.mysql.jdbc.Driver
> MySQL 8版本使用jdbc8驱动，驱动类使用：com.mysql.cj.jdbc.Driver
> 2、连接地址url
> MySQL 5版本的url：
> jdbc:mysql://localhost:3306/ssm
> MySQL 8版本的url：
> jdbc:mysql://localhost:3306/ssm?serverTimezone=UTC
> 否则运行测试用例报告如下错误：
> java.sql.SQLException: The server time zone value 'ÖÐ¹ú±ê×¼Ê±¼ä' is unrecognized or
> represents more

### 创建maven工程

- 新建项目

![image-20220918181400315](D:\ALQF\Typora图片\image-20220918181400315.png)

![image-20220918181557726](D:\ALQF\Typora图片\image-20220918181557726.png)

![image-20220918181549589](D:\ALQF\Typora图片\image-20220918181549589.png)

- 选择maven构建工具

![image-20220918181743899](D:\ALQF\Typora图片\image-20220918181743899.png)

- 新建moulde

![image-20220918182042375](D:\ALQF\Typora图片\image-20220918182042375.png)	

# Spring

## Spring简介

官网地址：https://spring.io/

> Spring 是最受欢迎的企业级 Java 应用程序开发框架，数以百万的来自世界各地的开发人员使 用
> Spring 框架来创建性能好、易于测试、可重用的代码。
> Spring 框架是一个开源的 Java 平台，它最初是由 Rod Johnson 编写的，并且于 2003 年 6 月首
> 次在 Apache 2.0 许可下发布。
> Spring 是轻量级的框架，其基础版本只有 2 MB 左右的大小。
> Spring 框架的核心特性是可以用于开发任何 Java 应用程序，但是在 Java EE 平台上构建 web 应
> 用程序是需要扩展的。 Spring 框架的目标是使 J2EE 开发变得更容易使用，通过启用基于 POJO
> 编程模型来促进良好的编程实践。

## Spring家族

项目列表：https://spring.io/projects

## Spring Framework

Spring 基础框架，可以视为 Spring 基础设施，基本上任何其他 Spring 项目都是以 Spring Framework
为基础的。

### 特性

- 非侵入式：使用 Spring Framework 开发应用程序时，Spring 对应用程序本身的结构影响非常
  小。对领域模型可以做到零污染；对功能性组件也只需要使用几个简单的注解进行标记，完全不会
  破坏原有结构，反而能将组件结构进一步简化。这就使得基于 Spring Framework 开发应用程序
  时结构清晰、简洁优雅。

- 控制反转：IOC——Inversion of Control，翻转资源获取方向。把自己创建资源、向环境索取资源
  变成环境将资源准备好，我们享受资源注入。
- 面向切面编程：AOP——Aspect Oriented Programming，在不修改源代码的基础上增强代码功
  能。
  容器：Spring IOC 是一个容器，因为它包含并且管理组件对象的生命周期。组件享受到了容器化
  的管理，替程序员屏蔽了组件创建过程中的大量细节，极大的降低了使用门槛，大幅度提高了开发
  效率。
- 组件化：Spring 实现了使用简单的组件配置组合成一个复杂的应用。在 Spring 中可以使用 XML
  和 Java 注解组合这些对象。这使得我们可以基于一个个功能明确、边界清晰的组件有条不紊的搭
  建超大型复杂应用系统。
- 声明式：很多以前需要编写代码才能实现的功能，现在只需要声明需求即可由框架代为实现。
  一站式：在 IOC 和 AOP 的基础上可以整合各种企业应用的开源框架和优秀的第三方类库。而且
  Spring 旗下的项目已经覆盖了广泛领域，很多方面的功能性需求可以在 Spring Framework 的基
  础上全部使用 Spring 来实现。

### 五大功能模块

![image-20220918175534363](D:\ALQF\Typora图片\image-20220918175534363.png)

## IOC

### IOC容器

#### IOC思想

IOC：Inversion of Control，翻译过来是反转控制。

Spring创建的对象默认就是单例的，我们如果想要多例的只需要一个属性来配置。

**①获取资源的传统方式**

我们使用对象，需要我们自己创建对象

自己做饭：买菜、洗菜、择菜、改刀、炒菜，全过程参与，费时费力，必须清楚了解资源创建整个过程
中的全部细节且熟练掌握。
在应用程序中的组件需要获取资源时，传统的方式是组件主动的从容器中获取所需要的资源，在这样的
模式下开发人员往往需要知道在具体容器中特定资源的获取方式，增加了学习成本，同时降低了开发效
率。
**②反转控制方式获取资源**

Spring来为我们提供对象，Spring提供的是什么，我们就使用什么。

点外卖：下单、等、吃，省时省力，不必关心资源创建过程的所有细节。
反转控制的思想完全颠覆了应用程序组件获取资源的传统方式：反转了资源的获取方向——改由容器主
动的将资源推送给需要的组件，开发人员不需要知道容器是如何创建资源对象的，只需要提供接收资源
的方式即可，极大的降低了学习成本，提高了开发的效率。这种行为也称为查找的被动形式。
**③DI**

IOC是一种思想，DI是IOC的一种实现方式。

DI：Dependency Injection，翻译过来是**依赖注入**。(为我们当前使用的Spring管理对象的属性赋值)
DI 是 IOC 的另一种表述方式：即组件以一些预先定义好的方式（例如：setter 方法）接受来自于容器
的资源注入。相对于IOC而言，这种表述更直接。
所以结论是：IOC 就是一种反转控制的思想， 而 DI 是对 IOC 的一种具体实现。

#### IOC容器在Spring中的实现

Spring 的 IOC 容器就是 IOC 思想的一个落地的产品实现。IOC 容器中管理的组件也叫做 bean。在创建
bean 之前，首先需要创建 IOC 容器。Spring 提供了 IOC 容器的两种实现方式：

##### ①BeanFactory

这是 IOC 容器的基本实现，是 Spring 内部使用的接口。面向 Spring 本身，不提供给开发人员使用。

##### ②ApplicationContext

BeanFactory 的子接口，提供了更多高级特性。面向 Spring 的使用者，几乎所有场合都使用
ApplicationContext 而不是底层的 BeanFactory。

##### ③ApplicationContext的主要实现类

![image-20220918182258002](D:\ALQF\Typora图片\image-20220918182258002.png)

![image-20220918182306672](D:\ALQF\Typora图片\image-20220918182306672.png)

## 基于XML管理bean

### 实验一：入门案例

#### ①创建Maven Module

#### ②引入依赖

```xml
   <dependencies>
    <!-- 基于Maven依赖传递性，导入spring-context依赖即可导入当前所需所有jar包 -->
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-context</artifactId>
        <version>5.3.1</version>
    </dependency>
    <!-- junit测试 -->
    <dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
        <version>4.12</version>
        <scope>test</scope>
    </dependency>
    </dependencies>
```

基于Maven依赖传递性，导入spring-context依赖即可导入当前所需所有jar包 是什么意思呢？

导入spring-context其实导入了这么多包

![image-20220918183525435](D:\ALQF\Typora图片\image-20220918183525435.png)

#### ③查看BeanFactory子接口

ctrl+H可以查看继承和实现关系。

![image-20220918182712110](D:\ALQF\Typora图片\image-20220918182712110.png)

![image-20220918183108032](D:\ALQF\Typora图片\image-20220918183108032.png)

ClassPathXmlApplicationContext用的比较多，因为我们的配置文件都是在项目路径下

![image-20220918183117157](D:\ALQF\Typora图片\image-20220918183117157.png)

![image-20220918183744706](D:\ALQF\Typora图片\image-20220918183744706.png)