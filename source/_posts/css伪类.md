---
title: css伪类和伪元素
date: 2016-06-10 13:56:16
tags: [css]
---

## 伪类和伪元素的概念
w3c 对两者的定义：
>* CSS 伪类用于向某些选择器添加特殊的效果。
>* CSS 伪元素用于将特殊的效果添加到某些选择器。

## 伪类和伪元素的区别
这里用伪类 :first-child 和伪元素 :first-letter 来进行比较。
```
	p>i:first-child {
		color: red
	}
//结构
	<p>
    	<i>first</i>
    	<i>second</i>
	</p>
```
如果我们不使用伪类，而希望达到上述效果，可以这样做：
```
	.first-child {
		color: red
	}
//结构
	<p>
    	<i class="first-child">first</i>
    	<i>second</i>
	</p>
```
即我们给第一个子元素添加一个类，然后定义这个类的样式。那么我们接着看看为元素：
```
	p:first-letter {
		color: red
	}
//结构
	<p>I am stephen lee.</p>
```
那么如果我们不使用伪元素，要达到上述效果，应该怎么做呢？
```
	.first-letter {
		color: red
	}
//结构
	<p><span class='first-letter'>I</span> am stephen lee.</p>
```
即我们给第一个字母添加一个 span，然后给 span 增加样式。
两者的区别已经出来了。那就是：
>* 伪类的效果可以通过添加一个实际的类来达到，而伪元素的效果则需要通过添加一个实际的元素才能达到，这也是为什么他们一个称为伪类，一个称为伪元素的原因。

## 常见的伪类和伪元素说明

### 锚伪类

伪类 | 说明
-----|------
a:link|未访问的链接    
a:visited| 已访问的链接    
a:hover| 鼠标移动到链接上,此伪类不止限于超链接上，其他元素也可使用   
a:active|选定的链接,被激活的元素，其他元素也使用

注意：在 CSS 定义中，a:hover 必须被置于 a:link 和 a:visited 之后，才是有效的；a:active 必须被置于 a:hover 之后，才是有效的；伪类名称对大小写不敏感。
### 其余伪类

伪类 | 说明
-----|------ 
:focus| 向拥有键盘输入焦点的元素添加样式。
:first-child	| 向元素的第一个子元素添加样式。
:lang|向带有指定 lang 属性的元素添加样式。

### 伪元素

CSS中，还有伪元素，形态及使用方法类同伪类。

伪元素 | 说明
-----|------ 
:first-letter|向文本的第一个字母添加特殊样式。
:first-line	| 向文本的首行添加特殊样式。。
:before|在元素之前添加内容。
:after|在元素之后添加内容。