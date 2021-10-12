# Day30笔记

## 一、函数

### 1.1 概述

* 完成指定功能的代码块
* 可以通过函数名字重复调用

### 1.2 语法

```
function funcName(参数列表){
	方法体
}
```

### 1.3 函数案例

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>函数</title>
	</head>
	<body>
		<button type="button" onclick="func01()">无参数无返回值</button>
		<br>
		<button type="button" onclick="func002()">有参数无返回值</button>
		<br>
		<button type="button" onclick="func003()">无参数有返回值</button>
		<br>
		<button type="button" onclick="func004()">有参数有返回值</button>
		
	</body>
	<script type="text/javascript">
		/**
		 * 使用关键字function声明
		 * function FuncName(参数列表){
			 方法体
		   }
		 */
		// 无参数无返回值
		function func01(){
			alert("我是js中的无参数无返回值方法...");
		}
		
		// func01();
		
		// 有参数无返回值
		function func02(name,age){
			alert("name = " + name + ",age = " + age);
		}
		
		function func002(){
			/**
			 * js函数传入的参数会按照顺序赋值
			 * 	可以多于参数列表
			 * 	可以少于参数列表
			 */
			func02("张三",23,"杭州九堡");
			// 参数会放到数组中
		}
		
		// 无参数有返回值
		function func03(){
			return new Date();
		}
		
		function func003(){
			var ret = func03();
			alert(ret);
		}
		
		// 有参数有返回值
		function func04(a,b){
			return a+b;
		}
		
		function func004(){
			var ret = func04(33,55);
			alert("调用func04得到的结果:" + ret);
		}
		
	</script>

</html>
```

 

### 1.4 闭包

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>函数</title>
	</head>
	<body>
	</body>
	<script type="text/javascript">
		function func01(){
			alert("我是func01");
		}
		
		var ret = func01;
		// ret();
		
		function func02(){
			function func002(){
				alert("我是func002,我在函数func02中");
			}
			return func002;
		}
		
		var ret002 = func02();
		// ret002();
		
		
		function func03(){
			var counter = 0;
			counter++;
			console.log(counter);
		}
		func03();
		func03();
		func03();
		
		counter = 30;
		func03();
		func03();
		func03();
		
		console.log("=======");
		
		// 闭包
		var add = (function () {
		    var counter = 0;
		    return function () {return counter += 1;}
		})();
		
		var result; 
		result = add();
		console.log(result);
		
		result = add();
		console.log(result);
		
		result = add();
		console.log(result);
		
	</script>
</html>
```

### 1.5 函数和对象

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>函数和对象</title>
	</head>
	<body>
	</body>
	<script type="text/javascript">
		
		//创建对象
		function Person(name,age,addr){
			this.name = name;
			this.age = age;
			this.addr = addr;
		}
		
		var p = new Person("张三",23,"九堡");
		console.log(p);
		
		
		class Stu{
			constructor(name,age,addr) {
			    this.name = name;
			    this.age = age;
			    this.addr = addr;
			}
			
			show(){
				console.log("我是stu中的show");
			}
		}
		
		var stu = new Stu("李四",24,"五堡家园");
		console.log(stu);
		stu.show();
		
		class Student extends Stu{
			constructor(name,age,addr) { 
				super();
			    this.name = name;
			    this.age = age;
			    this.addr = addr;
			}
			
			show(){
				console.log("我是student中的show");
			}
		}
		
		var student = new Student("王五",25,"八堡");
		console.log(student);
		student.show();
	</script>
</html>
```

## 二、内置方法

### 2.1内置弹窗函数

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>弹窗函数</title>
	</head>
	<body>
		<button type="button" onclick="func01()">提示</button>
		<br>
		
		<button type="button" onclick="func02()">确认</button>
		<br>
		
		<button type="button" onclick="func03()">输入</button>
		<br>
		
	</body>
	<script type="text/javascript">
		
		function func01(){
			alert("我是alert弹窗,只是给出提示或者警告...");
		}
		
		function func02(){
			var ret = confirm("我是confirm弹窗,可以选择确定或者取消");
			// alert("我是confirm的选择结果:" + ret);
			if (ret) {
				alert("密码保存成功");
			} else{
				alert("放弃保存密码");
			}
		}
		
		function func03(){
			var ret = prompt("我是confirm弹窗,可以输入信息","静夜思");
			alert("我是prompt的选择结果:" + ret);
		}
		
	</script>
</html>
```

### 2.2 乘法表

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>乘法表</title>
	</head>
	<body>
		
	</body>
	
	<script type="text/javascript">
		
		for (var i = 1; i <= 9; i++) {
			for (var j = 1; j <= i; j++) {
				document.write(j + "*" + i + "=" + j*i + "&nbsp;&nbsp;&nbsp;&nbsp;");
			}
			document.write("<br>");
		}
		
	</script>
</html>
```

### 2.3 键盘录入

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>录入数据</title>
	</head>
	<body>
		<button type="button" onclick="inputNum()">计算</button>
	</body>
	
	<script type="text/javascript">
		
		function getSum(n){
			var sum = 0;
			for (var i = 1; i <= n; i++) {
				sum += i;
			}
			alert("1---" + n + "累加的结果是:" + sum);
			return sum;
		}
		
		function inputNum(){
			var n = prompt("请输入数字n","1");
			console.log("n的类型是" + (typeof n));
			
			var num = parseInt(n);
			console.log("num的类型是" + (typeof num));
			
			getSum(num);
		}

	</script>
	
</html>
```

## 三、事件

### 3.1 概述

* 在html页面发生的一件事
* 可以使用函数去响应事件

### 3.2 鼠标事件

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>事件01</title>
		<style type="text/css">
			
			#box{
				width: 300px;
				height: 300px;
				background-color: red;
			}
			
			#box01{
				width: 300px;
				height: 300px;
				background-color: green;
			}
			
			#box02{
				width: 300px;
				height: 300px;
				background-color: blue;
			}
			
		</style>
	</head>
	<body>
		<!-- 添加鼠标单击事件 -->
		<div id="box" onclick="changeColor()">
		</div>
		
		<div id="box01" ondblclick="click02()">
			
		</div>
		
		<div id="box02" onmouseover="overDiv()" onmouseout="outDiv()">
			
		</div>
	</body>
	<script type="text/javascript">
		
		function changeColor(){
			var r = Math.floor(Math.random()*256);
			var g = Math.floor(Math.random()*256);
			var b = Math.floor(Math.random()*256);
			document.getElementById("box").style.backgroundColor = "rgb("+r+","+g+","+b+")";
		}
		
		function click02(){
			console.log("双击.." + Math.random());
		}
		
		function overDiv(){
			document.getElementById("box02").style.width = "500px";
			document.getElementById("box02").style.height = "500px";
		}
		
		function outDiv(){
			document.getElementById("box02").style.width = "300px";
			document.getElementById("box02").style.height = "300px";
		}
		
	</script>
</html>
```

### 3.3 键盘事件

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>事件02</title>
	</head>
	<body>
	</body>
	<script type="text/javascript">
		
		document.onkeypress = function(event){
			console.log(event.keyCode);
			var code = event.keyCode;
			switch (code){
				case 119:
					console.log("向上...");
					break;
				
				case 115:
					console.log("向下...");
					break;
					
				case 97:
					console.log("向左...");
					break;
					
				case 100:
					console.log("向右...");
					break;
				default:
					console.log("哈哈哈哈哈哈哈");
					break;
			}
		}
		
	</script>
</html>
```

### 3.4 页面加载事件

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>事件03</title>
		
		<script type="text/javascript">
			
			window.onload = function(){
				document.getElementById("box").style.backgroundColor = "blue";
			}
			
		</script>
		
		<style type="text/css">
			#box{
				width: 300px;
				height: 300px;
				background-color: red;
			}
		</style>
	</head>
	<body>
		<div id="box">
			
		</div>
	</body>
</html>
```

 

### 3.5 表单事件

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>表单事件</title>
	</head>
	<body>
		<form method="get" id="formLogin">
			
			<table align="center">
				<tr>
					<td align="right">
						用户名
					</td>
					<td>
						<input type="text" name="username" id="username" placeholder="请输入用户名" onfocus="changeUsernameBorder()" onblur="changeUsernameNotice()"/>
					</td>
					<td>
						<span id="usernameNoeict" style="display: none;">
							
						</span>
					</td>
				</tr>
				
				<tr>
					<td align="right">
						密码
					</td>
					<td>
						<input type="password" name="password" id="password" placeholder="请输入密码"  onfocus="changePasswordBorder()" onblur="changePasswordNotice()"/>
					</td>
				</tr>
				<tr>
					<td>
						<input type="submit" value="提交"/>
					</td>
				</tr>
			</table>
		</form>
		
		<button type="button" onclick="submitForm()">提交表单</button>
		
	</body>
	
	<script type="text/javascript">
		
		function changeUsernameBorder(){
			document.getElementById("username").style.borderStyle = "solid";
			document.getElementById("username").style.borderColor = "red";
			document.getElementById("username").style.borderWidth = "10px";
		}
		
		function changeUsernameNotice(){
			document.getElementById("username").style.borderColor = "lightgrey";
			var value = document.getElementById("username").value;
			
			
			if (value.length < 6) {
				document.getElementById("usernameNoeict").style.display = "inline";
				document.getElementById("usernameNoeict").innerText = "用户名太短";
			} else{
				document.getElementById("usernameNoeict").style.display = "inline";
				document.getElementById("usernameNoeict").innerText = "用户名可用";
			}
		}
		
		function submitForm(){
			document.getElementById("formLogin").submit();
		}
		
	</script>
	
</html>
```

## 四、正则表达式

### 4.1 概述

* 正则表达式是由一个字符序列形成的搜索模式。
* 当你在文本中搜索数据时，你可以用搜索模式来描述你要查询的内容。
* 正则表达式可以是一个简单的字符，或一个更复杂的模式。
* 正则表达式可用于所有文本搜索和文本替换的操作。

### 4.2 正则表达式案例

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>正则表达式</title>
	</head>
	<body>
	</body>
	<script type="text/javascript">
		var str = "Visit Runoob!"; 
		var n = str.search(/Runoob/i);
		console.log(n);
		
		var ret = str.search("Runoob");
		console.log(ret);
		
		ret = str.replace(/Runoob/,"JavaScript");
		console.log(ret);
		
		var patt = /best/;
		ret = patt.test("The best things in life are free!");
		console.log(ret);
		
		patt = /1[3-9][0-9]{9}/;
		ret = patt.test("11937012800");
		console.log(ret);
		
		patt = /[\d\w]{6,20}@(126|163|qq)\.com/;
		ret = patt.test("dushine@126.com");
		console.log(ret);
	</script>
</html>
```

## 五、DOM

### 5.1 概述

* 文档对象模型(Document Object Model)
* 把整个html页面看成一个文档对象
  * 文档中有很多的子节点
  * html
    * head
      * mate
      * title
    * body
      * div
      * p
      * table
      * a
      * 。。。 。。。

* 能对文档中的各种元素进行

  * 增加
  * 删除
  * 修改
  * 查询
  * ... ...

  

### 5.2 通过id获取元素

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>DOM-查找</title>
	</head>
	<body>
		<h3 id="title01">
			草000
			<a href="">
				草
			</a>
		</h3>
		<p class="con" id="con01">离离原上草，</p>
		<p class="con" id="con02">一岁一枯荣。</p>
		<p class="con" id="con03">野火烧不尽，</p>
		<p class="con" id="con04">春风吹又生。</p>
		
		<button type="button" onclick="getTagById()">id获取标记</button>
	</body>
	
	<script type="text/javascript">
		/**
		 * id
		 * class
		 * tag
		 * 
		 */
		function getTagById(){
			var title01 = document.getElementById("title01");
			console.log(title01);
			// 获取文本内容
			console.log(title01.innerText);
			
			// 获取html内容
			console.log(title01.innerHTML);
			title01.style.color = "red";
		}
		
	</script>
	
</html>
```

### 5.3 通过class标签名获取标签

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>DOM-查找</title>
	</head>
	<body>
		<h3 id="title01">
			<a href="">
				草
			</a>
		</h3>
		<p class="con-cao" id="con01">离离原上草，</p>
		<p class="con-cao" id="con02">一岁一枯荣。</p>
		<p class="con-cao" id="con03">野火烧不尽，</p>
		<p class="con-cao" id="con04">春风吹又生。</p>
		
		<h3 id="title02">黄鹤楼</h3>
		<p class="con-lou" id="con05">故人西辞黄鹤楼，</p>
		<p class="con-lou" id="con06">烟花三月下扬州。</p>
		<p class="con-lou" id="con07">孤帆远影碧空尽，</p>
		<p class="con-lou" id="con08">唯见长江天际流。</p>
		<button type="button" onclick="getTagById()">id获取标记</button>
		<button type="button" onclick="getTagByclass()">class获取标签</button>
		<button type="button" onclick="getTagByTagName()">标签名字获取标签</button>
	</body>
	
	<script type="text/javascript">
		/**
		 * id
		 * class
		 * tag
		 * 
		 */
		function getTagById(){
			var title01 = document.getElementById("title01");
			console.log(title01);
			// 获取文本内容
			console.log(title01.innerText);
			
			// 获取html内容
			console.log(title01.innerHTML);
			title01.style.color = "red";
		}
		
		function getTagByclass(){
			var cons = document.getElementsByClassName("con-lou");
			console.log(cons);
			for (var i = 0; i < cons.length; i++) {
				console.log(cons[i].innerText);
			}
		}
		
		function getTagByTagName(){
			var titles = document.getElementsByTagName("h3");
			console.log(titles);
			for (var i = 0; i < titles.length; i++) {
				console.log(titles[i].innerText);
			}
		}
		
	</script>
	
</html>
```

### 5.4 获取上下级元素

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>DOM-查找</title>
	</head>
	<body>
		<ul id="xiyouji">
			<li>孙悟空</li>
			<li>猪八戒</li>
			<li>沙和尚</li>
			<li>白龙马</li>
		</ul>
		
		<ul id="shuihu">
			<li>宋江</li>
			<li>林冲</li>
			<li>鲁智深</li>
			<li>扈三娘</li>
		</ul>
		
		<button type="button" onclick="getXiYou()">获取西游记人物</button>
		<button type="button" onclick="getShuiHu()">获取水浒传人物</button>
		
	</body>
	<script type="text/javascript">
		function getXiYou(){
			var xiyouji = document.getElementById("xiyouji");
			console.log(xiyouji);
			
			var lis = xiyouji.children;
			console.log(lis);
		}
		
		function getShuiHu(){
			var shuihu = document.getElementById("shuihu");
			console.log(shuihu);
			
			var lis = shuihu.children;
			console.log(lis);
			
			var p = shuihu.parentElement;
			console.log(p);
		}
	</script>
</html>
```

