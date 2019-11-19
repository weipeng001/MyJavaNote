## 1. IoC容器
本章介绍了Spring的Inversion of Control（IoC）容器。

#### 1.1。 Spring IoC容器和Bean简介
本章介绍了控制反转（IoC）原理的Spring框架实现。 IoC也称为依赖注入（DI）。 在此过程中，对象仅通过构造函数参数，工厂方法的参数或在构造或从工厂方法返回后在对象实例上设置的属性来定义其依赖项（即，与它们一起使用的其他对象） 。 然后，容器在创建bean时注入那些依赖项。 此过程从根本上讲是通过使用类的直接构造或诸如服务定位器模式之类的方法来控制其依赖项的实例化或位置的bean本身的逆过程（因此称为Control Inversion）。

org.springframework.beans和org.springframework.context包是Spring Framework的IoC容器的基础。 BeanFactory接口提供了一种高级配置机制，能够管理任何类型的对象。 ApplicationContext是BeanFactory的子接口。 它增加了：

* 与Spring的AOP功能轻松集成

* 消息资源处理（用于国际化）

* 活动发布

* 应用层特定的上下文，例如Web应用程序中使用的WebApplicationContext。

简而言之，BeanFactory提供了配置框架和基本功能，而ApplicationContext添加了更多企业特定的功能。 ApplicationContext是BeanFactory的完整超集，在本章中对Spring的IoC容器的描述专门使用。 有关使用BeanFactory代替ApplicationContext的更多信息，请参见BeanFactory。

在Spring中，构成应用程序主干并由Spring IoC容器管理的对象称为bean。 Bean是由Spring IoC容器实例化，组装和以其他方式管理的对象。 否则，bean仅仅是应用程序中许多对象之一。 Bean及其之间的依赖关系反映在容器使用的配置元数据中。

#### 1.2。 容器概述
org.springframework.context.ApplicationContext接口表示Spring IoC容器，并负责实例化，配置和组装Bean。 容器通过读取配置元数据来获取有关要实例化，配置和组装哪些对象的指令。 配置元数据以XML，Java批注或Java代码表示。 它使您能够表达组成应用程序的对象以及这些对象之间的丰富相互依赖关系。

Spring提供了ApplicationContext接口的几种实现。 在独立应用程序中，通常创建ClassPathXmlApplicationContext或FileSystemXmlApplicationContext的实例。 尽管XML是定义配置元数据的传统格式，但是您可以通过提供少量XML配置来声明性地启用对这些其他元数据格式的支持，从而指示容器将Java注释或代码用作元数据格式。

在大多数应用场景中，不需要显式用户代码即可实例化一个Spring IoC容器的一个或多个实例。 例如，在Web应用程序场景中，应用程序的web.xml文件中简单的八行（约）样板Web描述符XML通常就足够了（请参阅Web应用程序的便捷ApplicationContext实例化）。 如果使用Spring Tool Suite（基于Eclipse的开发环境），则只需单击几次鼠标或击键即可轻松创建此样板配置。

下图显示了Spring的工作原理的高级视图。 您的应用程序类与配置元数据结合在一起，以便在创建和初始化ApplicationContext之后，您将拥有一个完全配置且可执行的系统或应用程序。
![Alt text](/img/spring ioc.jpg)

#### 1.3。 Bean总览

#### 1.4。 依存关系

#### 1.5。 豆范围

#### 1.6。 自定义豆的性质

#### 1.7。 Bean定义继承

#### 1.8。 集装箱延伸点

#### 1.9。 基于注释的容器配置

#### 1.10。 类路径扫描和托管组件

#### 1.11。 使用JSR 330标准注释

#### 1.12。 基于Java的容器配置

#### 1.13。 环境抽象

#### 1.14。 注册一个LoadTimeWeaver

#### 1.15。 ApplicationContext的其他功能

#### 1.16。 豆工厂

## 2.资源

## 3.验证，数据绑定和类型转换

## 4.春季表达语言（SpEL）

## 5.使用Spring进行面向方面的编程

## 6. Spring AOP API

## 7.空安全

## 8.数据缓冲区和编解码器

## 9.附录