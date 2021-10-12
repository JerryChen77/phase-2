# Day 49笔记

## 一、工厂创建对象

### 1.1 概述

* 对象的创建都是在其他类中
* 类的信息、类名关联紧密
* 可以使用工厂的方式来解决这个问题
  * 工厂类负责创建对象
  * 创建的对象在配置文件中指明，只需要向工厂类方法中传入对象名即可

### 1.2 BeanFactory

```
package com.qf.hotel.factory;

import java.io.*;
import java.util.Properties;

/**
 * 生成对象的工厂类
 *
 * foodTypeService=com.qf.hotel.service.impl.FoodTypeServiceImpl
 */
public class BeanFactory {
    private static final Properties PROPERTIES = new Properties();

    static {
        InputStream is = null;
        try {
            is = BeanFactory.class.getClassLoader().getResourceAsStream("bean.properties");
            PROPERTIES.load(is);
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            if (is != null){
                try {
                    is.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }

    /**
     * 通过对象名获取对象的方式
     * @param beanName
     * foodTypeService=com.qf.hotel.service.impl.FoodTypeServiceImpl
     * beanName===》foodTypeService
     * 通过beanName获取类名
     * 通过类名创建对象
     * @return
     * @throws ClassNotFoundException
     */
    public static Object getBean(String beanName){
        Object instance = null;
        try {
            // 1、获取类名
            String className = PROPERTIES.getProperty(beanName);
            Class<?> clazz = Class.forName(className);

            // 2、创建对象
            instance = clazz.newInstance();
        } catch (Exception e) {
            e.printStackTrace();
        }
        return instance;
    }
}
```

## 二、Servlet优化

### 2.1 概述

* 每一个功能都创建了一个对应的Servlet
  * foodtype
    * FoodTypeFindById
    * FoodTypeFindByCondition
    * FoodTypeUpdate
    * FoodTypeSave
    * FoodTypeDeleteById
* 能不能在一个Servlet中解决foodtype模块所有的问题呢？
  * 请求的时候加上一个参数标记，标明此请求需要完成的功能
  * 服务端根据标记来执行对应的方法

### 2.2 在doGet或者doPost中使用switch

```java
package com.qf.hotel.controller.foodtype;

import com.qf.hotel.factory.BeanFactory;
import com.qf.hotel.pojo.FoodType;
import com.qf.hotel.service.FoodTypeService;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.io.UnsupportedEncodingException;
import java.sql.SQLException;
import java.util.List;

@WebServlet("/foodtype01")
public class FoodTypeController01 extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        doGet(request,response);
    }

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        String method = request.getParameter("method");

        // 判断参数意图
        switch (method){
            case "findById":
                findById(request,response);
                break;

            case "update":
                update(request,response);
                break;

            case "search":
                search(request,response);
            default:
                response.sendRedirect(request.getContextPath() + "/index.jsp");
        }
    }

    public void findById(HttpServletRequest request, HttpServletResponse response) {
        System.out.println("调用findById方法...");
    }

    public void update(HttpServletRequest request, HttpServletResponse response) {
        System.out.println("调用update方法...");
    }

    public void search(HttpServletRequest request, HttpServletResponse response) throws UnsupportedEncodingException {
        System.out.println("调用search方法...");
        // 1、设置字符编码
        request.setCharacterEncoding("UTF-8");
        response.setContentType("text/html;charset=UTF-8");

        try {
            // 2、接收参数
            String keyword = request.getParameter("keyword");

            // 3、创建FoodType对象，设置typeName
            FoodType foodType = new FoodType();
            foodType.setTypeName(keyword);

            // 4、创建业务对象
            // FoodTypeService foodTypeService = new FoodTypeServiceImpl();
            FoodTypeService foodTypeService = (FoodTypeService) BeanFactory.getBean("foodTypeService");
            List<FoodType> foodTypes = foodTypeService.findByCondition(foodType);

            // 5、存储在域对象中
            request.setAttribute("foodTypes",foodTypes);

            // 6、转发到显示数据的页面
            request.getRequestDispatcher("/backend/detail/foodtype/foodtype-list.jsp").forward(request,response);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```



### 2.3 在service方法中使用switch

```
package com.qf.hotel.controller.foodtype;

import com.qf.hotel.factory.BeanFactory;
import com.qf.hotel.pojo.FoodType;
import com.qf.hotel.service.FoodTypeService;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.io.UnsupportedEncodingException;
import java.util.List;

@WebServlet("/foodtype02")
public class FoodTypeController02 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        // 1、设置字符编码
        request.setCharacterEncoding("UTF-8");
        response.setContentType("text/html;charset=UTF-8");

        String method = request.getParameter("method");

        // 判断参数意图
        switch (method){
            case "findById":
                findById(request,response);
                break;

            case "update":
                update(request,response);
                break;

            case "search":
                search(request,response);
            default:
                response.sendRedirect(request.getContextPath() + "/index.jsp");
        }
    }

    public void findById(HttpServletRequest request, HttpServletResponse response) {
        System.out.println("foodtype02调用findById方法...");
    }

    public void update(HttpServletRequest request, HttpServletResponse response) {
        System.out.println("foodtype02调用update方法...");
    }

    public void search(HttpServletRequest request, HttpServletResponse response) throws UnsupportedEncodingException {
        System.out.println("foodtype02调用search方法...");
        try {
            // 2、接收参数
            String keyword = request.getParameter("keyword");

            // 3、创建FoodType对象，设置typeName
            FoodType foodType = new FoodType();
            foodType.setTypeName(keyword);

            // 4、创建业务对象
            // FoodTypeService foodTypeService = new FoodTypeServiceImpl();
            FoodTypeService foodTypeService = (FoodTypeService) BeanFactory.getBean("foodTypeService");
            List<FoodType> foodTypes = foodTypeService.findByCondition(foodType);

            // 5、存储在域对象中
            request.setAttribute("foodTypes",foodTypes);

            // 6、转发到显示数据的页面
            request.getRequestDispatcher("/backend/detail/foodtype/foodtype-list.jsp").forward(request,response);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

### 2.4 创建BaseServlet01

* 在BaseServlet01的service方法中处理请求

```java
package com.qf.hotel.controller;

import com.qf.hotel.factory.BeanFactory;
import com.qf.hotel.pojo.FoodType;
import com.qf.hotel.service.FoodTypeService;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.io.UnsupportedEncodingException;
import java.util.List;

/**
 * 所有的控制器继承此Servlet
 * 能处理所有的请求
 */
@WebServlet()
public class BaseServlet01 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        // 1、设置字符编码
        request.setCharacterEncoding("UTF-8");
        response.setContentType("text/html;charset=UTF-8");

        String method = request.getParameter("method");

        // 判断参数意图
        switch (method){
            case "findById":
                findById(request,response);
                break;

            case "update":
                update(request,response);
                break;

            case "search":
                search(request,response);

            default:
                response.sendRedirect(request.getContextPath() + "/index.jsp");
        }
    }

    public void findById(HttpServletRequest request, HttpServletResponse response) {
        System.out.println("BaseServlet01调用findById方法...");
    }

    public void update(HttpServletRequest request, HttpServletResponse response) {
        System.out.println("BaseServlet01调用update方法...");
    }

    public void search(HttpServletRequest request, HttpServletResponse response) throws UnsupportedEncodingException {
        System.out.println("BaseServlet01调用search方法...");
        try {
            // 2、接收参数
            String keyword = request.getParameter("keyword");

            // 3、创建FoodType对象，设置typeName
            FoodType foodType = new FoodType();
            foodType.setTypeName(keyword);

            // 4、创建业务对象
            // FoodTypeService foodTypeService = new FoodTypeServiceImpl();
            FoodTypeService foodTypeService = (FoodTypeService) BeanFactory.getBean("foodTypeService");
            List<FoodType> foodTypes = foodTypeService.findByCondition(foodType);

            // 5、存储在域对象中
            request.setAttribute("foodTypes",foodTypes);

            // 6、转发到显示数据的页面
            request.getRequestDispatcher("/backend/detail/foodtype/foodtype-list.jsp").forward(request,response);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

### 2.5 创建BaseServlet02

* 使用反射的方式创建对象、方法，调用方法

```java
package com.qf.hotel.controller;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.lang.reflect.Method;

@WebServlet(name = "BaseServlet02")
public class BaseServlet02 extends HttpServlet {
    @Override
    protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        // 设置字符编码
        request.setCharacterEncoding("UTF-8");
        response.setContentType("text/html;charset=UTF-8");

        try {
            // 获取请求方法method携带的数据
            String methodName = request.getParameter("method");
            System.out.println("methodName==" + methodName);

            // 使用反射创建请求的Servlet的对象
            Class<? extends BaseServlet02> clazz = this.getClass();

            // 使用反射获取方法
            Method method = clazz.getMethod(methodName, HttpServletRequest.class, HttpServletResponse.class);

            // 调用方法
            Object obj = method.invoke(this, request, response);
            System.out.println("obj===" + obj);

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

* 继承了BaseServlet02 的控制器

```java
package com.qf.hotel.controller.foodtype;

import com.qf.hotel.controller.BaseServlet02;
import com.qf.hotel.factory.BeanFactory;
import com.qf.hotel.pojo.FoodType;
import com.qf.hotel.service.FoodTypeService;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.io.UnsupportedEncodingException;
import java.util.ArrayList;
import java.util.List;

@WebServlet("/foodtype04")
public class FoodTypeController04 extends BaseServlet02 {
    public void findById(HttpServletRequest request, HttpServletResponse response) {
        System.out.println("foodtype04调用findById方法...");
    }

    public void update(HttpServletRequest request, HttpServletResponse response) {
        System.out.println("foodtype04调用update方法...");
    }

    public void search(HttpServletRequest request, HttpServletResponse response) throws UnsupportedEncodingException {
        System.out.println("foodtype04调用search方法...");
        try {
            // 2、接收参数
            String keyword = request.getParameter("keyword");

            // 3、创建FoodType对象，设置typeName
            FoodType foodType = new FoodType();
            foodType.setTypeName(keyword);

            // 4、创建业务对象
            // FoodTypeService foodTypeService = new FoodTypeServiceImpl();
            FoodTypeService foodTypeService = (FoodTypeService) BeanFactory.getBean("foodTypeService");
            List<FoodType> foodTypes = foodTypeService.findByCondition(foodType);

            // 5、存储在域对象中
            request.setAttribute("foodTypes",foodTypes);

            // 6、转发到显示数据的页面
            request.getRequestDispatcher("/backend/detail/foodtype/foodtype-list.jsp").forward(request,response);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    public List<String> findByCondition(HttpServletRequest request, HttpServletResponse response) {
        ArrayList list = new ArrayList();
        list.add("张三");
        list.add("李四");
        list.add("王五");
        System.out.println("foodtype04调用findByCondition方法...");
        return list;
    }
}
```

### 2.6 终极版

```java
package com.qf.hotel.controller;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.lang.reflect.Method;

@WebServlet(name = "BaseServlet")
public class BaseServlet extends HttpServlet {
    @Override
    protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        try {
            // 获取请求方法method携带的数据，method表示请求执行的方法
            String methodName= request.getParameter("method");

            // 使用反射创建请求的Servlet的对象
            Class clazz = this.getClass();

            // 使用反射获取方法
            Method method = clazz.getMethod(methodName, HttpServletRequest.class, HttpServletResponse.class);

            //反射调用方法。谁处理业务方法，this表示请求执行的Servlet
            Object obj = method.invoke(this, request, response);

            // obj是我们自己设定的返回值，是一个字符串
            if(obj != null && obj instanceof String) {
                //给出响应
                /*
                 * 请求转发   forward:/url
                 * 重定向     redirect:
                 */
                String str = (String) obj;
                String url = str.substring(str.indexOf(":") + 1);
                if(str.startsWith("forward:")) {
                    request.getRequestDispatcher(url).forward(request, response);
                } else if(str.startsWith("redirect:")) {
                    response.sendRedirect(url);
                } else {
                    response.getWriter().write(str);
                }
                return;
            }
        } catch (Exception e) {
            e.printStackTrace();
        }
        response.getWriter().write("服务器正忙。。。");
    }
}
```

