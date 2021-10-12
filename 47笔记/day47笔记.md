# Day47笔记

## 一、EL表达式

### 1.1 概述

* Expression Language
* 相当于是jsp输出标签的简写形式
* 用来获取jsp域中存储的数据

### 1.2 获取方式

* 获取指定域中的数据

  * ${scope.name}
  * 如果没有获取到数据，返回""

* 获取不指定域中的数据

  * ${name}
  * 从小范围到大范围查找

  ```jsp
  <%--
    Created by IntelliJ IDEA.
    User: Dushine2008
    Date: 2021/6/22
    Time: 9:32
    To change this template use File | Settings | File Templates.
  --%>
  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
  <html>
      <head>
          <title>获取存储在域中的数据</title>
      </head>
      <body>
          <%--
              pageContext有效范围：当前页面
              request有效范围：一次请求
              session有效范围：一次会话
              application有效范围：服务器生命周期
          --%>
          <%
              request.setAttribute("flag","request设置的标记");
              session.setAttribute("flag","session设置的标记");
              application.setAttribute("flag","application设置的标记");
          %>
  
          <%=
             "pageContext===" + pageContext.findAttribute("flag")
          %>
          <br>
  
          <%=
              "request===" + request.getAttribute("flag")
          %>
          <br>
  
          <%=
              "session===" + session.getAttribute("flag")
          %>
          <br>
  
          <%=
              "application===" + application.getAttribute("flag")
          %>
          <br>
          <hr>
          <%--    可以获取指定域中的数据    --%>
          ${pageScope.flag}
          ${requestScope.flag}
          ${sessionScope.flag}
          ${applicationScope.flag}
  
          <hr>
  
          <%--    获取域中的数据，范围从小到大,pageContext > request > session > application    --%>
          ${flag}
          ${flag}
          ${flag}
          ${flag}
  
      </body>
  </html>
  ```

  

### 1.3 获取各种数据中的数据

```jsp
<%@ page import="com.qf.entity.User" %>
<%@ page import="java.util.Map" %>
<%@ page import="java.util.HashMap" %>
<%@ page import="java.util.List" %>
<%@ page import="java.util.ArrayList" %><%--
  Created by IntelliJ IDEA.
  User: Dushine2008
  Date: 2021/6/22
  Time: 9:50
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
    <head>
        <title>读取对象数据</title>
    </head>
    <body>
        <%

            User user = new User();
            user.setUsername("lisi");
            user.setPassword("sili");

            request.setAttribute("user",user);
        %>

        ${user}
        <br>
        ${user.username}

        <hr>

        <%
            int[] array = new int[]{111,2222,333,4,5};
            request.setAttribute("array",array);

            List<User> users = new ArrayList<>();
            users.add(new User("songjiang","jiangsong"));
            users.add(new User("wuyong","yongwu"));
            users.add(new User("likui","kuili"));
            users.add(new User("wusong","songwu"));
            request.setAttribute("users",users);

            Map<String,String> maps = new HashMap<>();
            maps.put("CN","中国");
            maps.put("FK","法国");
            maps.put("US","美国");
            request.setAttribute("maps",maps);
        %>

        array===${array}
        <br>
        users===${users}
        <br>
        maps===${maps}
        <br>

        ${array[0]}
        <br>
        ${array[1]}
        <br>
        ${array[2]}
        <br>

        <hr>

        ${users[0]}
        <br>
        ${users[1]}
        <br>
        ${users[2]}
        <br>

        <hr>

        ${users.get(0)}
        <br>
        ${users.get(1)}
        <br>
        ${users.get(2)}
        <br>
        <hr>

        ${maps.get("CN")}
        <br>
        ${maps.get("FK")}
        <br>
        ${maps.get("US")}
        <br>
        <hr>

        ${maps.CN}
        <br>
        ${maps.FK}
        <br>
        ${maps.US}
        <br>

    </body>
</html>
```

### 1.4 EL运算符

```jsp
<%--
  Created by IntelliJ IDEA.
  User: Dushine2008
  Date: 2021/6/22
  Time: 10:07
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
    <head>
        <title>EL运算符</title>
    </head>
    <body>
        <%
            request.setAttribute("num",1234);
            String ss = "123";
            request.setAttribute("ss",ss);
        %>
        <h1>算术运算</h1>
        num + 1==${num + 1}<br/>
        num - 1==${num - 1}<br/>
        num * 2==${num * 2}<br/>
        num div 2==${num div 2}<br/>
        num mod 2==${num mod 2}<br/>

        <hr/>

        <h1>关系运算</h1>
        ${num == 1234}<br/>
        ${num != 1234}<br/>
        ${num > 1200}<br/>
        ${num < 1200}<br/>
        ${num >= 1234}<br/>
        ${num <= 1234}<br/>

        <hr/>

        <h1>关系运算</h1>
        ${num eq 1234}<br/>
        ${num ne 1234}<br/>
        ${num gt 1200}<br/>
        ${num lt 1200}<br/>
        ${num ge 1234}<br/>
        ${num le 1234}<br/>
        <hr/>

        <h1>逻辑运算</h1>
        ${num %2==0 || num /2 ==1}<br/>
        ${num % 2==0 && num % 4==0}<br/>
        ${!(num > 1234)}<br/>

        <hr/>

        <h1>empty运算符</h1>
        ${ss == null}<br/>
        ${empty ss}<br/>
    </body>
</html>
```

### 1.5 获取上下文和cookie

```jsp
<%--
  Created by IntelliJ IDEA.
  User: Dushine2008
  Date: 2021/6/22
  Time: 10:15
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
    <head>
        <title>EL内置对象</title>
    </head>
    <body>
        ${pageContext.request.contextPath}
        <a href="demo03.jsp">点我01</a>
        <a href="/Day47_war_exploded/demo03.jsp">点我02</a>
        <a href="<%=request.getContextPath()%>/demo03.jsp">点我03</a>
        <a href="${pageContext.request.contextPath}/demo03.jsp">点我04</a>

        <hr>

        <%
            Cookie[] cookies = request.getCookies();
            String uname = "";
            String upwd = "";
            if (cookies != null){
                for (Cookie cookie : cookies) {
                    if (cookie.getName().equals("uname")){
                        uname = cookie.getValue();
                    }

                    if (cookie.getName().equals("upwd")){
                        upwd = cookie.getValue();
                    }
                }
            }
        %>

        <%="uname==="+uname%>
        <%="upwd==="+upwd%>

        <hr>

        uname===----${cookie.uname.value}
        <br>
        upwd===---${cookie.upwd.value}

    </body>
</html>
```

## 二、JSTL

### 2.1 概述

* jsp标准标签库
* EL能获取数据，不能对数据进行流程控制、循环遍历之类的操作
* EL结合JSTL可以实现

### 2.2 使用JSTL

* 导入jar包
  * jstl.jar
  * standard.jsr
* taglib引入jsp的内核
  * <%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>

### 2.3 JSTL条件判断

```jsp
<%@ page import="com.qf.entity.User" %><%--
  Created by IntelliJ IDEA.
  User: Dushine2008
  Date: 2021/6/22
  Time: 10:53
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<html>
    <head>
        <title>Title</title>
    </head>
    <body>

        <%
            User user = new User("zhangsan","123");
            request.setAttribute("user",user);
        %>

        <%--  如果test=true，执行if之间的内容，否则不执行,只有if，没有else  --%>
        <c:if test="false">
            <h3>if判断成立</h3>
        </c:if>
        <hr>

        <c:if test="${user.username == 'zhangsan'}">
            <h3>欢迎您，${user.username}</h3>
        </c:if>
        <c:if test="${user.username != 'zhangsan'}">
            <h3>用户名错误</h3>
        </c:if>
    </body>
</html>
```

### 2.4 JSTL分支语句

```jsp
<%--
  Created by IntelliJ IDEA.
  User: Dushine2008
  Date: 2021/6/22
  Time: 11:04
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<html>
    <head>
        <title>分支</title>
    </head>
    <body>
        <%
            request.setAttribute("score",108);
        %>

        <%--    雷同java中的switch分支语法    --%>
        <c:choose>
            <c:when test="${score>=0 && score<60}">不及格</c:when>
            <c:when test="${score>=60 && score<70}">及格</c:when>
            <c:when test="${score>=70 && score<80}">中等</c:when>
            <c:when test="${score>=80 && score<90}">良好</c:when>
            <c:when test="${score>=90 && score<=100}">优秀</c:when>
            <c:otherwise>成绩不存在</c:otherwise>
        </c:choose>

        <%--    完成月份和季节、星期和课程的案例    --%>
    </body>
</html>
```

### 2.5 JSTL循环

```jsp
<%--
  Created by IntelliJ IDEA.
  User: Dushine2008
  Date: 2021/6/22
  Time: 11:11
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<html>
    <head>
        <title>JSTL遍历</title>
    </head>
    <body>
        <%
            int[] arr = {111,222,333,444,555,666,777,888,999};
            request.setAttribute("arr",arr);
        %>
        <%--
            ​var="变量名"
        ​	items="集合"
        ​	begin="起始下标"
        ​	end="结束下标"
        ​	step="间隔长度"
        ​	varstatus="遍历状态">
        --%>
        <c:forEach var="num" items="${arr}" begin="1" end="7" step="2" varStatus="vs">
            <h4>${num}====顺序:${vs.count}===索引:${vs.index}</h4>
        </c:forEach>

    </body>
</html>
```

### 2.6 获取数据添加到页面

```jsp
<%--
  Created by IntelliJ IDEA.
  User: Dushine2008
  Date: 2021/6/22
  Time: 11:18
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<html>
    <head>
        <title>水浒英雄表</title>
    </head>
    <body>
        ${shuihus}
    </body>

    <table border="" width="500px" align="center">
        <tr>
            <th>id</th>
            <th>姓名</th>
            <th>性别</th>
            <th>地址</th>
            <th>备注</th>
        </tr>

        <c:forEach var="shuihu" items="${shuihus}">
            <tr>
                <td>${shuihu.id}</td>
                <td>${shuihu.username}</td>
                <td>${shuihu.gender}</td>
                <td>${shuihu.address}</td>
                <td>${shuihu.info}</td>
            </tr>
        </c:forEach>

    </table>

</html>
```

### 2.7 cookie被禁用的情况

```jsp
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<%--
  Created by IntelliJ IDEA.
  User: Dushine2008
  Date: 2021/6/22
  Time: 11:34
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
    <head>
        <title>Title</title>
    </head>
    <body>
        <%
            String newUrl = response.encodeRedirectURL(request.getContextPath() + "/jstl/demo08.jsp");
        %>
        <%=
            newUrl
        %>
        <br>
        <c:url context="${pageContext.request.contextPath}" value="/jstl/demo08.jsp" />

    </body>
</html>
```

## 三、Git

### 3.1 概述

* 版本管理工具
* 协同开发管理工具

### 3.2 下载

* https://git-scm.com/download/win

### 3.3 安装

* 双击安装包===》一直下一步到最后

### 3.4 检查安装是否成功

* 在命令提示符运行git --version指令

### 3.5 创建工作区

* 创建空文件夹
* 使用git执行把这里认定为工作区

### 3.6 把工作区中的文件放入暂存区

* git add .<fileName>
* 把工作区中所有<指定>文件放入暂存区

### 3.7 提交到版本分支

* git commit -m "提交信息"
  * 提交并标注提交信息
  * 提交信息如果是中文，在命名提示符中查看提交信息将得到不认识的内容

### 3.8 IDEA集成Git

