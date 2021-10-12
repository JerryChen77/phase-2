# Day 45笔记

## 一、转发和重定向

### 1.1 概述

* 一个文件不可能处理所有的业务
* 需要多个Servlet或者view共同完成操作
* 多个文件之间的跳转、数据传递
* 转发和重定向可以完成这些操作

### 1.2 转发

* 转发是服务端行为，只在服务器内部实现

* 数据通过request对象保存，一次请求的数据可以在多次转发之间使用

* request调用的方法

  * ```
    request.getRequestDispatcher("相对地址").forward(request,response);
    ```

* 转发浏览器地址不变
* 存数据：request.setAttribute(key,value); 
  
  - 以键值对形式存储在request作用域中。key为String类型，value为Object类型
* 取数据：request.getAttribute(key);
  
  - 通过String类型的key访问Object类型的value

### 1.3 转发实现

* BuyLightServlet

```java
package com.qf.servlets;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

@WebServlet("/BuyLightServlet")
public class BuyLightServlet extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        doGet(request,response);
    }

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        request.setCharacterEncoding("UTF-8");
        response.setContentType("text/html;charset=utf-8");

        String light = request.getParameter("light");
        // 设置属性
        request.setAttribute("username","李四五金店");
        // request.removeAttribute("username");
        // 移出属性
        System.out.println("李四接收到买灯的请求,买:" + light);
        System.out.println("李四家没有这个灯...，李四带着参数去王五家买灯...");

        // 转发请求到另一个servlet
        request.getRequestDispatcher("LightFactoryServlet").forward(request,response);

    }
}
```

* LightFactoryServlet

```java
package com.qf.servlets;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

@WebServlet("/LightFactoryServlet")
public class LightFactoryServlet extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        doGet(request,response);
    }

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        request.setCharacterEncoding("UTF-8");
        response.setContentType("text/html;charset=utf-8");

        String light = request.getParameter("light");

        System.out.println("王五灯工厂收到" + request.getAttribute("username") + "转发来买灯的请求...买：" + light);

        response.getWriter().write("由王五家生产的灯即将送上...");
    }
}
```

* 前端

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>买灯</title>
	</head>
	<body>
		
		<form action="BuyLightServlet" method="get">
			<input type="text" name="light" id="light" value="" placeholder="张三买的灯"/>
			<input type="submit" value="买灯"/>
		</form>
	</body>
	
</html>
```

### 1.4 重定向

* 服务端接收到请求之后，响应给客户端一个新的地址，客户端再次向新地址发送请求
* 重定向是客户端行为
* 重定向过程中第一次发送的数据，在第二次请求中会消失
* 重定向能跳转到本项目和其他项目资源

### 1.5 重定向实现

* 前端

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>买灯</title>
	</head>
	<body>
		
		<form action="BuyLightServlet2" method="get">
			<input type="text" name="light" id="light" value="" placeholder="张三买的灯"/>
			<input type="submit" value="买灯"/>
		</form>
	</body>
	
</html>
```



* BuyLightServlet2

```java
package com.qf.servlets;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.net.URLEncoder;

@WebServlet("/BuyLightServlet2")
public class BuyLightServlet2 extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        doGet(request,response);
    }

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        request.setCharacterEncoding("UTF-8");
        response.setContentType("text/html;charset=UTF-8");

        String light = request.getParameter("light");
        System.out.println("light===" + light);
        /*// 设置属性
        request.setAttribute("username","李四五金店");
        // request.removeAttribute("username");
        // 移出属性
        System.out.println("李四接收到买灯的请求,买:" + light);
        System.out.println("李四家没有这个灯...，李四带着参数去王五家买灯...");*/

        // 重定向请求到另一个servlet
        // response.sendRedirect("/Day45_war_exploded/LightFactoryServlet2?light=" + URLEncoder.encode(light,"UTF-8"));
        response.sendRedirect(request.getContextPath() + "/LightFactoryServlet2?light=" + URLEncoder.encode(light,"UTF-8"));
        // response.sendRedirect("https://www.baidu.com/");

    }
}
```

* LightFactoryServlet2

```java
package com.qf.servlets;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.net.URLDecoder;

@WebServlet("/LightFactoryServlet2")
public class LightFactoryServlet2 extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        doGet(request,response);
    }

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        request.setCharacterEncoding("UTF-8");
        response.setContentType("text/html;charset=UTF-8");

        String light = request.getParameter("light");
        light = URLDecoder.decode(light,"UTF-8");

        /*System.out.println("王五灯工厂收到" + request.getAttribute("username") + "转发来买灯的请求...买：" + light);*/

        System.out.println("王五灯工厂收到转发来买灯的请求...买：" + light);
        response.getWriter().write("由王五家生产的灯即将送上...");
    }
}
```

### 1.6 重定向细节处理

* 数据传递

  * 重定向过程中request中的数据不会共享

  * 如果想在重定向过程中携带参数可以采用拼接参数的方式发送数据

    * ```
      /Day45_war_exploded/LightFactoryServlet2?light=" + light
      ```

* 路径书写问题
  * 转发直接书写相对路径
  * /重定向需要项目名称/目标文件
  * request.getContextPath()===项目名字

## 二、乱码处理

### 2.1 乱码产生原因

* 客户端 || 服务端 || 数据库其中的一项或者多项与其他字符编码不一致
* 编码和解码方式不同会导致中文乱码

### 2.2 设置编码集解决乱码

* 前端和服务端和数据库编码集设置一致
* 不一定能绝对解决问题

### 2.3 字符串拆散重组

* str.getBytes("字符集")
* String str = new String(bytes,"字符集")

### 2.4 使用IO解决乱码

* 桥转换流

### 2.5 使用URLEncode和URLDecode方法解决

```
URLEncoder.encode(light,"UTF-8")
URLDecoder.decode(light,"UTF-8");
```

### 2.6 使用字节方式传输

## 三、Cookie

### 3.1 概述

* 客户端保存数据的一种方式
* 客户端发送请求之后，服务端将数据放入cookie返回给客户端
* 由服务器创建，保存在客户端
* 客户端得到cookie之后每次访问会携带cookie

### 3.2 创建对象

```
Cookie cookie = new Cookie("key","value");
```

### 3.3 响应cookie给客户端

```
response.addCookie(cookie);
```

### 3.4 修改Cookie

* 创建同名的覆盖

### 3.5 删除Cookie

* 默认生命周期中关闭浏览器自动删除
* 手动在浏览器中删除

### 3.6 优点和缺点

* 优点

```
- 可配置到期规则。
- 简单性：Cookie 是一种基于文本的轻量结构，包含简单的键值对。
- 数据持久性：Cookie默认在过期之前是可以一直存在客户端浏览器上的。
```

* 缺点

```
- 大小受到限制：大多数浏览器对 Cookie 的大小有 4K、8K字节的限制。
- 用户配置为禁用：有些用户禁用了浏览器或客户端设备接收 Cookie 的能力，因此限制了这一功能。、
- 潜在的安全风险：Cookie 可能会被篡改。会对安全性造成潜在风险或者导致依赖于Cookie 的应用程序失败。
```

## 四、Session

### 4.1 概述

* 服务端存储数据、状态的对象
* 有效期是一次会话
  * 多次请求可以是同一次会话
  * 一旦浏览器关闭，则结束会话

* 服务器会为每一次会话分配一个Session对象
  * Session是服务器创建，保存在服务器
* 首次使用到Session时，服务器会自动创建Session，并创建Cookie存储SessionId发送回客户端
  * 可以使用request获取
* 可以将数据存入Session中，在一次会话的任意位置进行获取
* 可传递任何数据(基本数据类型、对象、集合、数组)

### 4.2 获取Session对象

```java
package com.qf.servlets.ssion;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import javax.servlet.http.HttpSession;
import java.io.IOException;

@WebServlet("/SS01")
public class SS01 extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        doGet(request,response);
    }

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        // 设置编码集
        request.setCharacterEncoding("UTF-8");
        response.setContentType("text/html;charset=UTF-8");

        // 获取session
        HttpSession session01 = request.getSession();
        System.out.println(session01.getId());

        response.sendRedirect(request.getContextPath() + "/SS02");

    }
}
```

### 4.3 删除session属性

```
// 更多时候存储的User对象
session01.removeAttribute("loginUser");
```

### 4.4 修改session属性

```
// 更多时候存储的User对象
session01.setAttribute("loginUser",true);
```

### 4.5 添加session属性

```
// 更多时候存储的User对象
session01.setAttribute("loginUser",true);
```

### 4.6 验证码案例

* 后端使用Validate生成验证码、存在Session中
* 前端登录页获取验证码
* 前端发送验证码到服务端，和Session中的验证码比较是否正确

## 五、ServletContext

### 5.1 概述

* 全局的对象，能存储数据
* 生命周期贼长--和服务器一样

### 5.2 获取ServletContext

```
- GenericServlet提供了getServletContext()方法。（推荐） this.getServletContext();
- HttpServletRequest提供了getServletContext()方法。(推荐)
- HttpSession提供了getServletContext()方法。
```

### 5.3 添加属性

```
// 设置全局的参数
context01.setAttribute("flag","全局的标记");
```

### 5.4 修改属性

```
// 设置全局的参数
context01.setAttribute("flag","全局的标记");
```

### 5.5 获取属性

```
// 获取ServletContext
ServletContext context02 = request.getServletContext();
```

### 5.6 移除属性

```
context04.removeAttribute("flag");
```

### 5.7 其他API

```java
package com.qf.servlets.context;

import javax.servlet.ServletContext;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

@WebServlet("/SC04")
public class ServletSC04 extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        doGet(request,response);
    }

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        // 设置编码集
        request.setCharacterEncoding("UTF-8");
        response.setContentType("text/html;charset=UTF-8");

        // 获取ServletContext
        ServletContext context04 = request.getSession().getServletContext();

        String contextPath = context04.getContextPath();
        System.out.println("contextPath:" + contextPath);

        String realPath = context04.getRealPath("/");
        System.out.println("realPath:" + realPath);

        context04.removeAttribute("flag");

        System.out.println("在SC04中获取flag:" + context04.getAttribute("flag"));

    }
}
```

### 5.8 统计访问次数

```java
package com.qf.servlets.context;

import javax.servlet.ServletContext;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.io.PrintWriter;

@WebServlet("/SC05")
public class SC05 extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        doGet(request,response);
    }

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        // 设置编码集
        request.setCharacterEncoding("UTF-8");
        response.setContentType("text/html;charset=UTF-8");

        ServletContext application = request.getServletContext();
        Integer count = (Integer) application.getAttribute("count");
        if(count==null) {
            count=1;
            application.setAttribute("count", count);
        }else {
            count++;
            application.setAttribute("count", count);
        }

        PrintWriter out=response.getWriter();
        out.write("servlet共访问次数："+count);

    }
}
```

## 六、存储数据的对象对比

* request
* cookie
* session
* ServletContext

```
比较
	创建方式
	存取值方式
	作用域
	生命周期
```

