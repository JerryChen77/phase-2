# Day31笔记

## 一、查询元素

* 通过id查询
* 通过class查
* 通过Tag名称查
* 查询子元素

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>查找元素</title>
	</head>
	<body>
		<h3 id="title01">九月九日忆山东兄弟</h3>
		<p class="con" id="con01">独在异乡为异客，</p>
		<p class="con" id="con02">每逢佳节倍思亲。</p>
		<p class="con" id="con03">遥知兄弟登高处，</p>
		<p class="con" id="con04">遍插茱萸少一人。</p>
		
		<button type="button" onclick="getTitle()">查询标题</button>
		<button type="button" onclick="getCon()">查询内容</button>
		
		<hr >
		
		<form method="get">
			昵称:
			<input type="text" id="username" placeholder="请输入昵称..." onblur="checkUname()"/>
			<span id="uname">
				
			</span>
			<br>
			
			密码:
			<input type="password" name="password" placeholder="请输入密码..." onblur="checkUpwd()" />
			<span id="upwd">
				
			</span>
			<br>
			
			<input type="submit" value="注册"/>
		</form>
		
		<ul id="humans">
			<li>罗翔</li>
			<li>鲁迅</li>
			<li>周树人</li>
			<li>贺龙</li>
		</ul>
		<button type="button" onclick="getHumans()">读取所有人</button>
		
	</body>
	
	<script type="text/javascript">
		
		function getTitle(){
			var title01 = document.getElementById("title01");
			console.log(title01.innerText);
		}
		
		function getCon(){
			var cons = document.getElementsByClassName("con");
			for (var i = 0; i < cons.length; i++) {
				console.log(cons[i].innerText);
			}
		}
		
		function checkUname(){
			var username = document.getElementById("username");
			console.log(username.value);
			if (username.value.length >= 6) {
				document.getElementById("uname").innerText = "用户名可用";
			} else{
				document.getElementById("uname").innerText = "用户名应是长度大于6的字符序列";
			}
		}
		
		function getHumans(){
			var ul0 = document.getElementById("humans");
			var humans = ul0.children;
			for (var i = 0; i < humans.length; i++) {
				console.log(humans[i].innerText);
			}
		}
		
	</script>
	
</html>
```

## 二、添加元素

* 创建子元素中的内容
* 创建子元素
* 把内容放入子元素
* 子元素放入父元素

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>添加标签</title>
	</head>
	<body>
		<ul id="dishes">
			<li>佛跳墙</li>
			<li>东坡肉</li>
		</ul>
		
		<input type="text" id="dish-name" value="" placeholder="请输入想要的菜品..."/>
		<button type="button" onclick="addDish()">加菜</button>
		
	</body>
	
	<script type="text/javascript">
		function addDish(){
			var dishName = document.getElementById("dish-name").value;
			
			if (dishName.length == 0) {
				alert("请输入菜名...");
				return;
			}
			
			// 创建文本标记
			var dishNode = document.createTextNode(dishName);
			
			// 创建li标记
			var dishLi = document.createElement("li");
			
			// 把文本标记放入li
			dishLi.appendChild(dishNode);
			
			// 把li放入ul
			var dishes = document.getElementById("dishes");
			dishes.appendChild(dishLi);
			
			document.getElementById("dish-name").value = "";
		}
	</script>
	
</html>
```

## 三、删除元素

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>删除元素</title>
	</head>
	<body>
		<ul id="JY">
			<li id="JY1001">JY1001房祖名</li>
			<li id="JY1002">JY1002张默</li>
			<li id="JY1003">JY1003柯震东</li>
			<li id="JY1004">JY1004陈羽凡</li>
			<li id="JY1005">JY1005尹相杰</li>
			<li id="JY1006">JY1006宋冬野</li>
		</ul>
		<input type="text" id="uname" placeholder="请输入要放人的编号" />
		<button type="button" onclick="release()">放人</button>
	</body>
	
	<script type="text/javascript">
		function release(){
			// 找到编号
			var uid = document.getElementById("uname").value;
			
			// 找到所有的li
			var JY = document.getElementById("JY");
			var lis = JY.children;
			
			for (var i = 0; i < lis.length; i++) {
				if (lis[i].id == uid) {
					JY.removeChild(lis[i]);
				}
			}
			document.getElementById("uname").value = "";
		}
	</script>
</html>
```

## 四、修改元素

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>修改元素</title>
	</head>
	<body>
		<h3 id="title02">登鹳雀楼</h3>
		<p id="con01" class="con">白日依山尽，</p>
		<p id="con02" class="con">黄河入海流。</p>
		<p id="con03" class="con">欲穷千里目，</p>
		<p id="con04" class="con">更上一层楼。</p>
		<button type="button" onclick="changeTitleColor()">改变标题颜色</button>
		<button type="button" onclick="changeTitle()">标题->链接</button>
		<hr >
		
		<div id="box">
			心灵鸡汤
		</div>
		<button type="button" onclick="getWord()">获取心灵鸡汤</button>
	</body>
	
	<script type="text/javascript">
		var arr = ["red","orange","yellow","green","cyan","blue","purple"];
		var count = 0;
		function changeTitleColor(){
			var title02 = document.getElementById("title02");
			// 修改颜色
			title02.style.color = arr[count%arr.length];
			count++;
		}
		
		var strs = ["只会幻想而不行动的人，永远也体会不到收获果实时的喜悦。",
		"嘲讽是一种力量，消极的力量。赞扬也是一种力量，但却是用心的力量。",
		"目标的坚定是性格中最必要的力量源泉之一，也是成功的利器之一。没有它，天才会在矛盾无定的迷径中徒劳无功。",
		"青春就像一只容器，装满了不安躁动青涩与偶尔的疯狂。",
		"同伴，不一定非要走到最后，某一段路上，对方给自己带来的朗朗笑声，那就已经足够。",
		"不去期望，失去了不会伤心，得到了便是惊喜。",
		"当你觉得又丑又穷的时候，不要悲伤，至少你的判断还是正确的。",
		"失败并不可怕，可怕的是到现在还有人相信这句话。",
		"真正努力过的人，就会明白天赋的重要。",
		"你之所以活得累，是因为心里装了多余的东西，跟吃饱了撑的是一个道理。"];
		function getWord(){
			var i = Math.floor(Math.random()*10);
			var box = document.getElementById("box");
			// 修改box中的内容
			box.innerText = strs[i];
		}
		
		function changeTitle(){
			var title02 = document.getElementById("title02");
			title02.innerHTML = "<a href=''>"+title02.innerText+"</a>";
		}
	</script>
</html>
```

## 五、事件传递

* 冒泡
  * 默认
* 捕获
  * 可以设置useCapture值为true的方式设置

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>事件传递</title>
		
		<style type="text/css">
			#box01{
				height: 300px;
				width: 300px;
				background-color: red;
			}
			
			#box02{
				height: 200px;
				width: 200px;
				background-color: green;
			}
			
			#box03{
				height: 100px;
				width: 100px;
				background-color: blue;
			}
		</style>
		
	</head>
	<body>
		<div id="box01">
			<div id="box02">
				<div id="box03">
					
				</div>
			</div>
		</div>
	</body>
	
	<script type="text/javascript">
		document.getElementById("box01").addEventListener("click",function(){console.log("red被点击...")},true);
		document.getElementById("box02").addEventListener("click",function(){console.log("green被点击...")},true);
		document.getElementById("box03").addEventListener("click",function(){console.log("blue被点击...")},true)
	</script>
	
</html>
```

## 六、常用类

### 6.1 Math

* Math 对象用于执行数学任务。
* 不用创建对象，可以直接调用方法

### 6.2 String

* String 对象用于处理文本（字符串）。

### 6.3 Date

* Date 对象用于处理日期和时间。

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>常用类</title>
	</head>
	<body>
	</body>
	<script type="text/javascript">
		console.log(Math.PI);
		console.log(Math.sqrt(9));
		console.log(Math.SQRT2);
		console.log(Math.pow(2,3));
		
		console.log("=======================");
		
		// 获取的方法
		var date = new Date();
		console.log(date);
		console.log(date.getFullYear());
		console.log(date.getMonth());
		console.log(date.getDay());
		console.log(date.getDate());
		console.log(date.getHours());
		console.log(date.getMinutes());
		console.log(date.getSeconds());
		console.log(date.getMilliseconds());
		console.log(date.getTime());
		
		// 设置的方法
		date.setFullYear(2019);
		date.setMonth(2);
		date.setDate(29);
		
		console.log(date);
		
		// 转换的方法
		console.log(date.toDateString());
		console.log(date.toTimeString());
		
	</script>
</html>
```

## 七、BOM

### 7.1 概述

* Browser Object Model
* 浏览器对象模型
* 把整个浏览器当做一个对象操作，有很多子节点
  * Screen
  * History
  * ... ...

### 7.2 Screen

### 7.3 Location

* Location 对象包含有关当前 URL 的信息。

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>Location</title>
	</head>
	<body>
		<button type="button" id="btn">跳转</button>
		<button type="button" id="btn0">再次跳转</button>
		<button type="button" id="btn00">又一次跳转</button>
	</body>
	<script type="text/javascript">
		console.log(window.location.host);
		console.log(window.location.hostname);
		console.log(window.location.url);
		console.log(window.location.port);
		console.log(window.location.href);
		
		// http://127.0.0.1:8848/Day31/9%E3%80%81BOM-Location.html
		
		document.getElementById("btn").addEventListener("click",function(){window.location.assign("http://www.baidu.com/")});
		
		document.getElementById("btn0").addEventListener("click",function(){window.location.href="http://www.taobao.com/"});
		
		document.getElementById("btn00").addEventListener("click",function(){window.location.replace("http://www.vip.com/")});
	</script>
</html>
```

### 7.4 History

* History 对象包含用户（在浏览器窗口中）访问过的 URL。
* History 对象是 window 对象的一部分，可通过 window.history 属性对其进行访问。

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>red</title>
		<style type="text/css">
			#box{
				width: 100%;
				height: 500px;
				text-align: center;
			}
			
			#box00{
				width: 500px;
				height: 300px;
				background-color: red;
				margin: auto;
			}
		</style>
	</head>
	<body>
		<div id="box">
			<div id="box00">
				
			</div>
			<button type="button" id="shang">上一页</button>
			<a href="green.html">绿色页面</a>
			<a href="blue.html">蓝色页面</a>
			<button type="button" id="xia">下一页</button>
		</div>
	</body>
	
	<script type="text/javascript">
		document.getElementById("shang").addEventListener("click",function(){
			window.history.back();
		});
		
		document.getElementById("xia").addEventListener("click",function(){
			window.history.forward();
		});
	</script>
	
</html>
```

### 7.5 Navigator 

* 对象包含有关浏览器的信息。

## 八、定时和倒计时

### 8.1 倒计时

* 时间到期后执行
* 只执行一次
* setTimeout

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
	</body>
	<script type="text/javascript">
		setTimeout(func,5000);
		
		function func(){
			alert("时间到");
		}
	</script>
</html>
```

### 8.2 定时

* 每间隔指定时间执行一次

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>定时器</title>
	</head>
	<body>
	</body>
	<script type="text/javascript">
		var timer = setInterval(func,1000);
		
		var count = 10;
		function func(){
			console.log(count);
			count--;
			if (count < 0) {
				clearInterval(timer);
			}
		}
		
	</script>
</html>
```

## 九、案例

### 9.1 轮播图

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>轮播图</title>
		<style type="text/css">
			#box{
				width: 650px;
				height: 515px;
				margin: auto;
			}
		</style>
	</head>
	<body>
		<div id="box">
			<img src="img/pic00.png" id="pic">
		</div>
	</body>
	
	<script type="text/javascript">
		// 定时器
		setInterval(changePic,1000);
		
		var index = 0;
		
		function changePic(){
			var pic = document.getElementById("pic");
			// 修改src
			pic.src = "img/pic0" + (index++ % 8) + ".png";
			console.log(pic.src);
		}
		
	</script>
	
</html>
```

### 9.2 点名器

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>点名器</title>
		
		<style type="text/css">
			#box{
				width: 500px;
				height: 200px;
				border: 1px solid red;
				margin: auto;
				margin-top: 300px;
				border-radius: 20px;
				background-color: aqua;
			}
			
			#box-name{
				width: 300px;
				line-height: 80px;
				border: 1px solid #008000;
				margin: auto;
				margin-top: 35px;
				border-radius: 15px;
				text-align: center;
				font-size: 32px;
				font-weight: 700;
				font-family: "黑体";
				background-color: antiquewhite;
			}
			
			#box-btn{
				width: 100px;
				line-height: 32px;
				border: 1px solid #008000;
				margin: auto;
				margin-top: 20px;
				border-radius: 15px;
				text-align: center;
				background-color: blueviolet;
				font-weight: 700;
				font-family: "黑体";
			}
		</style>
		
	</head>
	<body>
		<div id="box">
			<div id="box-name">
				点名器
			</div>
			
			<div id="box-btn">
				开始
			</div>
		</div>
	</body>
	
	<script type="text/javascript">
		var nameList = ["智文龙","聂梦佳","于伦明","龚哲明","梁日良","车菩轩","田仁光",
		"蔡波","高青爽","王佳敏","叶铤","陈竟伦","张雾进","陈兴隆","陈德锐","方安云","周权权",
		"周徐磊","高思远","刘翰臣","周论宇","宋跃","章楷铭","赵世春","丁森伦","胡轲祺","温从城",
		"张天业","马学远","李有国","胡洲豪","邓茂","田景旭","李重恩","胡海源","雷智高","田梦","何灵龙","刘彪"];
	
		// setInterval(changeName,50);
		var btn = document.getElementById("box-btn");
		
		btn.addEventListener("click",changeName);
		
		// 偶数次是开始，奇数次是要结束
		var count = 0;
		var timer;
		function changeName(){
			// 判断点击的是开始还是结束
			if (count % 2 == 0) {
				console.log("开始")
				btn.innerText = "结束";
				btn.style.backgroundColor = "red";
				
				// 开始后变化名字
				timer = setInterval(showName,50);
			} else{
				console.log("结束")
				btn.innerText = "开始";
				btn.style.backgroundColor = "green";
				
				// 清除定时器
				clearInterval(timer);
				
			}
			count++;
		}
		
		function showName(){
			var name = document.getElementById("box-name");
			var index = Math.floor(Math.random()*nameList.length);
			console.log(index);
			name.innerText = nameList[index];
		}
		
	</script>
</html>
```

### 9.3 全选和全不选

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>选中</title>
		
		<style type="text/css">
			#box{
				width: 500px;
				height: 200px;
				border: 1px solid red;
			}
		</style>
		
	</head>
	<body>
		<div id="box">
			
			<div id="box-select">
				<input type="radio" name="selectBook" id="selectAll" value="" />全选
				<input type="radio" name="selectBook" id="selectNone" value="" />全不选
			</div>
			
			<hr >
			
			<div id="box-option">
				<input type="checkbox" class="book" id="" value="" />三国演义
				<br>
				<input type="checkbox" class="book" id="" value="" />水浒传
				<br>
				<input type="checkbox" class="book" id="" value="" />西游记
				<br>
				<input type="checkbox" class="book" id="" value="" />红楼梦
				<br>
			</div>
		</div>
	</body>
	
	<script type="text/javascript">
		// 找到所有的元素
		var selectAll = document.getElementById("selectAll");
		var selectNone = document.getElementById("selectNone");
		var books = document.getElementsByClassName("book");
		
		// 添加监听
		selectAll.addEventListener("click",selectAllBooks);
		function selectAllBooks(){
			for (var i = 0; i < books.length; i++) {
				books[i].checked = "checked";
			}
		}
		
		selectNone.addEventListener("click",selectNoneBooks);
		function selectNoneBooks(){
			for (var i = 0; i < books.length; i++) {
				books[i].checked = "";
			}
		}
		
		/**
		 * 当四个小的选项选中之后，全选自动勾选
		 * 全选状态下，如果小的选项有任何未选择，全选取消
		 */ 
		
	</script>
	
</html>
```

