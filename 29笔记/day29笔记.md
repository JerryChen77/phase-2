# Day29笔记

## 一、数组

### 1.1 基本类型数组创建

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>数组</title>
	</head>
	<body>
	</body>
	<script type="text/javascript">
		// 第一种创建数组方式
		var arr01 = [111,true,"haha",3.14];
		console.log(arr01);
		
		// 第二种创建数组
		var arr02 = new Array();
		console.log(arr02);
		arr02[0] = 123;
		arr02[1] = 3.1415;
		console.log(arr02);
		
		var arr03 = new Array(5);
		console.log(arr03);
		
		var arr04 = new Array("hello");
		console.log(arr04);
		
		var arr05 = new Array("张三","李思思","王五","赵柳");
		console.log(arr05);
		
		var arr06 = new Array(10,20,30,40);
		console.log(arr06);
	</script>
</html>
```

### 1.2 数组嵌套--多维数组

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>数组嵌套</title>
	</head>
	<body>
	</body>
	<script type="text/javascript">
		
		var arr01 = [111,222,333];
		var arr02 = [110,220,330,440];
		var arr03 = ["Hello","World",arr01];
		
		// 二维数组
		var arr = [arr01,arr02,arr03];
		console.log(arr);
		
		console.log(arr[1][2]);
		
		var arr05 = [10,20,30];
		console.log(arr05);
		
		arr05[3] = arr05;
		console.log(arr05);
		
	</script>
</html>
```

### 1.3 对象数组

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>对象数组</title>
	</head>
	<body>
	</body>
	
	<script type="text/javascript">
		var stu01 = {
			name:"宋江",
			age:22,
			subject:["山东话","河南话","浙江话"]
		};
		
		var stu02 = {
			name:"林冲",
			age:25,
			student:[
				{
					name:"张二蛋",
					age:15
				},
				{
					name:"刘大胆",
					age:16
				},
				{
					name:"葛二蛋",
					age:25
				}
			]
		};
		
		var stu03 = {
			name:"鲁智深",
			age:23
		};
		
		var stus = [stu01,stu02,stu03];
		console.log(stus);
		
		var cities = [
			{
				"北京市":[
				"西城区","东城区","朝阳区","昌平区","平谷区","密云区"
			]},
			{
				"河北省":[
					{
						"石家庄":[
							"桥西区",
							"高新区"
						]
					},
					{},
					{}
				]
			}
		];
		console.log(cities);
	</script>
	
</html>
```

## 二、运算符

### 2.1 算术运算符

### 2.2 赋值运算符

### 2.3 关系运算符

### 2.4 逻辑运算符

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>运算符01</title>
	</head>
	<body>
	</body>
	<script type="text/javascript">
		
		var a=110,b=210;
		console.log("a=" + a + ",b=" + b);
		
		/* 
			算术运算符
				+
				-
				*
				/
				%
				++
				--
		 */
		
		console.log("a + b = " + (a + b));	// 320
		console.log("a - b = " + (a - b));	// -100
		console.log("a * b = " + (a * b));	// 23100
		console.log("a / b = " + (a / b));	// 小数
		console.log("a % b = " + (a % b));	// 110
		a++;
		++b;
		console.log("a=" + a + ",b=" + b);
		
		console.log(a++);
		console.log(++b);
		
		console.log("a=" + a + ",b=" + b);
		
		/**
		 * 赋值运算符
		 * 	=
		 * 	+=
		 * 	-=
		 * 	*=
		 * 	/=
		 * 	%=
		 */
		
		var i = 10,j = 15;
		console.log("i=" + i + ",j=" + j);
		
		i += j;
		console.log("i=" + i + ",j=" + j);
		
		i -= j;
		console.log("i=" + i + ",j=" + j);
		
		i *= j;
		console.log("i=" + i + ",j=" + j);
		
		i /= j;
		console.log("i=" + i + ",j=" + j);
		
		i %= j;
		console.log("i=" + i + ",j=" + j);
		
		/**
		 * >
		 * >=
		 * <
		 * <=
		 * !=
		 * ==
		 * ===
		 */
		var x = 15,y = 25;
		console.log("x > y ? " + (x > y));
		console.log("x >= y ? " + (x >= y));
		console.log("x < y ? " + (x < y));
		console.log("x <= y ? " + (x <= y));
		console.log("x == y ? " + (x == y));
		var z = "15";
		console.log("x == z ? " + (x == z));
		console.log("x != z ? " + (x != z));
		console.log("x === z ? " + (x === z));
		
		/**
		 * 逻辑运算符
		 * 	&&
		 * 		遇到false结果就是false
		 *  ||
		 * 		遇到true结果就是true
		 *  !
		 * 		布尔值取反
		 */
		
		console.log("true && true == " + (true && true));
		console.log("true && false == " + (true && false));
		console.log("false && true == " + (false && true));
		console.log("false && false == " + (false && false));
		
		console.log("true || true == " + (true || true));
		console.log("true || false == " + (true || false));
		console.log("false || true == " + (false || true));
		console.log("false || false == " + (false || false));
		
		console.log("!true == " + !true);
		console.log("!false == " + !false);
		
		console.log(true + 1);
		console.log(false + 1);
		console.log(true + false);
	</script>
</html>
```

### 2.5 三元运算符

### 2.6 位运算符

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>运算符02</title>
	</head>
	<body>
	</body>
	<script type="text/javascript">
		
		var a = 22;
		var b = 33;
		
		var max;
		max = a > b ? a : b;
		console.log("a和b中最大的值是:" + max);
		
		max = a > b ? "a大" : "b大";
		console.log("a和b比较的结果:" + max);
		
		/**
		 * 0000 1010
		 * 0000 0101
		 */
		console.log("10 & 15 == " + (10 & 15));
		console.log("10 | 5 == " + (10 | 5));
		console.log(10 >> 1);
		console.log(10 << 2);
		
	</script>
</html>
```

## 三、分支

### 3.1 if结构

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>if结构</title>
	</head>
	<body>
	</body>
	
	<script type="text/javascript">
		
		/**
		 * 带刀子上车
		 * 课程表
		 * 月份和季节
		 */
		
		/**
		 * if
		 * if...else
		 * if...else if...else
		 */
		
		var len = 100;
		if (len >= 150) {
			console.log("刀具长度不合法...");
		} else{
			console.log("安检通过...");
		}
		console.log("OVER01");
		
		var day = 30;
		if (day == 1) {
			console.log("今天是星期一,课程有语文数学");
		} else if(day == 2){
			console.log("今天是星期二,课程有体育数学");
		} else if (day == 3) {
			console.log("今天是星期三,课程有体育语文");
		} else if(day == 4){
			console.log("今天是星期四,课程有语文数学");
		} else if(day == 5){
			console.log("今天是星期五,课程有英语");
		} else if(day == 6){
			console.log("今天是星期六,课程有体育");
		} else if(day == 7){
			console.log("今天是星期日,休息");
		} else{
			console.log("日期不存在...");
		}
		console.log("OVER02");
		
		var month = 15;
		if (month==12 || month==1 || month==2) {
			console.log("现在冬季,冷");
		} else if(month==3 || month==4 || month==5){
			console.log("现在春天,万物复苏");
		} else if (month==6 || month==7 || month==8) {
			console.log("现在是夏天,万物疯狂生长");
		} else if (month==9 || month==10 || month==11) {
			console.log("现在是秋季,收获的季节");
		} else{
			console.log("月份不存在");
		}
	</script>
</html>
```

### 3.2 switch结构

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>switch结构</title>
	</head>
	<body>
	</body>
	<script type="text/javascript">
		
		/**
		 * 课程表
		 * 月份和季节
		 */
		
		var day = 5;
		switch (day){
			case 1:
				console.log("今天是星期一,课程有语文数学");
				break;
			case 2:
				console.log("今天是星期二,课程有语文数学");
				break;
			case 3:
				console.log("今天是星期三,课程有语文数学");
				break;
			case 4:
				console.log("今天是星期四,课程有语文数学");
				break;
			case 5:
				console.log("今天是星期五,课程有语文数学");
				break;
			case 6:
				console.log("今天是星期六,课程有语文数学");
				break;
			case 7:
				console.log("今天是星期日,休息");
				break;
			default:
				console.log("日期不存在");
				break;
		}
		
		console.log("OVER01");
		
		var month = 7;
		switch (month){
			case 12:
			case 1:
			case 2:
				console.log("冬季");
				break;
				
			case 3:
			case 4:
			case 5:
				console.log("春季");
				break;
			
			case 6:
			case 7:
			case 8:
				console.log("夏季");
				break;
			
			case 9:
			case 10:
			case 11:
				console.log("秋季");
				break;
				
			default:
				console.log("月份不存在...");
				break;
		}
		
	</script>
</html>
```

## 四、循环结构

### 4.1 for循环

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>for循环</title>
	</head>
	<body>
	</body>
	<script type="text/javascript">
		
		/**
		 * 输出1--100
		 * 输出1--100偶数
		 * 计算1--100累加
		 */
		
		for (var i = 0; i < 100; i++) {
			console.log(i);
		}
		console.log("==========");
		
		for (var i = 0; i < 100; i++) {
			if (i % 2 == 0) {
				console.log(i);
			}
		}
		console.log("===========");
		
		var sum = 0;
		for (var i = 0; i <= 100; i++) {
			sum += i;
		}
		console.log("sum = " + sum);
		
		/* 
		for (var i = 0; i >= 0; i++) {
			console.log(i);
		} 
		*/
	</script>
</html>
```



### 4.2 while循环

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>while循环</title>
	</head>
	<body>
	</body>
	<script type="text/javascript">
		/**
		 * 输出1--100
		 * 输出1--100偶数
		 * 计算1-100累加
		 */
		
		var i;
		i = 0;
		while (i <= 100){
			console.log(i);
			i++;
		}
		console.log("===========");
		
		i = 0;
		while (i <= 100){
			if (i % 2 == 0) {
				console.log(i);
			}
			i++;
		}
		console.log("===========");
		
		var sum = 0;
		i = 0;
		while (i <= 100){
			sum += i;
			i++;
		}
		console.log("sum = " + sum);
	</script>
</html>
```

### 4.3 do...while循环

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>dowhile</title>
	</head>
	<body>
	</body>
	<script type="text/javascript">
		/**
		 * 输出1--100
		 * 输出1--100偶数
		 * 计算1-100累加
		 */
		
		var i;
		i = 0;
		do {
			console.log(i);
			i++;
		} while (i <= 100)
		console.log("===========");
		
		i = 0;
		do {
			if (i % 2 == 0) {
				console.log(i);
			}
			i++;
		} while (i <= 100)
		console.log("===========");
		
		i = 0;
		var sum = 0;
		do {
			sum += i;
			i++;
		} while (i <= 100)
		console.log("sum = " + sum);
	</script>
</html>
```

### 4.4 foreach

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>foreach</title>
	</head>
	<body>
	</body>
	<script type="text/javascript">
		var arr = [111,222,333,444,555];
		for(var i in arr){
			console.log(i + "===" + arr[i]);
		}
		console.log("============");
		
		for(var a of arr){
			console.log(a);
		}
		
		console.log("============");
		
		for(let a of arr){
			console.log(a);
		}
	</script>
</html>
```

### 4.5 遍历对象

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>遍历对象</title>
	</head>
	<body>
	</body>
	<script type="text/javascript">
		var person = {
			name:"张三",
			age:23,
			addr:"九堡"
		};
		
		for (let s in person) {
			console.log(s + "===" + person[s]);
		}
		console.log("=============");
	</script>
</html>
```

