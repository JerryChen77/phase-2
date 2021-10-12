# Day34笔记

## 一、Validate

### 1.1 概述

* jQuery Validate 插件为表单提供了强大的验证功能，让客户端表单验证变得更简单，同时提供了大量的定制选项，满足应用程序各种需求。
* 该插件捆绑了一套有用的验证方法，包括 URL 和电子邮件验证，同时提供了一个用来编写用户自定义方法的 API。
* 所有的捆绑方法默认使用英语作为错误信息，且已翻译成其他 37 种语言。

### 1.2 使用教程

* 导入jquery.js
* 导入validate.js
* 如果需要中文提示，导入message.zh.js
* 在脚本中书写验证规则
  * rules
  * messages
  * 验证的选项和标签的name属性一致

### 1.3 validate基本使用

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<!-- 引入jq框架 -->
		<script src="js/jquery-3.6.0.min.js" type="text/javascript" charset="utf-8"></script>
		<script src="js/jquery.validate.min.js" type="text/javascript" charset="utf-8"></script>
		<script src="js/messages_zh.min.js" type="text/javascript" charset="utf-8"></script>
		<link rel="stylesheet" type="text/css" href="css/validation.css"/>
	</head>
	<body>
		<form method="get" id="myForm">
			用户名:
			<input type="text" id="username" name="username" value="" placeholder="请输入6--20用户名..." />
			<br>

			密码:
			<input type="password" name="password" id="password" value="" placeholder="请输入6--20密码..." />
			<br>

			邮箱:
			<input type="email" name="email" id="email" value="" placeholder="请输入邮箱..." />
			<br>

			<input type="submit" value="提交" />
		</form>
	</body>

	<script type="text/javascript">
		$("#myForm").validate({
			rules: {
				username: {
					required: true,
					minlength: 6,
					maxlength:20
				},
				password: {
					required: true,
					minlength: 6,
					maxlength:20
				},
				email: {
					required: true,
					email: true
				},
			},
			messages: {
				username: {
					required: "请输入合法用户名，长度6--20字符",
					minlength: "用户名长度不能小于 6 个字符",
					maxlength: "用户名长度不能大于 20 个字符"
				},
				password: {
					required: "请输入密码",
					minlength: "密码长度不能小于 6 个字符",
					maxlength: "密码长度不能大于 20 个字符"
				},
				email: "请输入一个正确的邮箱",
			}
		});
	</script>

</html>
```

## 二、Bootstrap

### 2.1 概述

* 快速布局的一个开源框架
* 预设了很多css样式
* 可以根据需要导入到我们的项目中

### 2.2 开发教程

* 下载bootstrap开发包
  * css
  * js
* 导入到项目中
* 设置对应的class属性，展示需要的效果

### 2.3 栅格系统

* 对页面进行布局的操作
* 默认每行是12列
* 可以使用不同的class属性设置对应的列数

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<script src="js/jquery-3.6.0.min.js" type="text/javascript" charset="utf-8"></script>
		<script src="js/bootstrap.min.js" type="text/javascript" charset="utf-8"></script>
		<link rel="stylesheet" type="text/css" href="css/bootstrap.min.css"/>
		<link rel="stylesheet" type="text/css" href="css/bootstrap-theme.min.css"/>
	</head>
	<body>
		
		<div class="container">
			<div class="row">
			  <div class="col-md-1">.col-md-1</div>
			  <div class="col-md-1">.col-md-1</div>
			  <div class="col-md-1">.col-md-1</div>
			  <div class="col-md-1">.col-md-1</div>
			  <div class="col-md-1">.col-md-1</div>
			  <div class="col-md-1">.col-md-1</div>
			  <div class="col-md-1">.col-md-1</div>
			  <div class="col-md-1">.col-md-1</div>
			  <div class="col-md-1">.col-md-1</div>
			  <div class="col-md-1">.col-md-1</div>
			  <div class="col-md-1">.col-md-1</div>
			  <div class="col-md-1">.col-md-1</div>
			</div>
			
			<div class="row">
			  <div class="col-md-3">.col-md-1</div>
			  <div class="col-md-3">.col-md-1</div>
			  <div class="col-md-3">.col-md-1</div>
			  <div class="col-md-3">.col-md-1</div>
			</div>
			
			<div class="row">
			  <div class="col-md-1">.col-md-1</div>
			  <div class="col-md-2">.col-md-1</div>
			  <div class="col-md-3">.col-md-1</div>
			  <div class="col-md-4">.col-md-1</div>
			</div>
			
			<div class="row">
			  <div class="col-xs-6 col-md-4 col-md-offset-4">.col-xs-6 .col-md-4</div>
			  <div class="col-xs-6 col-md-4">.col-xs-6 .col-md-4</div>
			</div>
			
			<div class="row">
			  <div class="col-sm-9">
			    Level 1: .col-sm-9
			    <div class="row">
			      <div class="col-xs-8 col-sm-6">
			        Level 2: .col-xs-8 .col-sm-6
			      </div>
			      <div class="col-xs-4 col-sm-6">
			        Level 2: .col-xs-4 .col-sm-6
			      </div>
			    </div>
			  </div>
			</div>
		</div>
	</body>
</html>
```

### 2.4 排版

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<script src="js/jquery-3.6.0.min.js" type="text/javascript" charset="utf-8"></script>
		<script src="js/bootstrap.min.js" type="text/javascript" charset="utf-8"></script>
		<link rel="stylesheet" type="text/css" href="css/bootstrap.min.css"/>
		<link rel="stylesheet" type="text/css" href="css/bootstrap-theme.min.css"/>
	</head>
	<body>
		<div class="container">
			<h1>h1. Bootstrap heading<small>Secondary text</small></h1>
			<h2>h2. Bootstrap heading</h2>
			<h3>h3. Bootstrap heading</h3>
			<h4>h4. Bootstrap heading</h4>
			<h5>h5. Bootstrap heading</h5>
			<h6>h6. Bootstrap heading</h6>
			
				
			<p>
				Nullam quis risus eget urna mollis ornare vel eu leo. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Nullam id dolor id nibh ultricies vehicula.
				
				Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec ullamcorper nulla non metus auctor fringilla. Duis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit. Donec ullamcorper nulla non metus auctor fringilla.
				
				Maecenas sed diam eget risus varius blandit sit amet non magna. Donec id elit non mi porta gravida at eget metus. Duis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit.
			</p>
			
			<p class="lead">
				Vivamus sagittis lacus vel augue laoreet rutrum faucibus dolor auctor. Duis mollis, est non commodo luctus.
			</p>
			
			<p>
				You can use the mark tag to <mark>highlight</mark> text.
			</p>
			
			<p>
				This line of text is meant to be treated <del>as deleted text.</del>
			</p>
			
			<p>
				This line of text is meant to be treated as an <ins>addition to the document.</ins>
			</p>
			
			<p class="text-left">Left aligned text.</p>
			<p class="text-center">Center aligned text.</p>
			<p class="text-right">Right aligned text.</p>
			<p class="text-justify">Justified text.</p>
			<p class="text-nowrap">No wrap text.</p>
			<p>An abbreviation of the word attribute is <abbr title="attribute">attr</abbr>.</p>
			
			<p>
				<address>
				  <strong>Twitter, Inc.</strong><br>
				  1355 Market Street, Suite 900<br>
				  San Francisco, CA 94103<br>
				  <abbr title="Phone">P:</abbr> (123) 456-7890
				</address>
				
				<address>
				  <strong>Full Name</strong><br>
				  <a href="mailto:#">first.last@example.com</a>
				</address>
			</p>
			
			<p>
				<blockquote>
				  <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer posuere erat a ante.</p>
				</blockquote>
			</p>
			
			<p>
				<blockquote class="blockquote-reverse">
					<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer posuere erat a ante.</p>
				</blockquote>
			</p>
			
			<ul class="list-inline">
				<li>首页</li>
				<li>图书</li>
			    <li>电影</li>
				<li>小说</li>
			</ul>
			
			<dl>
				<dt>天龙八部</dt>
				<dd>乔峰</dd>
				<dd>段誉</dd>
				<dd>虚竹</dd>
				<dt>天龙八部</dt>
				<dd>乔峰</dd>
				<dd>段誉</dd>
				<dd>虚竹</dd>
			</dl>
			
			<dl class="dl-horizontal">
			  <dt>天龙八部</dt>
			  <dd>乔峰</dd>
			  <dd>段誉</dd>
			  <dd>虚竹</dd>
			  
			  <dt>水浒传</dt>
			  <dd>宋江</dd>
			  <dd>呼延灼</dd>
			  <dd>林冲</dd>
			</dl>
			
			<p>
				To switch directories, type <kbd>cd</kbd> followed by the name of the directory.<br>
				To edit settings, press <kbd><kbd>ctrl</kbd> + <kbd>,</kbd></kbd>
			</p>
			
			<p>
				<var>y</var> = <var>m</var><var>x</var> + <var>b</var>
			</p>
			
		</div>
		
	</body>
</html>
```

### 2.5 表格

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<script src="js/jquery-3.6.0.min.js" type="text/javascript" charset="utf-8"></script>
		<script src="js/bootstrap.min.js" type="text/javascript" charset="utf-8"></script>
		<link rel="stylesheet" type="text/css" href="css/bootstrap.min.css"/>
	</head>
	<body>
		<div class="container">
			<table class="table table-striped table-bordered table-hover">
				<tr>
					<th>Header</th>
					<th>Header</th>
					<th>Header</th>
				</tr>	
				<tr>
					<td>Data</td>
					<td>Data</td>
					<td>Data</td>
				</tr>
				
				<tr>
					<td>Data</td>
					<td>Data</td>
					<td>Data</td>
				</tr>
				
				<tr>
					<td>Data</td>
					<td>Data</td>
					<td>Data</td>
				</tr>	
			</table>
			
			<table class="table table-striped table-bordered table-hover table-condensed">
				<tr>
					<th>Header</th>
					<th>Header</th>
					<th>Header</th>
				</tr>	
				<tr>
					<td>Data</td>
					<td>Data</td>
					<td>Data</td>
				</tr>
				
				<tr>
					<td>Data</td>
					<td>Data</td>
					<td>Data</td>
				</tr>
				
				<tr>
					<td>Data</td>
					<td>Data</td>
					<td>Data</td>
				</tr>	
			</table>
			
			<table class="table table-bordered table-responsive">
				<tr>
					<th>Header</th>
					<th>Header</th>
					<th>Header</th>
				</tr>	
				<tr class="active">
					<td>Data</td>
					<td>Data</td>
					<td>Data</td>
				</tr>
				
				<tr class="success">
					<td>Data</td>
					<td>Data</td>
					<td>Data</td>
				</tr>
				
				<tr class="warning">
					<td>Data</td>
					<td>Data</td>
					<td>Data</td>
				</tr>	
				
				<tr class="danger">
					<td>Data</td>
					<td>Data</td>
					<td>Data</td>
				</tr>
				
				<tr class="info">
					<td>Data</td>
					<td>Data</td>
					<td>Data</td>
				</tr>
				
				<tr>
					<td>Data</td>
					<td>Data</td>
					<td>Data</td>
				</tr>
			</table>
			<div class="table-responsive">
				<table class="table table-bordered">
					<tr>
						<th>Header</th>
						<th>Header</th>
						<th>Header</th>
					</tr>	
					<tr class="active">
						<td>Data</td>
						<td>Data</td>
						<td>Data</td>
					</tr>
					
					<tr class="success">
						<td>Data</td>
						<td>Data</td>
						<td>Data</td>
					</tr>
					
					<tr class="warning">
						<td>Data</td>
						<td>Data</td>
						<td>Data</td>
					</tr>	
					
					<tr class="danger">
						<td>Data</td>
						<td>Data</td>
						<td>Data</td>
					</tr>
					
					<tr class="info">
						<td>Data</td>
						<td>Data</td>
						<td>Data</td>
					</tr>
					
					<tr>
						<td>Data</td>
						<td>Data</td>
						<td>Data</td>
					</tr>
				</table>
			</div>
		</div>
	</body>
</html>
```

