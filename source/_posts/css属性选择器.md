---
title: css属性选择器
date: 2016-05-17 20:24:04
tags: [css]
---
## 基础说明
CSS 2 引入了属性选择器，可以根据元素的属性及属性值来选择元素。下面列举了常用的方法，参考[w3school](http://www.w3school.com.cn/css/css_selector_attribute.asp) 

## 属性举例

### [title]获取有title属性的元素。
代码举例：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>选择器</title>

		<style>			
		[yezi] { background: red;} /*IE7 √ IE8 √ IE9 √ IE11 √ safari √ firefox √ chrome √*/
		</style>
	</head>
	<body>
		<ul>
			<li yezi>无序列表第一</li>
			<li>无序列表第二</li>
			<li zi>无序列表第一</li>
			<li>无序列表第二</li>
			<li ye>无序列表第一</li>
		</ul>
	</body>
</html>

```


运行结果图：
![运行截图1](http://7xrkml.com1.z0.glb.clouddn.com/1.png)

### [title=yezi]:获取title属性值为yezi的元素。

代码举例：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>选择器</title>
		<style>			
		[title=yezi] { background:#FFE4C4;}/*IE7 √ IE8 √ IE9 √ IE11 √ safari √ firefox √ chrome √*/
		</style>
	</head>
	<body>
		<ul>
			<li title="yezi">无序列表第一</li>
			<li title="11 yezi">无序列表第二</li>
			<li title="yezi">无序列表第三</li>
		</ul>
	</body>
</html>
``` 

运行结果图：
![运行截图2](http://7xrkml.com1.z0.glb.clouddn.com/2.png)


### [title~=hello]:获取title元素中有hello样式(可以存在其他的)

代码举例：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>选择器</title>
		<style>					
		[title~=hello] { background:red}				
		</style>
	</head>
	<body>
		<ul>
			<li title="hello wrold">无序列表第一</li>
			<li title="hellowrold">title属性中有hello英文</li>
			<li title="hello-wrold">title属性中有hello英文，-区分</li>
		</ul>
	</body>
</html>
``` 

运行结果图：
![运行截图3](http://7xrkml.com1.z0.glb.clouddn.com/3.png)

### [title|=hello]:用于选取带有以指定值开头的属性值的元素，该值必须是整个单词。

代码举例：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>选择器</title>
		<style>					
		[title|=hello] { background:red}				
		</style>
	</head>
	<body>
		<ul>
			<li title="hello-wrold">是单词</li>
			<li title="hello wrold">不为一个单词</li>
			<li title="hello_wrold">title属性中有hello英文，_区分</li>
			<li title="hellowrold">title属性中有hello英文</li>
		</ul>
	</body>
</html>
``` 

运行结果图：
![运行截图4](http://7xrkml.com1.z0.glb.clouddn.com/4.png)

### [title^=hello]:获取title属性值开头是hello的元素

代码举例：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>选择器</title>
		<style>					
		[title^=hello] { background:red}				
		</style>
	</head>
	<body>
		<ul>
			<li title="hello-wrold">hello在开头</li>
			<li title="ni-hello">hello在结尾</li>	
			<li title="hello">单独hello</li>
			<li title="hellowrold">helloworld 不分开</li>	
		</ul>
	</body>
</html>
``` 

运行结果图：
![运行截图5](http://7xrkml.com1.z0.glb.clouddn.com/5.png)

### [title$=hello]:获取title元素值结尾是hello的元素
代码举例：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>选择器</title>
		<style>					
		[title$=hello] { background:red}				
		</style>
	</head>
	<body>
		<ul>
			<li title="hello-wrold">hello在开头</li>
			<li title="ni-hello">hello在结尾</li>	
			<li title="hello">单独hello</li>
			<li title="hellowrold">helloworld 不分开</li>			
		</ul>
	</body>
</html>
``` 

运行结果图：
![运行截图6](http://7xrkml.com1.z0.glb.clouddn.com/6.png)

### [title*=hello]:获取title元素值中存在hello的元素。
代码举例：

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>选择器</title>
		<style>					
		[title*=hello] { background:red}				
		</style>
	</head>
	<body>
		<ul>
			<li title="wroldhellowrold">中间有hello</li>
			<li title="hello-wrold">hello在开头</li>
			<li title="ni-hello">hello在结尾</li>	
			<li title="hello">单独hello</li>
			<li title="hellowrold">helloworld 不分开</li>			
		</ul>
	</body>
</html>
``` 

运行结果图：
![运行截图7](http://7xrkml.com1.z0.glb.clouddn.com/7.png)