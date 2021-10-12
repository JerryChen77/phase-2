# Day27笔记

## 一、框架标签

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<!-- 
		框架标签
			一个浏览器窗口可以存在多个HTML文件
			frameset不能和body标签共存
			frameset标签可以嵌套
	 -->
	<frameset cols="1,6">
		<frame src="frames/frame01.html" >
		<frameset rows="6,1">
			<frame src="frames/frame02.html" >
			<frame src="frames/frame03.html" >
		</frameset>
	</frameset>
</html>
```

## 二、音视频标签

### 2.1 视频标签

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>视频标签</title>
	</head>
	<body>
		<!-- 
			视频标签
			video
				src
					资源路径
				width
					播放器宽度
				height
					播放器高度
				controls
					控制按钮
				autoplay
					自动播放
		 -->
		<video width="800" height="" src="video/bigmovie.mp4" controls="controls" autoplay="autoplay" loop="loop">
			
		</video>
	</body>
</html>
```

### 2.2 音频标签

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>音频标签</title>
	</head>
	<body>
		<!-- 
			音频标签
			audio
				src
					资源路径
				controls
					控制界面
				autoplay
					自动播放
		 -->
		<audio src="audio/最炫民族风.mp3" controls="controls">
			当前浏览器不支持audio
		</audio>
	</body>
</html>
```

## 三、CSS概述

### 3.1 概述

* 层叠样式表
* Cascading style sheets
* 给HTML标签添加样式效果
* 多出效果可以叠加

### 3.2 css组成

* 选择器
  * 找到具体的HTML标签
* 声明
  * 需要修饰的样式内容

* 格式
  * 选择器{声明1;声明2...}

## 四、基本选择器

### 4.1 元素选择器

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>元素选择器</title>
		<!-- 修饰HTML标签样式 -->
		<style type="text/css">
			/* 元素选择器 */
			h3{
				color: red;
				font-size: 32px;
			}
			
			p{
				font-size: 24px;
			}
			
		</style>
		
	</head>
	<body>
		<h3>静夜思</h3>
		<p>床前明月光，</p>
		<p>疑是地上霜。</p>
		<p>举头望明月，</p>
		<p>低头思故乡。</p>
	</body>
</html>
```

### 4.2 id选择器

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>id选择器</title>
		
		<style type="text/css">
			/* 
				id选择器
				给标签添加唯一标识
				通过#id属性找到
			 */
			#title01{
				color: red;
			}
			
			#con01{
				color: aqua;
			}
			
			#con02{
				color: blue;
			}
			
			#con03{
				color: yellow;
			}
			
			#con04{
				color: pink;
			}
		</style>
		
	</head>
	<body>
		<h3 id="title01">咏鹅</h3>
		<p id="con01">鹅鹅鹅，</p>
		<p id="con02">曲项向天歌，</p>
		<p id="con03">白毛浮绿水，</p>
		<p id="con04">红掌拨清波。</p>
	</body>
</html>
```

### 4.3 class选择器

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>class选择器</title>
		
		<style type="text/css">
			/* 
				class选择器
					把同类的内容标记为相同的class属性
					可以通过.class属性找到
			
					适合同类、相似的属性修饰
					一个标签可以设置多个class属性
			 */
			.con{
				font-size: 24px;
			}
			
			.con-ji{
				background-color: red;
			}
			
			.con-ou{
				background-color: #00FFFF;
			}
		</style>
		
	</head>
	<body>
		<h3 id="title02" class="title">望庐山瀑布</h3>
		<p id="con01" class="con con-ji">日照香炉生紫烟，</p>
		<p id="con02" class="con con-ou">遥看瀑布挂前川。</p>
		<p id="con03" class="con con-ji">飞流直下三千尺，</p>
		<p id="con04" class="con con-ou">疑是银河落九天。</p>
	</body>
</html>
```

### 4.4 基本选择器的优先级

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>基本选择器优先级</title>
		
		<style type="text/css">
			/* 
				基本选择器优先级
					id > class > 元素
			 */
			p{
				color: #0000FF;
			}
			
			.con{
				color: red;
			}
			
			#con01{
				color: #FFFF00;
			}
		</style>
		
	</head>
	<body>
		<h3 id="title03" class="title">悯农</h3>
		<p id="con01" class="con">锄禾日当午，</p>
		<p id="con02" class="con">汗滴禾下土。</p>
		<p id="con03" class="con">谁知盘中餐，</p>
		<p id="con04" class="con">粒粒皆辛苦。</p>
	</body>
</html>
```

## 五、CSS引入方式

### 5.1 内嵌样式

* 只对单个HTML标签生效
* 适合做个性化的设置

### 5.2 内部样式

* 对整个html文件生效
* 适合对整个页面进行风格设置

### 5.3 外部样式

* 整个项目中的html文件都可以导入
* 对整个项目生效
* 适合最适用性最广的设置

### 5.4 @import方式

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>css引入方式</title>
		<!-- 
			外部样式
				通过link标签引入
				可以引入本项目的css文件
				也可以引入网络中的才css文件
		 -->
		<link rel="stylesheet" type="text/css" href="css/main.css"/>
		<link rel="stylesheet" type="text/css" href="css/haha.css"/>
		<!-- 
			内部样式
				书写在html文件内部，是HTML文件的一部分
		 -->
		<style type="text/css">
			
			@import url("css/main.css");
			
			#con01{
				color: blue;
			}
		</style>
		
		<style type="text/css">
			#con03{
				color: pink;
			}
		</style>
		
	</head>
	<body>
		<!-- 
			内嵌样式
				书写在标签内部
		 -->
		<h3 style="color: red;border: 1px solid black">登高</h3>
		<p id="con01" class="con">风急天高猿啸哀，渚清沙白鸟飞回。</p>
		<p id="con02" class="con">无边落木萧萧下，无尽长江滚滚来。</p>
		<p id="con03" class="con">万里悲秋常作客，百年多病独登台。</p>
		<p id="con04" class="con">艰难苦恨繁霜鬓，潦倒新停浊酒杯。</p>
	</body>
</html>
```

### 5.5 引入方式的优先级

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>引入方式优先级</title>
		<!-- 
			外部样式
			内部样式
			内嵌样式
			
			就近原则，哪个离得近就生效
		-->
		<style type="text/css">
			#title04{
				color: blue;
			}
		</style>
		
		<link rel="stylesheet" type="text/css" href="css/main.css"/>
		
	</head>
	<body>
		<!-- 
			前不见古人,后不见来者。念天地之悠悠,独怆然而涕下。
		 -->
		 
		<h3 id="title04" class="title" style="color: #FFFF00;">登幽州台歌</h3>
		<p>前不见古人,</p>
		<p>后不见来者。</p>
		<p>念天地之悠悠,</p>
		<p>独怆然而涕下。</p>
		
	</body>
</html>
```

## 六、元素类型

### 6.1 块级元素

### 6.2 行内块元素

### 6.3 行内元素

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>元素的类型</title>
		<style type="text/css">
			div{
				border: 1px solid red;
				height: 60px;
			}
			
			img{
				height: 150px;
			}
			
			span{
				border: 1px solid red;
				height: 60px;
			}
		</style>
	</head>
	<body>
		<!-- 
			独占一行，能设置宽度和高度的
			不独占一行，能设置宽度和高度的
			不独占一行，不能设置宽度和高度的
		 -->
		 
		 <div id="box01">
		 	div01
		 </div>
		 
		 <div id="box02">
		 	div02
		 </div>
		 <div id="box03">
		 	div03
		 </div>
		 
		 <img src="img/pic00.jpg" >
		 <img src="img/pic01.jpg" >
		 
		 <br>
		 <span>
			 span01
		 </span>
		 
		 <span id="">
		 	span02
		 </span>
		 
	</body>
</html>
```

## 七、属性选择器

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>属性选择器</title>
		<style type="text/css">
			input{
				border: 2px solid red;
			}
			
			input[type='text']{
				background-color: #00FFFF;
			}
			
			input[type="password"]{
				background-color: yellow;
			}
			
		</style>
	</head>
	<body>
		<form method="get">
			昵称:
			<input type="text" placeholder="请输入用户名..."/>
			<br>
			
			密码:
			<input type="password" placeholder="请输入密码..."/>
			<br>
			
			<input type="submit" value="提交"/>
		</form>
	</body>
</html>
```

## 八、伪元素选择器

* 根据标签的状态显示对应的效果

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>伪元素选择器</title>
		<style type="text/css">
			a:link{
				color: #FF0000;
			}
			
			a:hover{
				font-size: 24px;
			}
			
			a:active{
				font-size: 24px;
				border: 1px solid red;
			}
			
			a:visited{
				color: yellow;
			}
			
			img:hover{
				width: 550px;
			}
			
		</style>
	</head>
	<body>
		<a href="https://www.runoob.com/">菜鸟教程</a>
		<img src="img/pic00.jpg" >
	</body>
</html>
```

## 九、层级选择器

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>层级选择器</title>
		<style type="text/css">
			#xiyou dd{
				color: yellow;
			}
			
			#liaozhai dd{
				color: red;
			}
		</style>
	</head>
	<body>
		<dl id="xiyou">
			<dt>西游记</dt>
			<dd>蜘蛛精</dd>
			<dd>白骨精</dd>
			<dd>孙悟空</dd>
			<dd>兔子精</dd>
		</dl>
		
		<dl id="liaozhai">
			<dt>聊斋志异</dt>
			<dd>聂小倩</dd>
			<dd>宁采臣</dd>
			<dd>燕赤霞</dd>
			<dd>黑山老妖</dd>
		</dl>
		
	</body>
</html>
```

## 十、组合选择器

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>组合选择器</title>
		
		<style type="text/css">
			/* 
				组合选择器
					多个、多种元素同时选中修饰样式
			 */
			#con01,#con03{
				color: blue;
			}
			
			h3,li{
				color: red;
			}
			
			h3,#con04,.man{
				background-color: #00FFFF;
			}
			
		</style>
		
	</head>
	<body>
		<h3 id="title05">春晓</h3>
		<p id="con01">春眠不觉晓，</p>
		<p id="con02">处处闻啼鸟。</p>
		<p id="con03">夜来风雨声，</p>
		<p id="con04">花落知多少。</p>
		
		<h3>三国演义</h3>
		<ul>
			<li class="man">曹操</li>
			<li class="man">刘备</li>
			<li class="man">孙权</li>
			<li class="man">刘协</li>
		</ul>
	</body>
</html>
```

## 十一、文字相关属性

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>文字相关样式</title>
		
		<style type="text/css">
			#con00{
				font-size: 32px;
				font-family: "楷体";
				font-style: oblique;
				font-weight: bold;
				/* 
					R
						Red
					G
						Green
					B
						Blue
				 */
				color: rgb(255,0,0);
				text-decoration: overline;
				/* 修饰内容摆放的方式 */
				text-align: center;
				text-shadow: 10px 10px 10px red;
			}
			
			p{
				text-indent: 32px;
				/* 
					单词间距
						两个文字中间有空格就是多个单词
				 */
				word-spacing: 32px;
				/* 每个文字的间距 */
				/* letter-spacing: 16px; */
				
			}
		</style>
		
	</head>
	<body>
		<!-- 
			在我的后园，可以看见墙外有两株树，一株是枣树，还有一株也是枣树。
			
			这上面的夜的天空，奇怪而高，我生平没有见过这样奇怪而高的天空。他仿佛要离开人间而去，使人们仰面不再看见。然而现在却非常之蓝，闪闪地〖目夹〗着几十个星星的眼，冷眼。他的口角上现出微笑，似乎自以为大有深意，而将繁霜洒在我的园里的野花上。
			
			我不知道那些花草真叫什么名字，人们叫他们什么名字。我记得有一种开过极细小的粉红花，现在还开着，但是更极细小了，她在冷的夜气中，瑟缩地做梦，梦见春的到来，梦见秋的到来，梦见瘦的诗人将眼泪擦在她最末的花瓣上，告诉她秋虽然来，冬虽然来，而此后接着还是春，胡蝶乱飞，蜜蜂都唱起春词来了。她于是一笑，虽然颜色冻得红惨惨地，仍然瑟缩着。
			
			枣树，他们简直落尽了叶子。先前，还有一两个孩子来打他们别人打剩的枣子，现在是一个也不剩了，连叶子也落尽了。他知道小粉红花的梦，秋后要有春；他也知道落叶的梦，春后还是秋。他简直落尽叶子，单剩干子，然而脱了当初满树是果实和叶子时候的弧形，欠伸得很舒服。但是，有几枝还低亚着，护定他从打枣的竿梢所得的皮伤，而最直最长的几枝，却已默默地铁似的直刺着奇怪而高的天空，使天空闪闪地鬼〖目夹〗眼；直刺着天空中圆满的月亮，使月亮窘得发白。
		 -->
		 
		 <p id="con00">
			 <<秋夜>>
		 </p>
		 
		 <p id="con01">
			 在我的后园，可以看见墙外有两株树，一株是枣树，还有一株也是枣树。
		 </p>
		 
		 <p id="con02">
			这上面的夜的天空，奇怪而高，我生平没有见过这样奇怪而高的天空。 他仿佛要离开人间而去，使人们仰面不再看见。
			 然而现在却非常之蓝，闪闪地〖目夹〗着几十个星星的眼，冷眼。
			 他的口角上现出微笑，似乎自以为大有深意，而将繁霜洒在我的园里的野花上。
		 </p>
		 
		 <p id="con03">
			 我不知道那些花草真叫什么名字，人们叫他们什么名字。
			 我记得有一种开过极细小的粉红花，现在还开着，但是更极细小了，她在冷的夜气中，
			 瑟缩地做梦，梦见春的到来，梦见秋的到来，梦见瘦的诗人将眼泪擦在她最末的花瓣上，
			 告诉她秋虽然来，冬虽然来，而此后接着还是春，胡蝶乱飞，蜜蜂都唱起春词来了。
			 她于是一笑，虽然颜色冻得红惨惨地，仍然瑟缩着。
		 </p>
		 
		 <p id="con04">
			 枣树，他们简直落尽了叶子。
			 先前，还有一两个孩子来打他们别人打剩的枣子，现在是一个也不剩了，连叶子也落尽了。
			 他知道小粉红花的梦，秋后要有春；他也知道落叶的梦，春后还是秋。他简直落尽叶子，
			 单剩干子，然而脱了当初满树是果实和叶子时候的弧形，欠伸得很舒服。
			 但是，有几枝还低亚着，护定他从打枣的竿梢所得的皮伤，而最直最长的几枝，
			 却已默默地铁似的直刺着奇怪而高的天空，使天空闪闪地鬼〖目夹〗眼；
			 直刺着天空中圆满的月亮，使月亮窘得发白。
		 </p>
		 
	</body>
</html>
```

## 十二、背景属性

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>背景属性</title>
		<style type="text/css">
			#box01{
				width: 800px;
				height: 800px;
				border: 1px solid red;
				background-image: url(img/pic00.jpg);
				background-repeat: no-repeat;
				background-position: bottom right;
				background-size: 10% 10%;
			}
		</style>
	</head>
	<body>
		
		<div id="box01">
			div01
		</div>
		
	</body>
</html>
```

## 十三、列表属性

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>列表属性</title>
		
		<style type="text/css">
			li{
				/* border: 1px solid red; */
				/* list-style-type: disc; */
				list-style-position: inside;
				list-style-image: url(img/pic01.jpg);
			}
		</style>
		
	</head>
	<body>
		<ul>
			<li>人潮汹涌</li>
			<li>唐人街探案</li>
			<li>你好李焕英</li>
			<li>熊出没</li>
		</ul>
	</body>
</html>
```

## 十四、宽度和高度

* 可以使用具体的数值赋值
* 可以使用百分比赋值

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>尺寸属性</title>
		
		<style type="text/css">
			#box01{
				border: 1px solid red;
				width: 80%;
				height: 800px;
			}
			
			#box02{
				background-color: red;
				width: 80%;
				height: 80%;
			}
		</style>
		
	</head>
	<body>
		<div id="box01">
			<div id="box02">
				div02
			</div>
		</div>
	</body>
</html>
```

## 十五、显示属性

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>显示属性</title>
		
		<style type="text/css">
			/* 
			标签的显示类型
				块级元素
					独占一行
					能设置宽度和高度
					用作布局的规划
					div
					li
					td
					dd
					p
					
				行内块元素
					不独占一行
					可以设置宽度和高度
					用作内填充
					img
					input
					
				行内元素
					不独占一行
					不能设置宽度和高度
					内容填充
					a
					span
			 */
			div{
				width: 800px;
				height: 800px;
				background-color: #FF0000;
				display: inline;
			}
			
			span{
				width: 300px;
				height: 300px;
				background-color: blue;
				display: none;
			}
		</style>
		
	</head>
	<body>
		<div id="box01">
			div01
		</div>
		
		<div id="box02">
			div02
		</div>
		
		<br>
		
		<span>
			span01
		</span>
		
		<span>
			span02
		</span>
		
		<input type="text" name="" id="" value="" style="width: 1000px;"/>
		<a href="" style="border: 1px solid red;width: 500px;">aaa</a>
	</body>
</html>
```

