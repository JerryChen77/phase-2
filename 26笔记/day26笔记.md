# Day 26笔记

## 一、前端概述

### 1.1 学习前端的意义

### 1.2 网页的编写

* 文件--html文件
  * jsp/html/xhtml/php

### 1.3 HTML

* Hyper Text Markup Language
* 超文本
  * 表现能力超出文本
* 标记
  * 页面中内容都是各种各样的标记
* 语言
  * 计算机编程语言

### 1.4 开发工具

* Hbuilder
  * 国产
  * 免费
  * 功能强大
  * 绿色版
    * 无需安装，解压后可以直接运行
* WebStorm
  * 和IDEA一家
  * 收费

* Eclipse
* EditPlus
* 记事本

### 1.5 创建项目

* 见截图

### 1.6 HTML页面组成

* doctype
  * 文档类型
* html
  * 页面最大的标签
  * 根标签
* head
  * 设置
  * 配置
* body
  * 网页具体的内容

## 二、文字标记

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>
			我的第一个HTML程序
		</title>
	</head>
	<body>
		
		<!-- 
			残叶
			李觏〔宋代〕
			一树摧残几片存，栏边为汝最伤神。
			休翻雨滴寒鸣夜，曾抱花枝暖过春。
			与影有情唯日月，遇红无礼是泥尘。
			上阳宫女多诗思，莫寄人间取次人。
			
			b
				加黑、加粗
			strong
				加黑、加粗
				语气加强
			
			i
				倾斜
			em
				倾斜
				语气加强
			small
				字体变小
			big
				字体变大
			sub
				文字向下
			sup
				文字向上
			
		 -->
		 
		 <b><p style="font-size: 16px;color: red;">残叶</p></b>
		 李觏〔<strong>宋代</strong>〕
		 <br>
		 一树摧残<i>几片存</i>，栏边为汝<em>最伤神</em>。
		 <br>
		 <small>休翻雨滴</small>寒鸣夜，曾抱花枝<big>暖过春</big>。
		 <br>
		 与影有情唯日月，遇红无礼是泥尘。
		 <br>
		 上阳宫女多诗思，<del>莫寄人间取次人</del>。
		 <br>
		
		3^2=9
		
		<br>
		
		<sub>3</sub>
		<sup>2</sup>
		=9
		
	</body>
</html>
```

## 三、标题标记

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>标题标签</title>
	</head>
	<body>
		<!-- 
			标题标记
				hn
				n的范围是1--6
				逐渐减小
				如果n超出范围
					没有效果
					不会报错
				
				有默认样式，也可以通过代码再次设置
				h标记独占一行
		 -->
		<h1 style="color: red;">静夜思</h1>
		<h2 style="font-size: 64px;">静夜思</h2>
		<h3>静夜思</h3>
		<h4>静夜思</h4>
		<h5>静夜思</h5>
		<h6>静夜思</h6>
		<h7>静夜思</h7>
		<h8>静夜思</h8>
		<h9>静夜思</h9>
		静夜思
		静夜思
		静夜思
	</body>
</html>
```

## 四、段落标记

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>段落标签</title>
	</head>
	<body>
		<!-- 
			《秋夜》原文
			在我的后园，可以看见墙外有两株树，一株是枣树，还有一株也是枣树。
			
			这上面的夜的天空，奇怪而高，我生平没有见过这样奇怪而高的天空。
			他1仿佛要离开人间而去，使人们仰面不再看见。然而现在却非常之蓝，闪闪地䀹2着几十个星星的眼，冷眼。
			他的口角上现出微笑，似乎自以为大有深意，而将繁霜洒在我的园里的野花草上。
			
			我不知道那些花草真叫什么名字，人们叫他们什么名字。
			我记得有一种开过极细小的粉红花，现在还开着，但是更极细小了，她在冷的夜气中，瑟缩3地做梦，梦见春的到来，
			梦见秋的到来，梦见瘦的诗人将眼泪擦在她最末的花瓣上，告诉她秋虽然来，冬虽然来，而此后接着还是春，
			蝴蝶乱飞，蜜蜂都唱起春词来了。她于是一笑，虽然颜色冻得红惨惨地，仍然瑟缩着。
		 
			p
				段落标签
				每段独立存在
				可以设置宽度和高度
				可以设置其他样式
			
		 -->
		 
		 <h3>《秋夜》</h3>
		 
		 <h4>作者-鲁迅</h4>
		 
		 
		 <p style="width: 500px;text-align: center; border: 1px red solid;">
			在我的后园，可以看见墙外有两株树，一株是枣树，还有一株也是枣树。
		 </p>
		 
		 <p>
			这上面的夜的天空，奇怪而高，我生平没有见过这样奇怪而高的天空。
			他1仿佛要离开人间而去，使人们仰面不再看见。然而现在却非常之蓝，闪闪地䀹2着几十个星星的眼，冷眼。
			他的口角上现出微笑，似乎自以为大有深意，而将繁霜洒在我的园里的野花草上。
		 </p>
		 
		 <p>
			我不知道那些花草真叫什么名字，人们叫他们什么名字。
			我记得有一种开过极细小的粉红花，现在还开着，但是更极细小了，她在冷的夜气中，瑟缩3地做梦，梦见春的到来，
			梦见秋的到来，梦见瘦的诗人将眼泪擦在她最末的花瓣上，告诉她秋虽然来，冬虽然来，而此后接着还是春，
			蝴蝶乱飞，蜜蜂都唱起春词来了。她于是一笑，虽然颜色冻得红惨惨地，仍然瑟缩着。
		 </p>
		 
	</body>
</html>
```

## 五、字符实体

* 特殊字符
  * 键盘没有
  * 屏蔽了原本的含义
  * 使用符号+字母的方式展示

```java
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>特殊字符</title>
	</head>
	<body>
		<!--
			《秋夜》原文
			在我的后园，可以看见墙外有两株树，一株是枣树，还有一株也是枣树。
			
			这上面的夜的天空，奇怪而高，我生平没有见过这样奇怪而高的天空。
			他1仿佛要离开人间而去，使人们仰面不再看见。然而现在却非常之蓝，闪闪地䀹2着几十个星星的眼，冷眼。
			他的口角上现出微笑，似乎自以为大有深意，而将繁霜洒在我的园里的野花草上。
			
			我不知道那些花草真叫什么名字，人们叫他们什么名字。
			我记得有一种开过极细小的粉红花，现在还开着，但是更极细小了，她在冷的夜气中，瑟缩3地做梦，梦见春的到来，
			梦见秋的到来，梦见瘦的诗人将眼泪擦在她最末的花瓣上，告诉她秋虽然来，冬虽然来，而此后接着还是春，
			蝴蝶乱飞，蜜蜂都唱起春词来了。她于是一笑，虽然颜色冻得红惨惨地，仍然瑟缩着。
		 
			p
				段落标签
				每段独立存在
				可以设置宽度和高度
				可以设置其他样式
			
		 -->
		 
		 <h3>《秋夜》</h3>
		 
		 <h4>作者-鲁迅</h4>
		 
		 
		 <p>
			在我的后园，可以看见墙外有两株树，一株是枣树，还有一株也是枣树。
		 </p>
		 
		 <p>
			这上面的夜的天空，奇怪而高，我生平没有见过这样奇怪而高的天空。
			他1仿佛要离开人间而去，使人们仰面不再看见。然而现在却非常之蓝，闪闪地䀹2着几十个星星的眼，冷眼。
			他的口角上现出微笑，似乎自以为大有深意，而将繁霜洒在我的园里的野花草上。
		 </p>
		 
		 <p>
			&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;我不知道那些花草真叫什么名字，人们叫他们什么名字。
			我记得有一种开过极细小的粉红花，现在还开着，但是更极细小了，她在冷的夜气中，瑟缩3地做梦，梦见春的到来，
			梦见秋的到来，梦见瘦的诗人将眼泪擦在她最末的花瓣上，告诉她秋虽然来，冬虽然来，而此后接着还是春，
			蝴蝶乱飞，蜜蜂都唱起春词来了。她于是一笑，虽然颜色冻得红惨惨地，仍然瑟缩着。
		 </p>
		 <p>
			 3*2=6
		 </p>
		 <p>
			 3&times;2=6
		 </p>
		 <p>
			 6/3=2
		 </p>
		 <p>
			 6&divide;2=3
		 </p>
		 <p>
			 Copyright&copy;
		 </p>
		 <p>
			 &yen;
		 </p>
	</body>
</html>
```

## 六、列表标记

### 6.1 无序列表

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>列表标记</title>
	</head>
	<body>
		<!-- 
			无序列表
			ul
				子元素是li
				有圆点之类的标记
				可以通过type设置样式
		 -->
		<h3>吸毒监狱风云</h3>
		
		<ul type="disc">
			<li>柯震东</li>
			<li>张默</li>
			<li>房祖名</li>
			<li>陈羽凡</li>
			<li>尹相杰</li>
			<li>宋冬野</li>
		</ul>
		
		<h3>出轨风云榜</h3>
		<ul>
			<li>白百何</li>
			<li>李小璐</li>
			<li>皮几万</li>
			<li>陈思诚</li>
		</ul>
		
	</body>
</html>
```



### 6.2 有序列表

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>有序列表</title>
	</head>
	<body>
		<!-- 
			ol
				列表中的元素是li标记
				默认是数字序号
				可以通过type设置编号类型
				数字模式下可以设置start开始
		 -->
		
		<h3>四大名著</h3>
		<ol type="1" start="5">
			<li>西游记</li>
			<li>水浒传</li>
			<li>红楼梦</li>
			<li>三国演义</li>
		</ol>
		
		<h3>四大名著</h3>
		<ol type="1">
			<li>西游记</li>
			<li>水浒传</li>
			<li>红楼梦</li>
			<li>三国演义</li>
		</ol>
		
	</body>
</html>
```



### 6.3 自定义列表

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>

			
			<!-- 
			 		天龙八部
						乔峰
						段誉
						虚竹
					
					射雕英雄传
						郭靖
						黄蓉
						黄药师
						洪七公
						
				自定义列表
					dl--开始自定义列表
					dt--标题
					dd--列表内容
			 -->	
			<dl>
				<dt>天龙八部</dt>
				<dd>乔峰</dd>
				<dd>段誉</dd>
				<dd>虚竹</dd>
				<dd>王语嫣</dd>
				<dd>慕容复</dd>
			</dl>
			
			<dl>
				<dt>射雕英雄传</dt>
				<dd>郭靖</dd>
				<dd>黄蓉</dd>
				<dd>黄药师</dd>
				<dd>洪七公</dd>
			</dl>
			
	</body>
</html>
```

## 七、图片标签

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>图形标签</title>
	</head>
	<body>
		<!-- 
			图片标签
				img
					图片标签，多个图片可以在同一行存在，可以设置宽高属性
					src
						图片的资源位置
						采用相对路径书写
						网络图片资源
					width
						图片的宽度
					height
						图片的高度
						
						如果只设置了宽度和高度，另一个属性会等比例缩放
						如果同时设置了宽度和高度，两个属性同时生效。图片可能失真
					title
						光标悬浮显示的标题
					alt
						图片资源失效的时候显示的提示
		 -->
		<img src="img/pic00.jpg" height="500px" width="500px">
		<!-- <img src="D:\\files\\JavaFiles\\Java2103\\day26\\资料\\pic00.jpg" > -->
		<!-- <img src="https://song.gushiwen.org/mingjuImg/B38A17D34E9DADE168657985169F6443.jpg" > -->
		
		<img src="img/pic01.jpg" title="这是一个小姐姐的图片...">
		
		<img src="img/pic002.jpg" alt="这个也是一个小姐姐">
		
		<img src="./img/image/pic02.jpg" >
		
	</body>
</html>
```

## 八、超链接

### 8.1 基本使用

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>超链接标签</title>
	</head>
	<body>
		<!--
			超链接
			a
				href
					超链接指向的资源
					可以是本地资源
					可以是网络资源,需要添加协议
				title
					光标悬浮显示的提示
				target
					链接资源打开的方式
					_blank
						创建新的窗口
					_self
						覆盖自己
		 -->
		 
		 <a href="1、标题标签.html">
			 标题标签
		 </a>
		 
		 <a href="https://so.gushiwen.cn/shiwenv_a3ab29335412.aspx">
			 古诗文
		 </a>
		 
		 <a href="http://www.baidu.com" title="百度的链接" target="_self">
			 百度一下你就知道
		 </a>
		 
	</body>
</html>
```



### 8.2 图片超链接和锚点

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>图片链接</title>
	</head>
	<body>
		<!-- 
			图片和链接组合使用
			a标记中的内容是img标记
			
			锚点
			
		 -->
		<a href="https://image.baidu.com/search/detail?ct=503316480&z=0&ipn=false&word=%E7%BE%8E%E5%A5%B3&step_word=&hs=2&pn=20&spn=0&di=62370&pi=0&rn=1&tn=baiduimagedetail&is=0%2C0&istype=0&ie=utf-8&oe=utf-8&in=&cl=2&lm=-1&st=undefined&cs=2655281937%2C358661376&os=2115739832%2C1600540165&simid=3527826116%2C718990185&adpicid=0&lpn=0&ln=2392&fr=&fmq=1621838949680_R&fm=&ic=undefined&s=undefined&hd=undefined&latest=undefined&copyright=undefined&se=&sme=&tab=0&width=undefined&height=undefined&face=undefined&ist=&jit=&cg=girl&bdtype=0&oriquery=&objurl=https%3A%2F%2Fgimg2.baidu.com%2Fimage_search%2Fsrc%3Dhttp%3A%2F%2Fbenyouhuifile.it168.com%2Fforum%2F201201%2F09%2F204425wkhzcdrods6bcsr9.jpg%26refer%3Dhttp%3A%2F%2Fbenyouhuifile.it168.com%26app%3D2002%26size%3Df9999%2C10000%26q%3Da80%26n%3D0%26g%3D0n%26fmt%3Djpeg%3Fsec%3D1624430988%26t%3Da1d689836bfa9f399f0161852aeda4af&fromurl=ippr_z2C%24qAzdH3FAzdH3Ft1jwrw1_z%26e3Btp8mb_z%26e3Bv54AzdH3Fpi6jw1-8la0ac9-8-8_z%26e3Bip4s&gsm=18&rpstart=0&rpnum=0&islist=&querylist=&force=undefined">
			<img src="img/pic00.jpg" >
		</a>
		
		<dl>
			<dt>天龙八部</dt>
			<dd>乔峰</dd>
			<dd>段誉</dd>
			<dd>虚竹</dd>
			<dd>王语嫣</dd>
			<dd>慕容复</dd>
		</dl>
		
		<dl>
			<dt>射雕英雄传</dt>
			<dd>郭靖</dd>
			<dd>黄蓉</dd>
			<dd>黄药师</dd>
			<dd>洪七公</dd>
		</dl>
		
		<dl>
			<dt>天龙八部</dt>
			<dd>乔峰</dd>
			<dd>段誉</dd>
			<dd>虚竹</dd>
			<dd>王语嫣</dd>
			<dd>慕容复</dd>
		</dl>
		
		<dl>
			<dt>射雕英雄传</dt>
			<dd>郭靖</dd>
			<dd>黄蓉</dd>
			<dd>黄药师</dd>
			<dd>洪七公</dd>
		</dl>
		
		<dl>
			<dt>天龙八部</dt>
			<dd>乔峰</dd>
			<dd>段誉</dd>
			<dd>虚竹</dd>
			<dd>王语嫣</dd>
			<dd>慕容复</dd>
		</dl>
		
		<dl>
			<dt>射雕英雄传</dt>
			<dd>郭靖</dd>
			<dd>黄蓉</dd>
			<dd>黄药师</dd>
			<dd>洪七公</dd>
		</dl>
		
		<dl>
			<dt>天龙八部</dt>
			<dd>乔峰</dd>
			<dd>段誉</dd>
			<dd>虚竹</dd>
			<dd>王语嫣</dd>
			<dd>慕容复</dd>
		</dl>
		
		<dl>
			<dt>射雕英雄传</dt>
			<dd>郭靖</dd>
			<dd>黄蓉</dd>
			<dd>黄药师</dd>
			<dd>洪七公</dd>
		</dl>
		<a name="middle"></a>
		<hr >
		<dl>
			<dt>天龙八部</dt>
			<dd>乔峰</dd>
			<dd>段誉</dd>
			<dd>虚竹</dd>
			<dd>王语嫣</dd>
			<dd>慕容复</dd>
		</dl>
		
		<dl>
			<dt>射雕英雄传</dt>
			<dd>郭靖</dd>
			<dd>黄蓉</dd>
			<dd>黄药师</dd>
			<dd>洪七公</dd>
		</dl>
		
		<dl>
			<dt>天龙八部</dt>
			<dd>乔峰</dd>
			<dd>段誉</dd>
			<dd>虚竹</dd>
			<dd>王语嫣</dd>
			<dd>慕容复</dd>
		</dl>
		
		<dl>
			<dt>射雕英雄传</dt>
			<dd>郭靖</dd>
			<dd>黄蓉</dd>
			<dd>黄药师</dd>
			<dd>洪七公</dd>
		</dl>
		
		<dl>
			<dt>天龙八部</dt>
			<dd>乔峰</dd>
			<dd>段誉</dd>
			<dd>虚竹</dd>
			<dd>王语嫣</dd>
			<dd>慕容复</dd>
		</dl>
		
		<dl>
			<dt>射雕英雄传</dt>
			<dd>郭靖</dd>
			<dd>黄蓉</dd>
			<dd>黄药师</dd>
			<dd>洪七公</dd>
		</dl>
		
		<dl>
			<dt>天龙八部</dt>
			<dd>乔峰</dd>
			<dd>段誉</dd>
			<dd>虚竹</dd>
			<dd>王语嫣</dd>
			<dd>慕容复</dd>
		</dl>
		
		<dl>
			<dt>射雕英雄传</dt>
			<dd>郭靖</dd>
			<dd>黄蓉</dd>
			<dd>黄药师</dd>
			<dd>洪七公</dd>
		</dl>
		
		<dl>
			<dt>天龙八部</dt>
			<dd>乔峰</dd>
			<dd>段誉</dd>
			<dd>虚竹</dd>
			<dd>王语嫣</dd>
			<dd>慕容复</dd>
		</dl>
		
		<dl>
			<dt>射雕英雄传</dt>
			<dd>郭靖</dd>
			<dd>黄蓉</dd>
			<dd>黄药师</dd>
			<dd>洪七公</dd>
		</dl>
		
		<dl>
			<dt>天龙八部</dt>
			<dd>乔峰</dd>
			<dd>段誉</dd>
			<dd>虚竹</dd>
			<dd>王语嫣</dd>
			<dd>慕容复</dd>
		</dl>
		
		<dl>
			<dt>射雕英雄传</dt>
			<dd>郭靖</dd>
			<dd>黄蓉</dd>
			<dd>黄药师</dd>
			<dd>洪七公</dd>
		</dl>
		
		<dl>
			<dt>天龙八部</dt>
			<dd>乔峰</dd>
			<dd>段誉</dd>
			<dd>虚竹</dd>
			<dd>王语嫣</dd>
			<dd>慕容复</dd>
		</dl>
		
		<dl>
			<dt>射雕英雄传</dt>
			<dd>郭靖</dd>
			<dd>黄蓉</dd>
			<dd>黄药师</dd>
			<dd>洪七公</dd>
		</dl>
		
		<dl>
			<dt>天龙八部</dt>
			<dd>乔峰</dd>
			<dd>段誉</dd>
			<dd>虚竹</dd>
			<dd>王语嫣</dd>
			<dd>慕容复</dd>
		</dl>
		
		<dl>
			<dt>射雕英雄传</dt>
			<dd>郭靖</dd>
			<dd>黄蓉</dd>
			<dd>黄药师</dd>
			<dd>洪七公</dd>
		</dl>
		
		
		
		<dl>
			<dt>天龙八部</dt>
			<dd>乔峰</dd>
			<dd>段誉</dd>
			<dd>虚竹</dd>
			<dd>王语嫣</dd>
			<dd>慕容复</dd>
		</dl>
		
		<dl>
			<dt>射雕英雄传</dt>
			<dd>郭靖</dd>
			<dd>黄蓉</dd>
			<dd>黄药师</dd>
			<dd>洪七公</dd>
		</dl>
		
		<a href="#">顶部</a>
		<a href="#middle">中间</a>
	</body>
</html>
```

## 九、表格标签

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>表格标签</title>
	</head>
	<body>
		
		<!-- 
			表格标签
			table
				tr
					一行
				th
					一列标题
				td
					一列内容
				width
					表格宽度
				height
					表格高度
				align
					摆放方式
				cellspacing
					内部小表格的间距
				cellpadding
					内容和小表格的间距
				rowspan
					设置占据行数
				colspan
					设置占据列数
		 -->
		
		<table border="10px"  align="center" width="1000px" height="500px"style="text-align: center;font-size: 1.5rem;background-image: url(img/image/pic02.jpg); background-size: 100% 100%;">
			<tr">
				<th>
					姓名
				</th>
				<th>
					门派
				</th>
				<th>
					绝招
				</th>
				<th>
					备注
				</th>
			</tr>
			
			<tr>
				<td>乔峰</td>
				<td>丐帮</td>
				<td>降龙十巴掌</td>
				<td>后来发现是契丹人</td>
			</tr>
			
			<tr>
				<td>段誉</td>
				<td rowspan="3">大理皇家</td>
				<td>六脉神剑</td>
				<td>他有很多好妹妹</td>
			</tr>
			
			<tr>
				<td>段正淳</td>
				<!-- <td>大理皇家</td> -->
				<td>一阳指</td>
				<td>居中最大的种马</td>
			</tr>
			
			<tr>
				<td>段延庆</td>
				<!-- <td>大理皇家</td> -->
				<td>一阳指</td>
				<td>后来发现是段誉亲爹</td>
			</tr>
			
			<tr>
				<td>扫地僧</td>
				<td>少林</td>
				<td colspan="2">不详</td>
				<!-- <td>不详</td> -->
			</tr>
		</table>
	</body>
</html>
```

## 十、表单

* 收集数据，提交到指定位置

### 10.1 基本使用

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>表单</title>
	</head>
	<body>
		<!-- 
			表单
			收集用户数据提交到执行的地址
			form
				action
					数据提交的地址
				method
					数据提交的方式
			input
		 -->
		<form method="get">
			昵称:
			<input type="text" name="nickname" id="nickname" value="" placeholder="请输入昵称..."/>
			<br>
			
			密码:
			<input type="password" name="password" id="password" placeholder="请输入密码..."/>
			<br>
			
			重复密码:
			<input type="password" name="rePassword" id="rePassword" placeholder="请重复密码..."/>
			<br>
			
			性别:
			<input type="radio" name="gender" id="male" value="male" />男
			<input type="radio" name="gender" id="female" value="female" />女
			<br>
			
			兴趣:
			<input type="checkbox" name="hobby" id="sport" value="sport" />运动
			<input type="checkbox" name="hobby" id="travel" value="travel" />旅游
			<input type="checkbox" name="hobby" id="eat" value="eat" />吃
			<br>
			
			生日:
			<select name="year">
				<option value="1990">1990</option>
				<option value="1991">1991</option>
				<option value="1992">1992</option>
				<option value="1993">1993</option>
				<option value="1994">1994</option>
				<option value="1995">1995</option>
				<option value="1996">1996</option>
				<option value="1997">1997</option>
				<option value="1998">1998</option>
				<option value="1999">1999</option>
				<option value="2000">2000</option>
			</select>年
			
			<select name="month">
				<option value="1">1</option>
				<option value="2">2</option>
				<option value="3">3</option>
				<option value="4">4</option>
				<option value="5">5</option>
				<option value="6">6</option>
				<option value="7">7</option>
				<option value="8">8</option>
				<option value="9">9</option>
				<option value="10">10</option>
				<option value="11">11</option>
				<option value="12">12</option>
			</select>月
			
			<select name="day">
				<option value="1">1</option>
				<option value="2">2</option>
				<option value="3">3</option>
				<option value="4">4</option>
				<option value="5">5</option>
				<option value="6">6</option>
				<option value="7">7</option>
				<option value="8">8</option>
				<option value="9">9</option>
				<option value="10">10</option>
				<option value="11">11</option>
				<option value="12">12</option>
			</select>日	
			<br>
			
			头像:
			<input type="file" name="headshow" id="headshow" value="" />
			<br>
			
			自我介绍:
			<br>
			<textarea rows="15" cols="40">
				
			</textarea>
					
			<br>
			<!-- 提交数据的类型 -->
			<input type="submit" value="注册"/>
		</form>
	</body>
</html>
```



### 10.2 表单和表格

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>表格和表单</title>
	</head>
	<body>
		
			<form method="get">
				<table cellspacing="" cellpadding="" align="center" >
				<tr>
					<td>
						昵称:
					</td>
					<td>
						<input type="text" name="nickname" id="nickname" value="" placeholder="请输入昵称..."/>
					</td>
				</tr>
				<tr>
					<td>
						密码
					</td>
					<td>
						<input type="password" name="password" id="password" placeholder="请输入密码..."/>
					</td>
				</tr>
				
				<tr>
					<td>
						重复密码
					</td>
						
					<td>
						<input type="password" name="rePassword" id="rePassword" placeholder="请重复密码..."/>
					</td>
				</tr>
				
				<tr>
					<td>
						性别
					</td>
						
					<td>
						<input type="radio" name="gender" id="male" value="male" />男
						<input type="radio" name="gender" id="female" value="female" />女
					</td>
				</tr>
				
				<tr>
					<td>
						兴趣
					</td>
						
					<td>
						<input type="checkbox" name="hobby" id="sport" value="sport" />运动
						<input type="checkbox" name="hobby" id="travel" value="travel" />旅游
						<input type="checkbox" name="hobby" id="eat" value="eat" />吃
					</td>
				</tr>
				
				<tr>
					<td>
						生日
					</td>
						
					<td>
						<select name="year">
							<option value="1990">1990</option>
							<option value="1991">1991</option>
							<option value="1992">1992</option>
							<option value="1993">1993</option>
							<option value="1994">1994</option>
							<option value="1995">1995</option>
							<option value="1996">1996</option>
							<option value="1997">1997</option>
							<option value="1998">1998</option>
							<option value="1999">1999</option>
							<option value="2000">2000</option>
						</select>年
						
						<select name="month">
							<option value="1">1</option>
							<option value="2">2</option>
							<option value="3">3</option>
							<option value="4">4</option>
							<option value="5">5</option>
							<option value="6">6</option>
							<option value="7">7</option>
							<option value="8">8</option>
							<option value="9">9</option>
							<option value="10">10</option>
							<option value="11">11</option>
							<option value="12">12</option>
						</select>月
						
						<select name="day">
							<option value="1">1</option>
							<option value="2">2</option>
							<option value="3">3</option>
							<option value="4">4</option>
							<option value="5">5</option>
							<option value="6">6</option>
							<option value="7">7</option>
							<option value="8">8</option>
							<option value="9">9</option>
							<option value="10">10</option>
							<option value="11">11</option>
							<option value="12">12</option>
						</select>日	
					</td>
				</tr>
				
				<tr>
					<td>
						<input type="submit" value="注册"/>
					</td>
				</tr>
				
				</table>
			</form>
	</body>
</html>
```

