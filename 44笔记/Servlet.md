# 一、软件架构

## 1、C/S

### 1.1 意思

- Client/Server：客户端/服务器

### 1.2 例如

- QQ、微信、王者荣耀.......

### 1.3 特征

- 缺点

> 1. 必须在本地安装一个客户端软件
> 2. 如果版本升级了，那么本地客户端必须更新后才能享受新功能

- 优点

> 1. 画面非常酷炫
> 2. 而且游戏很少出现卡顿



## 2、B/S

### 1.1 意思

- Brower/Server：浏览器【客户端】/服务器

### 1.2 例如

- 百度、淘宝、新浪、CSDN、菜鸟教程、世纪佳缘，网页游戏.......

### 1.3 特征

- 缺点

> 1. 如果是网页游戏，会出现地图突然间没了，一会又出现这种情况

- 优点

> 1. 不用在本地安装独立的客户端，只需要安装一个浏览器即可
> 2. 应用更新了，本地无需做任何操作，照样直接访问服务器即可



## 3、Java一般市场就是专门开发B/S架构的系统

- PC端
- 手机端

==无论是开发PC端还是手机端应用，对于服务器来说，都没有任何区别==



# 二、服务器

## 1、概述

- 一个安装了特定软件(服务器软件)的电脑【这个电脑配置比较高，系统是Linux】



## 2、服务器软件

- tomcat
  - 版本：8.5.54
  - apache开源基金组织
  - 是一个中小型开源的服务器软件
  - 支持核心JavaEE开发规范(接口)【Servlet、JSP】



## 3、JavaWEB

- WEB：泛指网站，就是提供资源访问【资源：数据，是指网站所有的东西】
- WEB服务器：能够部署运行WEB应用的服务器软件 ---- tomcat
- JavaWEB：用Java开发WEB应用



# 三、Tomcat安装

## 1、安装及运行

> 1. 下载：https://tomcat.apache.org/download-80.cgi
> 2. 解压
>    - 解压到纯英文目录
> 3. 启动
>    - 双击 tomcat/bin/startup.bat
> 4. 测试
>    - 浏览器输入http://localhost:8080，回车看到一只猫就证明成功了
>      - http://localhost:8080 ：是一个URL地址【统一资源定位符】
>        - http：协议
>        - localhost：主机名或者ip地址【ip：127.0.0.1】
>        - 8080：端口号
>        - 没有输入资源地址，默认访问的是 index.jsp 这个资源

| http://localhost:8080                                        |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210616175121934.png" alt="image-20210616175121934" style="zoom:80%;" /> |



## 2、启动失败

- 启动时，窗口一闪而过

  - 原因是因为没有正确配置环境变量JAVA_HOME

  - 解决方案：正确配置环境变量JAVA_HOME

| 配置环境变量JAVA_HOME                                        |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210616175718870.png" alt="image-20210616175718870" style="zoom:80%;" /> |



## 3、停止tomcat

- 点击黑窗口叉【强制关闭，不推荐】
- 双击 tomcat/bin/shutdown.bat 【正常关闭，推荐】



## 4、Tomcat的目录结构

| Tomcat的目录结构                                             |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210617103926009.png" alt="image-20210617103926009" style="zoom:80%;" /> |



# 四、创建WEB项目

## 1、idea集成tomcat

| settings                                                     |
| ------------------------------------------------------------ |
| ![image-20210617110402785](pictures/image-20210617110402785.png) |
| <img src="pictures/image-20210617110444902.png" alt="image-20210617110444902" style="zoom:80%;" /> |



## 2、创建一个WEB项目

| 创建一个WEB项目                                              |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210617110752495.png" alt="image-20210617110752495" style="zoom:80%;" /> |



## 3、WEB项目的目录结构

| WEB项目的目录结构                                            |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210617111553649.png" alt="image-20210617111553649" style="zoom:80%;" /> |



## 4、如何启动一个WEB项目

- 部署

|                                                              |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210617112040173.png" alt="image-20210617112040173" style="zoom:80%;" /> |
| <img src="pictures/image-20210617112354051.png" alt="image-20210617112354051" style="zoom:80%;" /> |

- 如何访问

| 项目虚拟路径                                                 |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210617112630132.png" alt="image-20210617112630132" style="zoom:80%;" /> |

| tomcat配置页面                                               |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210617113208303.png" alt="image-20210617113208303" style="zoom:80%;" /> |
| <img src="pictures/image-20210617113542316.png" alt="image-20210617113542316" style="zoom:80%;" /> |

| tomcat真正访问的资源                                         |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210617113836779.png" alt="image-20210617113836779" style="zoom:80%;" /> |



# 五、Servlet

## 1、概述

- 就是一个服务器上运行小程序，本质上是JavaEE开发的一种规范【就是一个接口】
  - 凡是只有通过服务器上才能访问的资源被称为动态资源

## 2、服务器上资源

- 分类
  - 静态资源：就是不同的人访问，得到结果是相同的。
    - html、css、js
  - 动态资源：就是不同的人访问，得到结果有可能是不同的。
    - Servlet、JSP

## 3、快速入门

### 3.1 实现步骤

> 1. 创建一个web项目
> 2. 编写一个类，实现Servlet接口
> 3. 重写抽象方法，在Service方法中输出一句话
> 4. 在web.xml中配置和映射Servlet
> 5. 启动tomcat，在浏览器上输入url地址【通过 url-pattern 这个标签的配置】访问Servlet
>    - 在控制台看到输出的话就代表成功了

### 3.2 执行流程

| 执行流程                                                     |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210617115945695.png" alt="image-20210617115945695" style="zoom:80%;" /> |



## 4、Servlet生命周期

### 4.1 默认生命周期

> 1. tomcat启动时，会加载web.xml配置文件
> 2. 第一次访问Servlet时
>    - tomcat通过反射调用无参构造器创建Servlet实例
>    - tomcat调用init方法初始化Servlet信息
>    - tomcat调用service来处理请求
> 3. 第二次及以后每次访问都只会调用service方法
> 4. tomcat正常停止前一刻，调用destroy方法销毁Servlet实例

### 4.2 Servlet是线程安全的吗？

- Servlet是单例的，是线程非安全的

### 4.3 如何保证Servlet的线程安全？

- 上锁：效率太低
- ThreadLocal
- 不要在Servlet使用成员变量，即便使用成员变量，也不要对它进行修改【推荐】



## 5、能不能改变生命周期？

| load-on-startup ：可以指定Servlet的初始化时机                |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210617162316136.png" alt="image-20210617162316136" style="zoom:80%;" /> |



### 6、url-pattern这个标签有哪些配置方式

| 两种                                                         |
| ------------------------------------------------------------ |
| ![image-20210617163725967](pictures/image-20210617163725967.png) |



# 六、HTTP

## 1、概述

- 超文本传输协议（HTTP，HyperText Transfer Protocol)是互联网上应用最为广泛的一种网络协议，
- 是一个==基于请求与响应模式==的
- ==无状态==：每次发送请求到服务器，请求都是一个新的
- 应用层的协议，==运行于TCP协议基础之上。==



## 2、特点

- 基于请求与响应【适用于浏览器（客户端）与服务器】，且请求与响应是一对一的关系
- 无状态：每次发送请求到服务器，请求都是一个新的
- 版本1.1：持续连接机制
- HTTP允许传输任意类型的数据，传输的数据类型由Content-Type标识



## 3、HTTP通信

- 三次握手
  - ack机制：确保客户端与服务器是能够正常通信的
- 四次挥手
  - ack机制：确保服务器在断开客户端连接时，服务器端完成数据的传输，同意客户端断开连接请求

> 是基于ACK机制【确认机制】



## 4、请求报文和响应报文

- 请求报文
  - 请求行 请求方式/请求URL地址 HTTP/1.1
  - 请求头(Request Header)
  - 请求空行
  - 请求正文【只有POST请求方式才有】
- 响应报文
  - 状态行
  - 响应头(Response Header)
  - 响应空行
  - 响应正文



## 5、响应状态码

- 2开头的：响应成功【200】
- 3开头的
  - 缓存【304】
  - 重定向【302】
- 4开头的：客户端错误
  - 找不到资源【404】    
  - 请求方式不对【405】     
  - 请求参数错误【400】
  - 未认证【401】
  - 权限不足【403】
- 5开头的
  - 服务器错误【500，服务器出异常了（你代码写出错了）】
- 6开头的【没人用】

| 状态码大全                                                   |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210617174400501.png" alt="image-20210617174400501" style="zoom:80%;" /> |



# 七、Servlet高级

## 1、Servlet继承体系

- Servlet   -------   接口
  - GenericServlet   -------    抽象类
    - HttpServlet     ------    抽象类



## 2、Servlet三种创建方式

- 实现Servlet接口
- 继承GenericServlet，重写service方法
- 继承HttpServlet，重写 doGet方法 和 doPost方法

### 2.1 HTTP请求方式

- http请求有7种请求方式，目前浏览器只支持GET和POST，如果没有特殊指定，默认就是GET请求

### 2.2 Servlet接口的init方法

| web.xml                                                      |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210617180133482.png" alt="image-20210617180133482" style="zoom:80%;" /> |

| Demo01Servlet.java                                           |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210617180047197.png" alt="image-20210617180047197" style="zoom:80%;" /> |

### 2.3 GenericServlet

#### 2.3.1 作用

- init方法：对ServletConfig类型的变量config赋值
- service方法：等着我们去重写

#### 2.3.2 第二种创建Servlet的方式【了解】

| 继承GenericServlet                                           |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210618105425089.png" alt="image-20210618105425089" style="zoom:80%;" /> |



### 2.4 HttpServlet

#### 2.4.1 作用

- 重写service方法
  - 把请求对象和响应对象强转成子接口【HttpServletRequset、HttpServletResponse】
  - 调用自己的service方法
    - 通过不同的请求方式，调用不同doXxx方法

#### 2.4.2 第三种创建Servlet的方式【掌握】

- 继承HttpServlet，重写doGet和doPost方法【因为目前浏览器只支持get和post】

| 继承HttpServlet                                              |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210618110613710.png" alt="image-20210618110613710" style="zoom:80%;" /> |

#### 2.4.3 上述创建Servlet的方式，idea有自带菜单

| 使用idea自带菜单创建注解版Servlet                            |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210618110821845.png" alt="image-20210618110821845" style="zoom:80%;" /> |





## 3、创建纯注解版Servlet

### 3.1 制作注解版Servlet模版

| 注解版Servlet模版位置                                        |
| ------------------------------------------------------------ |
| ![image-20210618111535075](pictures/image-20210618111535075.png) |

- 把下面的代码复制到你的4位置上

```java
#if (${PACKAGE_NAME} && ${PACKAGE_NAME} != "")package ${PACKAGE_NAME};#end
#parse("File Header.java")
@javax.servlet.annotation.WebServlet("/${Entity_Name}")
public class ${Class_Name} extends javax.servlet.http.HttpServlet {
    
    @Override
    public void doPost(javax.servlet.http.HttpServletRequest request, javax.servlet.http.HttpServletResponse response) throws javax.servlet.ServletException, java.io.IOException {
		//写处理请求的代码
    }

    @Override
    public void doGet(javax.servlet.http.HttpServletRequest request, javax.servlet.http.HttpServletResponse response) throws javax.servlet.ServletException, java.io.IOException {
        this.doPost(request, response);
    }
}

```

| 模版生成的                                                   |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210618111821395.png" alt="image-20210618111821395" style="zoom:80%;" /> |

| @WebServlet                                                  |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210618112006838.png" alt="image-20210618112006838" style="zoom:80%;" /> |



# 八、Request

## 1、概述

- 请求【客户端向服务器获取某个资源时，这种动作被称为叫请求】
- Request对象封装了请求的所有信息

## 2、继承体系

- ServletRequest    -----  接口
  - HttpServletRequest   -----  子接口
    - org.apache.catalina.connector.RequestFacade   ----  服务器【tomcat】来创建HttpServletRequest实现类

## 3、API

```java
package com.qf.java2103.controller;

import javax.lang.model.SourceVersion;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.util.Enumeration;
import java.util.Map;

/**
 * @author ghy
 * @version 1.0
 */
@WebServlet("/demo05")
public class Demo05Servlet extends HttpServlet {

    @Override
    public void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {

        //处理post请求中文乱码
        request.setCharacterEncoding("UTF-8");

        //写处理请求的代码
        //System.out.println("Demo05Servlet doPost");
        //System.out.println(request);

        //1.获取项目虚拟路径
        String contextPath = request.getContextPath();   //   /:不会打出来
        System.out.println("contextPath = " + contextPath);

        //2.获取请求头
        String userAgentHeader = request.getHeader("User-Agent");
        System.out.println("userAgentHeader = " + userAgentHeader);

        //3.获取请求方式
        String method = request.getMethod();
        System.out.println("method = " + method);

        //4.获取请求参数对应的字符串
        String queryString = request.getQueryString();
        System.out.println("queryString = " + queryString);

        //了解命令
        String remoteUser = request.getRemoteUser();
        String remoteAddr = request.getRemoteAddr();
        String remoteHost = request.getRemoteHost();
        int remotePort = request.getRemotePort();
        System.out.println(remoteUser + " == " + remoteAddr + " == " + remoteHost +" == "+ remotePort);

        String servletPath = request.getServletPath();
        System.out.println("servletPath = " + servletPath);

        //5.获取请求路径
        String uri = request.getRequestURI();
        System.out.println("uri = " + uri);
        StringBuffer url = request.getRequestURL();
        System.out.println("url = " + url);

        //6.获取请求参数
        //根据请求参数名，获取值【浏览器为了保证传递到服务器的数据是完整的，传递的所有数据都是String】
        String age = request.getParameter("age");
        //获取请求参数是数组的形式对应的值
        String[] hobbies = request.getParameterValues("hobbies");
        //获取所有的请求参数，封装成一个map对象
        Map<String, String[]> parameterMap = request.getParameterMap();
        //获取所有的请求参数名
        Enumeration<String> parameterNames = request.getParameterNames();

    }

    @Override
    public void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doPost(request, response);
    }
}

```

- 重点

```java
//处理post请求中文乱码
request.setCharacterEncoding("UTF-8");

//6.获取请求参数,没有请求方式的限制
//根据请求参数名，获取值【浏览器为了保证传递到服务器的数据是完整的，传递的所有数据都是String】
String age = request.getParameter("age");
//获取请求参数是数组的形式对应的值
String[] hobbies = request.getParameterValues("hobbies");
//获取所有的请求参数，封装成一个map对象
Map<String, String[]> parameterMap = request.getParameterMap();
```



## 4、Get和Post请求的区别

### 4.1 Get

- 请求参数是在url后面，相对而言不安全
  - 请求参数的格式：url?key1=value1&key2=value2
    - 如 http://lcoalhost:8080/findByCondition?username=jack&gender=1&email=jack@163.com
- 请求数据大小有限制
- 效率高，没有请求体
- 浏览器默认请求方式就是Get

### 4.2 Post

- 请求参数在请求体，相对而言安全
- 请求数据没有大小限制
- 效率比Get稍低



# 九、Response

## 1、概述

- 响应
- 所有响应的数据都被封装到ServletResponse对象中

## 2、继承体系

- ServletResponse  ----  接口
  - HttpServletResponse    -----   子接口【一般就使用这个】
    - org.apache.catalina.connector.ResponseFacade   ----  tomcat实现HttpServletResponse的实现类

## 3、API

```java
package com.qf.java2103.controller;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.util.Enumeration;
import java.util.Map;

/**
 * @author ghy
 * @version 1.0
 */
@WebServlet("/demo06")
public class Demo06Servlet extends HttpServlet {

    @Override
    public void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        System.out.println("response = " + response);

        //1.设置响应头
        response.setHeader("MyHeader", "aa");

        //2.增加一个响应头
        response.addHeader("MyHeader", "bb");

        //3.设置状态码
        response.setStatus(666);

        //4.获取输出流
        //告知浏览器以text/html及UTF-8字符集这种解析响应的内容
        response.setContentType("text/html;charset=UTF-8");
        response.getWriter().write("hello, response!!<br/>");
        response.getWriter().write("你好，响应!!");
        response.getWriter().write("<hr/>");
        //把整数根据ascii码转成对应的字符
        response.getWriter().write(97);
        response.getWriter().write('a');
        response.getWriter().write("<hr/>");

        response.getWriter().println(97);
        response.getWriter().println('a');
        response.getOutputStream().write("你好，我是字节流".getBytes("UTF-8"));

    }

    @Override
    public void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        this.doPost(request, response);
    }
}

```

- 重点

```java
//告知浏览器以text/html及UTF-8字符集这种解析响应的内容
response.setContentType("text/html;charset=UTF-8");
response.getWriter().write("hello, response!!<br/>");
//字节流，是处理文件需要使用的
ServletOutputStream out = response.getOutputStream();
```



# 十、整个请求与响应的过程

| 整个请求与响应的过程                                         |
| ------------------------------------------------------------ |
| ![image-20210618165234534](pictures/image-20210618165234534.png) |



# 十一、登录

## 1、开发步骤

> 1. 创建数据库表
> 2. 创建项目`java2103-web-demo03-login`
> 3. 导入jar包【位置很重要】
>    - WEB-INF/lib/xxx.jar
> 4. 创建包
> 5. 准备工具类、配置文件等等
> 6. 写代码
> 7. 部署
> 8. 测试

## 2、具体实现

### 2.1 创建数据库表

1. 创建项目`java2103-web-demo03-login`
2. 导入jar包【位置很重要】
   - WEB-INF/lib/xxx.jar
3. 创建包
4. 写代码
5. 部署
6. 测试

















# 如何导入一个存在的web项目

- 选择 import Project，一路默认下一步
- 发现报错了，原因缺少tomcat

| 项目中增加tomcat                                             |
| ------------------------------------------------------------ |
| ![image-20210618104140583](pictures/image-20210618104140583.png) |
| <img src="pictures/image-20210618104220262.png" alt="image-20210618104220262" style="zoom:80%;" /> |
| <img src="pictures/image-20210618104238193.png" alt="image-20210618104238193" style="zoom:80%;" /> |

| 导出war包                                                    |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210618104440062.png" alt="image-20210618104440062" style="zoom:80%;" /> |
| <img src="pictures/image-20210618104536772.png" alt="image-20210618104536772" style="zoom:80%;" /> |
| <img src="pictures/image-20210618104552777.png" alt="image-20210618104552777" style="zoom:80%;" /> |

