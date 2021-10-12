# Day28笔记

## 一、定位属性

### 1.1 相对定位

* position:relative
* 不会脱离原来的文档流，元素原本的位置会继续被占用
* 可以向指定方向偏移

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>相对定位</title>
		
		<style type="text/css">
			div{
				width: 300px;
				height: 300px;
				float: left;
				top: 150px;
			}
			
			#box01{
				position: relative;
				background-color: red;
				left: 150px;
			}
			
			#box02{
				background-color: green;
			}
			
			#box03{
				background-color: blue;
			}
		</style>
		
	</head>
	<body>
		<div id="box01">
			box01
		</div>
		
		<div id="box02">
			box02
		</div>
		
		<div id="box03">
			box03
		</div>
	</body>
</html>
```

### 1.2 绝对定位

* position:absolate
* 会脱离原来的文档流，元素原来的位置会空出
* 摆放的位置相对于浏览器窗口的左上角

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>绝对定位</title>
		
		<style type="text/css">
			div{
				width: 300px;
				height: 300px;
			}
			
			#box{
				width: 800px;
				height: 800px;
				border: 1px solid red;
				margin: auto;
			}
			
			#box01{
				width: 200px;
				height: 200px;
				position: absolute;
				background-color: red;
				left: 200px;
				top: 200px;
			}
			
			#box02{
				background-color: green;
			}
			
			#box03{
				background-color: blue;
			}
		</style>
		
	</head>
	<body>
		<div id="box">
			<div id="box01">
			box01
			</div>
			
			<div id="box02">
				box02
			</div>
			
			<div id="box03">
				box03
			</div>
		</div>
		
	</body>
</html>
```

### 1.3 固定定位

* position:fixed
* 会脱离原来的文档流，元素原来的位置空出
* 摆放参考浏览器窗口左上角
* 无论其他元素怎么变换，对此元素无影响

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>固定定位</title>
		
		<style type="text/css">
			div{
				width: 300px;
				height: 300px;
			}
			
			#box{
				position: fixed;
				left: 400px;
				top: 300px;
			}
			
			.con-1{
				background-color: red;
			}
			
			.con-2{
				background-color: green;
			}
			
			.con-3{
				background-color: blue;
			}
			
		</style>
		
	</head>
	<body>
		<div id="box">
			<img src="img/pic00.jpg" style="width: 100%;height: 100%;">
		</div>
		
		<div class="con-1">
			box01
		</div>
		
		<div class="con-2">
			box02
		</div>
		
		<div class="con-3">
			box03
		</div>
		
		<div class="con-1">
			box01
		</div>
		
		<div class="con-2">
			box02
		</div>
		
		<div class="con-3">
			box03
		</div>
		
	</body>
</html>
```

## 二、盒子模型

### 2.1 边框属性

* border
* 可以分别设置上下左右的边框，也可以同时设置所有边框

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>盒子模型</title>
		
		<style type="text/css">
			#box{
				height: 300px;
				width: 300px;
				/* border-color: red;
				border-width: 10px;
				border-style: dotted; */
				border: solid red 1px;
			}
			
			#box0{
				height: 300px;
				width: 300px;
				border-color: red;
				border-right-color: blue;
				border-right-width: 5px;
				border-right-style: dotted;
			}
		</style>
		
	</head>
	<body>
		<div id="box">
			box
		</div>
		
		<div id="box0">
			box0
		</div>
	</body>
</html>
```

### 2.2 内边距

* padding
* 内容距离父元素内边距
* 可以设置上下左右等方向
* 会把父元素占用的大小改变

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>内边距</title>
		
		<style type="text/css">
			div{
				width: 300px;
				height: 300px;
				border: 1px solid red;
			}
			
			#box001{
				width: 200px;
				height: 200px;
				padding-left: 50px;
				padding-top: 50px;
			}
			
			#box002{
				width: 200px;
				height: 200px;
			}
			
		</style>
		
	</head>
	<body>
		<div id="box01">
			<div id="box001">
				box001
			</div>
		</div>
		
		<div id="box02">
			<div id="box002">
				box002
			</div>
		</div>
		
		<div id="box03">
			box03
		</div>
	</body>
</html>
```

### 2.3 外边距

* margin
* 内容距离父元素的外边距
* 可以分别设置上下左右等方向
* 不会把父元素扩大，会挤走相邻的元素

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>外边距</title>
		
		<style type="text/css">
			div{
				width: 200px;
				height: 200px;
				border: 1px solid red;
			}
			
			#box{
				width: 800px;
				height: 800px;
			}
			
			#box001{
				width: 100px;
				height: 100px;
				margin-left: 50px;
				margin-top: 50px;
			}
			
			#box01{
				margin-top: 50px;
			}
		</style>
		
	</head>
	<body>
		<div id="box">
			<div id="box01">
				<div id="box001">
					box001
				</div>
			</div>
			
			<div id="box02">
				box02
			</div>
			
			<div id="box03">
				box03
			</div>
		</div>
	</body>
</html>
```

### 2.4 计算水平方向占用大小

* 左外边距
* 左边框
* 左内边距
* 左侧宽度
* 右侧宽度
* 右内边距
* 右边框
* 右外边距

### 2.5 计算垂直方向占用大小

## 三、山寨淘宝

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>山寨淘宝</title>
	</head>
	
	<style type="text/css">
		#box{
			width: 1200px;
			height: 1000px;
			margin: auto;
			background-color: antiquewhite;
		}
		
		#title{
			width: 80%;
			height: 32px;
			margin: auto;
		}
		
		#title-left{
			float: left;
			width: 380px;
			line-height: 32px;
		}
		
		#title-right{
			float: right;
			width: 570px;
			line-height: 32px;
		}
		
		a{
			font-size: 14px;
		}
		
		#search{
			width: 80%;
			height: 64px;
			margin: auto;
		}
		
		#search-left{
			float: left;
			width: 240px;
			height: 64px;
			text-align: center;
		}
		
		#search-right{
			float: right;
			width: 715px;
			height: 64px;
		}
		
		#search-right-search{
			width: 715px;
			height: 30px;
		}
		
		#search-right-hotword{
			width: 715px;
			height: 30px;
		}
		
		#guess{
			width: 80%;
			line-height: 48px;
			margin: auto;
			text-align: center;
			background-color: aliceblue;
		}
		
		#self-option{
			width: 80%;
			height: 48px;
			margin: auto;
		}
		
		#product{
			width: 80%;
			height: 800px;
			margin: auto;
			text-align: center;
		}
		
		#product table{
			text-align: center;
			margin: auto;
		}
		
		#product-tb img{
			width: 180px;
		}
		
	</style>
	
	<body>
		<div id="box">
			<!-- 标题栏 -->
			<div id="title">
				<div id="title-left">
					<a href="" style="margin-left: 20px;">
						<font size="" color="red">
							亲，请登录
						</font>
					</a>
					
					<a href="" style="margin-left: 20px;">
						免费注册
					</a>
					
					<a href="" style="margin-left: 20px;">
						手机逛淘宝
					</a>
				</div>
				
				<div id="title-right">
					<a href="">
						淘宝网首页
					</a>
					<a href="">
						我的淘宝
					</a>
					<a href="">
						购物车
					</a>
					<a href="">
						收藏夹
					</a>
					<a href="">
						商品分类
					</a>
					<a href="">
						卖家中心
					</a>
					<a href="">
						联系客服
					</a>
					<a href="">
						网站导航
					</a>
				</div>
			</div>
			
			<!-- 搜索栏 -->
			<div id="search">
				<!-- logo -->
				<div id="search-left">
					<img src="img/taobao-logo.png" style="height: 100%;">
				</div>
				
				<!-- 搜索和热词 -->
				<div id="search-right">
					
					<div id="search-right-search">
						<input type="text" style="width: 400px;"/>
						<input type="button" value="搜索" />
					</div>
					
					<div id="search-right-hotword">
						<a href="">客厅灯</a>
						<a href="">冲锋衣</a>
						<a href="">床垫</a>
						<a href="">沙发垫</a>
						<a href="">男内裤</a>
						<a href="">电脑桌</a>
						<a href="">鞋柜</a>
						<a href="">窗帘</a>
						<a href="">椅子</a>
					</div>
					
				</div>
				
			</div>
			
			<!-- 猜你想要 -->
			<div id="guess">
				<span>你是不是想要:</span>
				<a href="">客厅灯</a>
				<span> |</span>
				<a href="">冲锋衣</a>
				<span> |</span>
				<a href="">床垫</a>
				<span> |</span>
				<a href="">沙发垫</a>
				<span> |</span>
				<a href="">男内裤</a>
				<span> |</span>
				<a href="">电脑桌</a>
				<span> |</span>
				<a href="">鞋柜</a>
				<span> |</span>
				<a href="">窗帘</a>
				<span> |</span>
				<a href="">椅子</a>
			</div>
			
			<!-- 选项 -->
			<div id="self-option">
				
			</div>
			
			<div id="product">
				<!-- 商品展示 -->
				<table border="" cellspacing="" cellpadding="" id="product-tb">
					<tr>
						<td>
							<img src="img/pic03.jpg">
							<br>
							<font size="" color="red">
								&yen;40.0 包邮
							</font>
							<br>
							<span id="">
								世界上最好的商品
							</span>
							<br>
							<span>
								潮色服饰专营店
							</span>
							<br>
							<span>
								如实描述4.8
							</span>
						</td>
						<td>
							<img src="img/pic03.jpg">
							<br>
							<font size="" color="red">
								&yen;40.0 包邮
							</font>
							<br>
							<span id="">
								世界上最好的商品
							</span>
							<br>
							<span>
								潮色服饰专营店
							</span>
							<br>
							<span>
								如实描述4.8
							</span>
						</td>
						<td>
							<img src="img/pic03.jpg">
							<br>
							<font size="" color="red">
								&yen;40.0 包邮
							</font>
							<br>
							<span id="">
								世界上最好的商品
							</span>
							<br>
							<span>
								潮色服饰专营店
							</span>
							<br>
							<span>
								如实描述4.8
							</span>
						</td>
						<td>
							<img src="img/pic03.jpg">
							<br>
							<font size="" color="red">
								&yen;40.0 包邮
							</font>
							<br>
							<span id="">
								世界上最好的商品
							</span>
							<br>
							<span>
								潮色服饰专营店
							</span>
							<br>
							<span>
								如实描述4.8
							</span>
						</td>
						<td>
							<img src="img/pic03.jpg">
							<br>
							<font size="" color="red">
								&yen;40.0 包邮
							</font>
							<br>
							<span id="">
								世界上最好的商品
							</span>
							<br>
							<span>
								潮色服饰专营店
							</span>
							<br>
							<span>
								如实描述4.8
							</span>
						</td>
					</tr>
					
					<tr>
						<td>
							<img src="img/pic03.jpg">
							<br>
							<font size="" color="red">
								&yen;40.0 包邮
							</font>
							<br>
							<span id="">
								世界上最好的商品
							</span>
							<br>
							<span>
								潮色服饰专营店
							</span>
							<br>
							<span>
								如实描述4.8
							</span>
						</td>
						<td>
							<img src="img/pic03.jpg">
							<br>
							<font size="" color="red">
								&yen;40.0 包邮
							</font>
							<br>
							<span id="">
								世界上最好的商品
							</span>
							<br>
							<span>
								潮色服饰专营店
							</span>
							<br>
							<span>
								如实描述4.8
							</span>
						</td>
						<td>
							<img src="img/pic03.jpg">
							<br>
							<font size="" color="red">
								&yen;40.0 包邮
							</font>
							<br>
							<span id="">
								世界上最好的商品
							</span>
							<br>
							<span>
								潮色服饰专营店
							</span>
							<br>
							<span>
								如实描述4.8
							</span>
						</td>
						<td>
							<img src="img/pic03.jpg">
							<br>
							<font size="" color="red">
								&yen;40.0 包邮
							</font>
							<br>
							<span id="">
								世界上最好的商品
							</span>
							<br>
							<span>
								潮色服饰专营店
							</span>
							<br>
							<span>
								如实描述4.8
							</span>
						</td>
						<td>
							<img src="img/pic03.jpg">
							<br>
							<font size="" color="red">
								&yen;40.0 包邮
							</font>
							<br>
							<span id="">
								世界上最好的商品
							</span>
							<br>
							<span>
								潮色服饰专营店
							</span>
							<br>
							<span>
								如实描述4.8
							</span>
						</td>
					</tr>
				</table>
			</div>
		</div>
	</body>
</html>
```

## 四、JavaScript

### 4.1 概述

* 解释性执行的脚本语言
* 和java名字很像，借鉴了一些java的语法

### 4.2 js组成

* ECMAScript语法
* DOM
* BOM

### 4.3 开发环境搭建

#### 代码编写工具

* HBulider

#### 代码运行、调试工具

* 浏览器
* 推荐使用
  * google
  * Firefox

### 4.4 我的第一个js代码

#### 内嵌js

* 书写在标签内部
* 只对当前标签起作用

#### 内部js

* 书写在html文件内部
* 位置自定义
* 对整个html文件起作用

#### 外部js

* html文件外部的独立文件
* 可以通过script标签引入
* 可以在整个项目中使用

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>js引入方式</title>
		
		<script src="js/main.js" type="text/javascript" charset="utf-8"></script>
		
	</head>
	<body>
		<!-- 
			js内嵌样式
				把js代码写在标签内部
		 -->
		<button type="button" onclick="alert('Hello JavaScript!')">点我</button>
		<button type="button" onclick="func()">内部js</button>
		
		<button type="button" onclick="func00()">外部js</button>
	</body>
		
	<!-- 
		内部js代码
			书写在html文件内部
	 -->
	<script type="text/javascript">
		function func(){
			alert("在函数中点我");
		}
	</script>
</html>
```

## 五、js变量和数据类型

### 5.1 变量名

* 需要是一个合法的标识符
* 见明知义
* 不能使用关键字
* 都是用var声明

### 5.2 js基本数据类型

* number
  * 整数
  * 小数
* string
  * 所有字符和字符串都是此类的实例
* undefined
  * 未定义的内容成为undefined

* boolean
  * true
  * false

* 查看变量数据类型
  * typeof 变量
* 变量的数据类型取决于变量的值
* 变量可以多次赋不同类型的值

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>js数据类型</title>
	</head>
	<body>
		
	</body>
	
	<script type="text/javascript">
		
		// 声明变量a
		var a;
		console.log("a=" + a);
		
		// 赋值10
		a = 10;
		console.log("a=" + a);
		var b = "10";
		console.log("b=" + b);
		
		console.log(typeof a);
		console.log(typeof b);
		
		var c = 3.14;
		console.log(typeof c);
		
		var d = 'hello';
		console.log(typeof d);
		
		var e = true;
		console.log(typeof e);
		
		console.log(typeof f);
		
		console.log("=======================");
		
		a = "true";
		console.log(a);
		
		f = "World";
		console.log(f);
		
	</script>
	
</html>
```



### 5.3 引用数据类型

#### js对象

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>js引用类型</title>
	</head>
	<body>
	</body>
	<script type="text/javascript">
		// 第一种创建对象方式
		var stu = new Object();
		console.log(stu);
		
		stu.name = "张三";
		stu.age = 23;
		stu.addr = "九堡";
		stu.info = "法外狂徒";
		
		console.log(stu);
		console.log(typeof stu);
		
		console.log(stu.name);
		console.log(stu.age);
		
		console.log(typeof stu.name);
		
		stu.age = 24;
		console.log(stu.age);
		
		// 第二种创建对象方式
		var s = {
			name:"李四",
			age:24,
			addr:"八堡",
			info:"法外狂徒张三的好友"
		};
		console.log(s);
		
		console.log(s.addr);
		console.log(s.info);
		
		// 第三种创建对象的方式
		var student = {
			"name":"王五",
			"age":25,
			"addr":"七堡",
			"info":"法外狂徒张三的小迷弟"
		};
		console.log(student);
		
	</script>
</html>
```

### 5.4 js数组

```html
R
	</head>
	<body>
	</body>
	<script type="text/javascript">
		// 创建数组的第一种方式
		var arr01 = [111,222,333];
		// 访问数组元素：通过索引，从0开始
		console.log(arr01);
		console.log(arr01[0]);
		console.log(arr01.length);
		
		console.log(arr01[1]);
		console.log(arr01[2]);
		
		// 修改数组元素
		arr01[0] = 1010;
		console.log(arr01[0]);
		
		// 如果索引超出范围，不报错，结果是undefined
		console.log(arr01[10]);
		console.log(arr01);
		
		// 给索引范围以外的赋值，能赋值成功，数组长度变化
		arr01[10] = 111000;
		console.log(arr01);
		console.log(arr01.length);
		
		console.log(arr01[3]);
		
		arr01[-1] = 1122;
		console.log(arr01);
		
		console.log(arr01[-1]);
		
	</script>
</html>
```

