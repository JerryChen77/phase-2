# Day32笔记

## 一、了解JQuery

### 1.1 概述

* jQuery 是一个 JavaScript 库。
* jQuery 极大地简化了 JavaScript 编程。
* jQuery 很容易学习。

### 1.2 jquery特点

```
Query 是一个 JavaScript 函数库。

jQuery 是一个轻量级的"写的少，做的多"的 JavaScript 库。

jQuery 库包含以下功能：

HTML 元素选取
HTML 元素操作
CSS 操作
HTML 事件函数
JavaScript 特效和动画
HTML DOM 遍历和修改
AJAX
Utilities
提示： 除此之外，jQuery 还提供了大量的插件。
```

### 1.3 为什么使用 jQuery 

* 目前网络上有大量开源的 JS 框架, 但是 jQuery 是目前最流行的 JS 框架，而且提供了大量的扩展。

* 很多大公司都在使用 jQuery， 例如:
  * Google
  * Microsoft
  * IBM
  * Netflix

### 1.4 安装JQ

* 在线版
  * 使用CDN，远程获取服务器中的jq框架
  * CDNjs
    * https://cdnjs.cloudflare.com/ajax/libs/jquery/3.6.0/jquery.min.js
  * JSDEliver
    * https://cdn.jsdelivr.net/npm/jquery@3.6.0/dist/jquery.min.js
  * 微软
    * https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.6.0.min.js
* 离线版
  * 把JQ下载到本地，放入项目中使用

## 二、JQ页面加载事件

### 2.1 原生js加载

### 2.2 jq加载

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<script src="js/jquery-3.6.0.min.js" type="text/javascript" charset="utf-8"></script>
		<title>第一个JQ案例</title>
		
		<script type="text/javascript">
			/* window.onload = function(){
				
			} */
			
			$(function(){
				console.log(document.getElementById("btn"));
			})
			
			$(function(){
				console.log(document.getElementById("btn00"));
			})
			
		</script>
		
	</head>
	<body>
		<button type="button" id="btn">点我</button>
		
		<button type="button" id="btn00">点我</button>
	</body>
</html>
```

## 三、jq选择器

### 3.1 基本选择器

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<script src="js/jquery-3.6.0.min.js" type="text/javascript" charset="utf-8"></script>
		<title>基本选择器</title>
	</head>
	<body>
		<h3 id="title01">静夜思</h3>
		<p id="con01" class="con-ji">床前明月光</p>
		<p id="con02" class="con-ou">疑是地上霜</p>
		<p id="con03" class="con-ji">举头望明月</p>
		<p id="con04" class="con-ou">低头思故乡</p>
		
		<button type="button" onclick="func01()">获取标题</button>
		<button type="button" onclick="func02()">获取所有p</button>
		<button type="button" onclick="func03()">获取奇数p</button>
		<button type="button" onclick="func04()">隐藏标题</button>
		<button type="button" onclick="func05()">显示标题</button>
	</body>
	
	<script type="text/javascript">
		
		function func01(){
			/* var title = document.getElementById("title01");
			console.log(title); */
			var $title01 = $("#title01");
			console.log($title01);
		}
		
		function func02(){
			var $ps = $("p");
			console.log($ps);
			for (var i = 0; i < $ps.length; i++) {
				console.log($ps[i]);
			}
		}
		
		function func03(){
			var $ji = $(".con-ji");
			console.log($ji);	
		}
		
		function func04(){
			$("#title01").hide();
		}
		
		function func05(){
			$("#title01").show();
		}
	</script>
	
</html>
```

### 3.2 属性和通选

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>属性选择器</title>
		<script src="js/jquery-3.6.0.min.js" type="text/javascript" charset="utf-8"></script>
	</head>
	<body>
		<h3 id="title02">
			<a href="" target="_self">
				古朗月行
			</a>
		</h3>
		<h4>
			<a href="https://baike.baidu.com/item/%E6%9D%8E%E7%99%BD/1043?fr=aladdin" title="唐代诗人李白" target="_blank">
				唐*李白
			</a>
		</h4>
		<p id="con01">小时不识月</p>
		<p class="con-ou">呼作白玉盘</p>
		<p title="李白的一首诗词">又疑瑶台镜</p>
		<p class="con-ou">飞在青云端</p>
		
		<button type="button" onclick="func01()">获取所有标签</button>
		<button type="button" onclick="func02()">href属性获取标签</button>
		<button type="button" onclick="func03()">title属性获取标签</button>
		<button type="button" onclick="func04()">target属性为_self标签</button>
		<button type="button" onclick="func05()">title属性p标签</button>
	</body>
	
	<script type="text/javascript">
		
		// 通选
		function func01(){
			var $tags = $("body *");
			console.log($tags);
			for (var i = 0; i < $tags.length; i++) {
				console.log($tags[i]);
			}
		}
		
		function func02(){
			var $hrefs = $("[href]");
			console.log($hrefs);
		}
		
		function func03(){
			var $titles = $("[title]");
			console.log($titles);
		}
		
		function func05(){
			var $ps = $("p[title]");
			console.log($ps);
		}
		
		function func04(){
			var $selfs = $("[target='_self']");
			console.log($selfs);
		}
		
	</script>
	
</html>
```

### 3.3 层级和奇数偶数选择器

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>层级选择器</title>
		<script src="js/jquery-3.6.0.min.js" type="text/javascript" charset="utf-8"></script>
	</head>
	<body>
		<ul id="mingzhu">
			<li>西游记</li>
			<li>水浒传</li>
			<li>红楼梦</li>
			<li>三国演义</li>
		</ul>
		
		<ul id="sida">
			<li>魔礼青</li>
			<li>魔礼红</li>
			<li>魔礼寿</li>
			<li>魔礼海</li>
		</ul>
		<button type="button" onclick="func01()">获取所有的li标记</button>
		<button type="button" onclick="func02()">获取名著所有的li标记</button>
		<button type="button" onclick="func03()">获取所有奇数位的li标记</button>
		<button type="button" onclick="func04()">获取第一个li标记</button>
		<button type="button" onclick="func05()">获取最后一个li标记</button>
		<button type="button" onclick="func06()">获取每一个ul中的第一个li标记</button>
		<button type="button" onclick="func07()">获取每一个ul中的最后一个li标记</button>
		
	</body>
	
	<script type="text/javascript">
		function func01(){
			console.log($("li"));
		}
		
		function func02(){
			console.log($("#mingzhu li"));
		}
		
		function func03(){
			// 获取所有索引为奇数的标记
			console.log($("li:odd"));
		}
		
		function func04(){
			// 获取第一个li标记
			console.log($("li:first"));
		}
		
		function func05(){
			// 获取最后的li标记
			console.log($("li:last"));
		}
		
		function func06(){
			console.log($("ul li:first-child"));
		}
		
		function func07(){
			console.log($("ul li:last-child"));
		}
	</script>
	
</html>
```

## 四、jq事件

### 4.1 概述

* 页面对不同访问者的响应叫做事件。

* 事件处理程序指的是当 HTML 中发生某些事件时所调用的方法。

* jq处理事件的格式

  ```
  $("选择器").action(function);
  ```

  

### 4.2 事件类型

| 鼠标事件                                                     | 键盘事件                                                     | 表单事件                                                  | 文档/窗口事件                                             |
| :----------------------------------------------------------- | :----------------------------------------------------------- | :-------------------------------------------------------- | :-------------------------------------------------------- |
| [click](https://www.runoob.com/jquery/event-click.html)      | [keypress](https://www.runoob.com/jquery/event-keypress.html) | [submit](https://www.runoob.com/jquery/event-submit.html) | [load](https://www.runoob.com/jquery/event-load.html)     |
| [dblclick](https://www.runoob.com/jquery/event-dblclick.html) | [keydown](https://www.runoob.com/jquery/event-keydown.html)  | [change](https://www.runoob.com/jquery/event-change.html) | [resize](https://www.runoob.com/jquery/event-resize.html) |
| [mouseenter](https://www.runoob.com/jquery/event-mouseenter.html) | [keyup](https://www.runoob.com/jquery/event-keyup.html)      | [focus](https://www.runoob.com/jquery/event-focus.html)   | [scroll](https://www.runoob.com/jquery/event-scroll.html) |
| [mouseleave](https://www.runoob.com/jquery/event-mouseleave.html) |                                                              | [blur](https://www.runoob.com/jquery/event-blur.html)     | [unload](https://www.runoob.com/jquery/event-unload.html) |
| [hover](https://www.runoob.com/jquery/event-hover.html)      |                                                              |                                                           |                                                           |

### 4.3 事件案例

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>事件01</title>
		<script src="js/jquery-3.6.0.min.js" type="text/javascript" charset="utf-8"></script>
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
		
		<button type="button" id="btn">点我</button>
		
		用户名:<input type="text" id="username" value="" placeholder="请输入用户名..."/>
		
	</body>
	
	<script type="text/javascript">
		
		$("#box").mouseenter(function(){
			console.log("鼠标进入box范围");
		});
		
		$("#box").mouseleave(function(){
			console.log("鼠标移出box范围----------");
		});
		
		$("#btn").click(func01);
		
		function func01(){
			alert("btn被点击lallaa");
		}
		
		$("input").keypress(function(){
		   console.log(Math.random());
		});
		
		$("#username").blur(function(){
			console.log($("#username").val());
		})
		
	</script>
	
</html>
```

## 五、显示效果

### 5.1 hide和show

```
可选的 speed 参数规定隐藏/显示的速度，可以取以下值："slow"、"fast" 或毫秒。

可选的 callback 参数是隐藏或显示完成后所执行的函数名称。

下面的例子演示了带有 speed 参数的 hide() 方法：
```



```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>隐藏和显示</title>
		
		<script src="js/jquery-3.6.0.min.js" type="text/javascript" charset="utf-8"></script>
		
		<style type="text/css">
			#box{
				width: 300px;
				height: 300px;
				background-color: red;
				border-radius: 150px;
			}
		</style>
		
	</head>
	<body>
		<button type="button" onclick="func01()">隐藏</button>
		<button type="button" onclick="func02()">显示</button>
		<button type="button" onclick="func03()">隐藏/显示</button>
		
		<div id="box">
			
		</div>
		
	</body>
	
	<script type="text/javascript">
		
		function func01(){
			$("#box").hide(2000,function(){
				alert("隐藏完成");
			});
		}
		
		function func02(){
			$("#box").show(2000,function(){
				alert("显示完成...");
			});
		}
		// 切换状态
		function func03(){
			$("#box").toggle(2000);
		}
		
	</script>
</html>
```

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>悬浮显示效果</title>
		
		<script src="js/jquery-3.6.0.min.js" type="text/javascript" charset="utf-8"></script>
		
		<style type="text/css">
			#box{
				width: 80%;
				margin: auto;
				background-color: antiquewhite;
				height: 800px;
			}
			
			p{
				width: 100px;
				line-height: 40px;
				background-color: coral;
			}
			
			ul{
				width: 100px;
				height: 200px;
				background-color: #FF0000;
				display: none;
			}
		</style>
		
	</head>
	<body>
		<div id="box">
			<p id="list-p">所有商品</p>
			<ul id="product">
				<li>男装</li>
				<li>女装</li>
				<li>数码</li>
				<li>书籍</li>
				<li>箱包</li>
				<li>日用</li>
			</ul>
		</div>
	</body>
	
	<script type="text/javascript">
		
		$("#list-p").mouseenter(function(){
			$("#product").show(500);
		});
		
		$("#list-p").mouseleave(function(){
			$("#product").hide(500);
		});
		
	</script>
</html>
```

### 5.2 fadeIn和fadeOut

* fadeIn

```
jQuery fadeIn() 方法
jQuery fadeIn() 用于淡入已隐藏的元素。

语法:

$(selector).fadeIn(speed,callback);
可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。.

可选的 callback 参数是 fading 完成后所执行的函数名称。
```

* fadeOut

```
jQuery fadeOut() 方法用于淡出可见元素。

语法:

$(selector).fadeOut(speed,callback);
可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。

可选的 callback 参数是 fading 完成后所执行的函数名称。
```

* fadeToggle

```
jQuery fadeToggle() 方法可以在 fadeIn() 与 fadeOut() 方法之间进行切换。

如果元素已淡出，则 fadeToggle() 会向元素添加淡入效果。

如果元素已淡入，则 fadeToggle() 会向元素添加淡出效果。

语法:

$(selector).fadeToggle(speed,callback);
可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。

可选的 callback 参数是 fading 完成后所执行的函数名称。
```

* fadeTo

```
jQuery fadeTo() 方法允许渐变为给定的不透明度（值介于 0 与 1 之间）。

语法:

$(selector).fadeTo(speed,opacity,callback);
必需的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。

fadeTo() 方法中必需的 opacity 参数将淡入淡出效果设置为给定的不透明度（值介于 0 与 1 之间）。

可选的 callback 参数是该函数完成后所执行的函数名称。
```



```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>淡入和淡出</title>
		
		<script src="js/jquery-3.6.0.min.js" type="text/javascript" charset="utf-8"></script>
		
		<style type="text/css">
			#box{
				width: 300px;
				height: 300px;
				background-color: red;
			}
		</style>
		
	</head>
	<body>
		
		<button type="button" onclick="func01()">淡出</button>
		<button type="button" onclick="func02()">淡入</button>
		<button type="button" onclick="func03()">淡出/淡入</button>
		<button type="button" onclick="func04()">改变透明度</button>
		
		<hr >
		
		<div id="box">
			
		</div>
		
	</body>
	
	<script type="text/javascript">
		
		function func01(){
			$("#box").fadeOut(2000,function(){
				alert("淡出成功...");
			});
		}
		
		function func02(){
			$("#box").fadeIn(2000,function(){
				alert("淡入成功");
			});
		}
		
		function func03(){
			$("#box").fadeToggle(2000,function(){
				alert("切换成功");
			});
		}
		
		function func04(){
			$("#box").fadeTo(2000,0.5);
		}
		
	</script>
</html>
```

### 5.3 slideDown和slideUp

* slideDown

```
jQuery slideDown() 方法用于向下滑动元素。

语法:

$(selector).slideDown(speed,callback);
可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。

可选的 callback 参数是滑动完成后所执行的函数名称。
```

* slideUp

```
jQuery slideUp() 方法用于向上滑动元素。

语法:

$(selector).slideUp(speed,callback);
可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。

可选的 callback 参数是滑动完成后所执行的函数名称。
```

* slideToggle

```
jQuery slideToggle() 方法可以在 slideDown() 与 slideUp() 方法之间进行切换。

如果元素向下滑动，则 slideToggle() 可向上滑动它们。

如果元素向上滑动，则 slideToggle() 可向下滑动它们。

$(selector).slideToggle(speed,callback);
可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。

可选的 callback 参数是滑动完成后所执行的函数名称。
```

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>滑入滑出效果</title>
		<script src="js/jquery-3.6.0.min.js" type="text/javascript" charset="utf-8"></script>
		
		<style type="text/css">
			#box{
				width: 300px;
				height: 300px;
				background-color: red;
			}
		</style>
		
	</head>
	<body>
		<button type="button" onclick="func01()">上拉</button>
		<button type="button" onclick="func02()">下拉</button>
		<button type="button" onclick="func03()">滑入/滑出</button>
		
		<hr >
		
		<div id="box">
			
		</div>
		
	</body>
	
	<script type="text/javascript">
		
		function func01(){
			$("#box").slideUp(2000,function(){
				alert("收起成功...");
			});
		}
		
		function func02(){
			$("#box").slideDown(2000,function(){
				alert("放下成功..");
			});
		}
		
		function func03(){
			$("#box").slideToggle(2000);
		}
		
	</script>
</html>
```

### 5.4 动画效果

* 如果需要改变颜色，要下载颜色插件

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>动画01</title>
		<script src="js/jquery-3.6.0.min.js" type="text/javascript" charset="utf-8"></script>
		<script
		  src="https://code.jquery.com/color/jquery.color-2.2.0.min.js"
		  integrity="sha256-aSe2ZC5QeunlL/w/7PsVKmV+fa0eDbmybn/ptsKHR6I="
		  crossorigin="anonymous"></script>
		<style type="text/css">
			#box{
				position: relative;
				width: 100px;
				height: 100px;
				background-color: red;
			}
		</style>
		
	</head>
	<body>
		<button type="button" onclick="func01()">动画01</button>
		<button type="button" onclick="func02()">动画02</button>
		<div id="box">
			
		</div>
	</body>
	
	<script type="text/javascript">
		
		function func01(){
			console.log("动画开始...");
			$("#box").animate({
				width:'300px',
				height:'300px',
				left:'200px',
				top:'200px',
				backgroundColor:'rgb(0,0,255)'
			},2000);
			
			$("#box").animate({
				width:'200px',
				height:'200px',
				left:'400px',
				top:'0px',
				backgroundColor:'blue',
				borderRadius:'100px'
			},2000);
			console.log("动画结束...");
		}
		
		function func02(){
			$("#box").animate({
				width:'400px',
				height:'400px',
				left:'200px',
				top:'200px',
			},2000).animate({
				width:'100px',
				height:'100px',
				left:'400px',
				top:'0px',
			},2000,function(){
				alert("动画完成");
			});
		}
		
	</script>
	
</html>
```

### 5.5 动画停止

* 停止动画使用stop方法

```
jQuery stop() 方法用于停止动画或效果，在它们完成之前。

stop() 方法适用于所有 jQuery 效果函数，包括滑动、淡入淡出和自定义动画。

语法:

$(selector).stop(stopAll,goToEnd);
可选的 stopAll 参数规定是否应该清除动画队列。默认是 false，即仅停止活动的动画，允许任何排入队列的动画向后执行。

可选的 goToEnd 参数规定是否立即完成当前动画。默认是 false。

因此，默认地，stop() 会清除在被选元素上指定的当前动画。
```

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>停止动画</title>
		<script src="js/jquery-3.6.0.min.js" type="text/javascript" charset="utf-8"></script>
		<style type="text/css">
			#box{
				position: absolute;
				width: 100px;
				height: 100px;
				background-color: red;
			}
		</style>
	</head>
	<body>
		<button type="button" onclick="func01()">动画开始</button>
		<button type="button" onclick="func02()">动画结束</button>
		<div id="box">
			
		</div>
	</body>
	
	<script type="text/javascript">
		
		function func01(){
			$("#box").animate({
				width: "200px",
				height: "20px",
				left:"400px",
				top:"600px"
			},4000);
			
			$("#box").animate({
				width: "10px",
				height: "100px",
				left:"0px",
				top:"900px"
			},4000);
			
			$("#box").animate({
				width: "300px",
				height: "30px",
				left:"900px",
				top:"100px"
			},4000);
			
			$("#box").animate({
				width: "50px",
				height: "500px",
				left:"100px",
				top:"800px"
			},4000);
		}
		
		function func02(){
			$("#box").stop();
			$("#box").stop();
		}
		
	</script>
	
</html>
```

### 5.6 callback

* 回调函数
* 动画执行结束之后调用此函数，可选操作

### 5.7 链式编程

* 多个方法的调用链接在一起书写
* $("选择器").action01().action02().action03()
* 后面的函数都会执行到

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>链式编程</title>
		<script src="js/jquery-3.6.0.min.js" type="text/javascript" charset="utf-8"></script>
		<style type="text/css">
			#box{
				width: 300px;
				height: 300px;
				background-color: red;
			}
		</style>
	</head>
	<body>
		<button type="button" onclick="func01()">动画</button>
		<div id="box">
			
		</div>
	</body>
	
	<script type="text/javascript">
		
		function func01(){
			$("#box").css("background-color","yellow").slideUp(2000).slideDown(2000);
		}
		
	</script>
</html>
```

## 六、jQuery DOM 操作

### 6.1 概述

* jQuery 中非常重要的部分，就是操作 DOM 的能力。

* jQuery 提供一系列与 DOM 相关的方法，这使访问和操作元素和属性变得很容易。

### 6.2 获取数据

* text
* html
* value

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<script src="js/jquery-3.6.0.min.js" type="text/javascript" charset="utf-8"></script>
		<title>获取数据</title>
	</head>
	<body>
		<h3>题临安邸</h3>
		<h4>
			<a href="">林升</a>
		</h4>
		<p>山外青山楼外楼，</p>
		<p>西湖歌舞几时休。</p>
		<p>暖风熏得游人醉</p>
		<p>直把杭州作汴州。</p>
		
		<button type="button" onclick="func01()">获取标题</button>
		<button type="button" onclick="func02()">获取作者</button>
		<button type="button" onclick="func03()">获取诗句</button>
		<hr >
		<input type="text" id="new-title" placeholder="请输入新标题" />
		<button type="button" onclick="func04()">修改标题</button>
		
	</body>
	
	<script type="text/javascript">
		function func01(){
			var $h3 = $("h3");
			// js获取text的方法
			console.log($h3[0].innerText);
			// jq获取text的方法
			console.log($h3.text());
		}
		
		function func02(){
			var $h4 = $("h4");
			console.log($h4.text());
			console.log($h4.html());
		}
		
		function func03(){
			var $ps = $("p");
			console.log($ps);
			console.log($ps.text());
			
			for (var i = 0; i < $ps.length; i++) {
				console.log($ps[i].innerText);
			}
		}
		
		function func04(){
			var $newTitle = $("#new-title");
			console.log($newTitle.val());
			
			$("h3").html("<a href=''>" + $newTitle.val()+"</a>");
		}
		
	</script>
	
</html>
```

