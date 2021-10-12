# 一、设计模式概述

> 很多程序员死在前面，通过经验总结出来一套非常优秀的模板代码。而这套模板可以帮我们在设计底层框架原理实现时，能够帮我们提高框架的各种优点，可扩展、可重用、可移性等等。。。。



## 1、设计模式遵循原则

- https://www.cnblogs.com/shijingjing07/p/6227728.html

> - 单一职责原则
> - 里氏替换原则
> - 依赖倒置原则
> - 接口隔离原则
> - 迪米特法则
> - 开闭原则

```
设计模式的六大原则
1、开闭原则（Open Close Principle）
开闭原则的意思是：对扩展开放，对修改关闭。在程序需要进行拓展的时候，不能去修改原有的代码，实现一个热插拔的效果。简言之，是为了使程序的扩展性好，易于维护和升级。想要达到这样的效果，我们需要使用接口和抽象类，后面的具体设计中我们会提到这点。

2、里氏代换原则（Liskov Substitution Principle）
里氏代换原则是面向对象设计的基本原则之一。 里氏代换原则中说，任何基类可以出现的地方，子类一定可以出现。LSP 是继承复用的基石，只有当派生类可以替换掉基类，且软件单位的功能不受到影响时，基类才能真正被复用，而派生类也能够在基类的基础上增加新的行为。里氏代换原则是对开闭原则的补充。实现开闭原则的关键步骤就是抽象化，而基类与子类的继承关系就是抽象化的具体实现，所以里氏代换原则是对实现抽象化的具体步骤的规范。

3、依赖倒转原则（Dependence Inversion Principle）
这个原则是开闭原则的基础，具体内容：针对接口编程，依赖于抽象而不依赖于具体。

4、接口隔离原则（Interface Segregation Principle）
这个原则的意思是：使用多个隔离的接口，比使用单个接口要好。它还有另外一个意思是：降低类之间的耦合度。由此可见，其实设计模式就是从大型软件架构出发、便于升级和维护的软件设计思想，它强调降低依赖，降低耦合。

5、迪米特法则，又称最少知道原则（Demeter Principle）
最少知道原则是指：一个实体应当尽量少地与其他实体之间发生相互作用，使得系统功能模块相对独立。

6、合成复用原则（Composite Reuse Principle）
合成复用原则是指：尽量使用合成/聚合的方式，而不是使用继承。
```



# 二、工厂模式

- 工厂模式提供了一个工厂来创建对象，对外隐藏了对象创建的细节。外部在获取对象时，只需要调用工厂的方法即可。无需关心对象是如何创建的。
-  使用工厂模式创建对象时，最好提供对应的标识，告知工厂通过该标识来创建对应的对象实例。



- bean.properties

```properties
product=com.qf.java2103.pojo.Product
user=com.qf.java2103.pojo.User
userDao=com.qf.java2103.dao.impl.UserDaoPlusImpl
```

- 工厂对象

```java
package com.qf.java2103.factory;

import com.qf.java2103.pojo.User;

import java.io.IOException;
import java.util.Properties;

/**
 * @author ghy
 * @version 1.0
 */
public class BeanFactory {

    private static final Properties PROPERTIES = new Properties();

    static {
        try {
            PROPERTIES.load(BeanFactory.class.getClassLoader().getResourceAsStream("bean.properties"));
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    /**
     *
     * @param beanName user product
     * @return
     */
    public static Object getBeanPlus(String beanName){
        String className = PROPERTIES.getProperty(beanName);
        try {
            Class<?> clazz = Class.forName(className);
            if(null != clazz) {
                return clazz.newInstance();
            }
        } catch (Exception e) {
            //e.printStackTrace();
        }
        return null;
    }

}
```



# 三、单例模式

- 整个应用中有且只有一个实例，这种实例被称为叫单例。
  - 可以节省应用的内存，提高性能。

## 1、分类

- 懒汉模式
  - 非线程安全的
- 饿汉模式
  - 线程安全的
- 线程安全的懒汉模式【双重校验锁】



## 2、实现步骤

> 1. 创建一个类
> 2. 构造器私有
> 3. 提供一个私有静态属性，类型就是当前类
> 4. 提供一个公开的静态方法，用于返回当前类实例



### 2.1 懒汉模式

```java
package com.qf.java2103.singleton;

/**
 * 懒汉式
 *  懒 ：Lazy，延迟：需要时再去获取实例，不需要的时候不创建实例
 * @author ghy
 * @version 1.0
 */
public class Singleton1 {

    private Singleton1(){}

    private static Singleton1 singleton = null;

    public static Singleton1 getInstance(){
        if(null == singleton) {
            singleton = new Singleton1();
        }
        return singleton;
    }

}

```



### 2.2 饿汉模式

```java
package com.qf.java2103.singleton;

/**
 * 饿汉式
 * @author ghy
 * @version 1.0
 */
public class Singleton2 {

    private Singleton2(){}

    //如果我现在不用该实例，那么在内存也会存在，浪费空间
    private static Singleton2 singleton = new Singleton2();

    public static Singleton2 getInstance(){
        return singleton;
    }

}

```





### 2.3 双重校验锁

```java
package com.qf.java2103.singleton;

/**
 * 双重校验锁（属于饿汉模式）
 *  既能解决性能问题，也是线程安全的
 * @author ghy
 * @version 1.0
 */
public class Singleton3 {

    private Singleton3(){}

    private static Singleton3 singleton = null;

    public static Singleton3 getInstance(){
        if(null == singleton) {
            synchronized (Singleton3.class) {
                if(null == singleton) {
                    singleton = new Singleton3();
                }
            }
        }
        return singleton;
    }

}
```



# 四、XML

- 可扩展性标记语言

## 1、特征

> 1. 语法非常严格



## 2、定位

- 充当配置文件存在
- 语法跟HTML很相似



## 3、语法

> 1. 必须有一个头声明，且写在xml文件的第一行
> 2. 有且只有一根标签
> 3. 标签不能相互嵌套【你中有我，我中有你】
> 4. 标签有开始必须有结束



## 4、自定义xml

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!-- 这是一个头部声明 -->
<!-- 有且只有一个根标签 -->
<!-- 
	一个DOM结构由三部分：标签，属性，文本
 -->
<users>
	<user id="10">
		<username>
			<value>张三</value>
		</username>
		<gender value="1"></gender>
		<address>hz</address>
	</user>
	<user>
		<username>
			<value>李四</value>
		</username>
		<gender value="0"/>
	</user>
	<address>hz</address>
</users>
```



## 5、约束

### 5.1 作用

- 约定并限制xml中能够写什么？

### 5.2 分类

- DTD约束：相对而言，具有一定约束作用，但是不是很严谨
  - Mybatis就是使用DTD约束
- Schame约束：就是非常严谨
  - Spring、SpringMVC、web.xml

> CDATA区：如果当前xml中有些内容出现了一特殊字符，无法进行正常显示，那么我们使用CDATA区进行包裹，就会还原成特殊字符的原始意义



## 6、解析

### 6.1 为什么要解析？

- 解析xml的目的是为了获取xml中的内容

### 6.2 谁来解析

- 谁编写的xml，谁来解析
  - 后期我们在使用框架就会有很多的xml文件，那么解析工作就由框架来完成
  - 框架底层使用的是dom4j解析

#### 6.3 解析技术

- DOM解析【很麻烦，很low】
- dom4j【在dom的基础进行封装，核心对象document】
- jsoup【支持选择器、支持XPath、支持正则解析】





