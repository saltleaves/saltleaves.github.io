---
title: CSS制作气泡
date: 2016-06-06 22:39:06
tags: [css]
---


## 制作气泡的效果图
 ![运行截图1](http://7xrkml.com1.z0.glb.clouddn.com/qipao1.png)

## 制作方法说明
首先，由于兼容的问题，没有使用伪类，可以使用伪类优化代码，首先我们需要知道一个三角形怎么完成。

### border属性说明
首先我们来玩一下border这个属性，当我们把一个div的border-color设为不同值的时候，可以看到四边都成了一个梯形。

```
	#test{
		width:50px; 
		height:50px; 
		border-width:50px; 
		border-style:solid; 
		border-color:#00ff00 #ff00ff #ff0000 #0000ff;
	}
```
效果图如下：
![运行截图2](http://7xrkml.com1.z0.glb.clouddn.com/tixing.png)

我们继续玩这个属性，可以想象，如果这个div没有宽高，那么应当是四个三角形。
```
	#test{
		width:0; 
		height:0;
		border-width:50px; 
		border-style:solid; 
		border-color:#00ff00 #ff00ff #ff0000 #0000ff;
	}
```
![运行截图3](http://7xrkml.com1.z0.glb.clouddn.com/4-sanjiaoxing.png)
结果果然如我们所料，那么可以想象，假如只有一条边有颜色，其余的边都为透明，就是一个三角形了。
```
	#test{
		 width:0; 
		 height:0; 
		 border-width:50px; 
		 border-style:solid; 
		 border-color:#ff00ff transparent transparent; 
	}
```
![运行截图4](http://7xrkml.com1.z0.glb.clouddn.com/1-sanjiaoxing.png)
一个三角形已经画好了，而我们最终效果是一个镂空的三角形，所以，我们只要在叠加一个与背景色相同发的三角形即可。

### 兼容IE6

在各大的主流浏览器中，测试上上诉的代码的，结果发现，IE6下存在两个问题

1. 上下边能形成三角形，左右两边仍然还是梯形
>* 解决方法：font-size和line-height都设为0的时候，div的四边在IE6下都能形成完美的三角形

2. IE6下transparent无效！其他三边被设置成默认的黑色了。
>* 解决方法：把border-style设置为dashed后，IE6下其他三边就能透明了！

###  最终代码实现
为了更方便维护，代码结构有所改动。
css如下：
```
	.tag{ 
		width:300px; 
		padding: 20px;
		border:5px solid #64A7D0; 
		position:relative; 
		background-color:#FFF;
	}
	.arrow{ 
		position:absolute; 
		width:40px; 
		height:40px; 
		bottom:-40px; 
		left:100px; 
	}
	.arrow *{ 
		display:block; 
		border-width:20px; 
		position:absolute; 
		border-style:solid dashed dashed dashed; 
		font-size:0; 
		line-height:0; 
	}
	.arrow em{
		border-color:#64A7D0 transparent transparent;
	}
	.arrow span{
		border-color:#FFF transparent transparent; top:-7px;
	}
```
html:
```
	<div class="tag">
 		<div class="arrow">
     		<em></em><span></span>
    	</div>
    	CSS气泡框实现
	</div>
```
### 思考题
![运行截图5](http://7xrkml.com1.z0.glb.clouddn.com/qipao2.png)
那么如图所示的不规则三角形该怎么制作呢，也很简单，只需要稍微改动代码即可。页面结构不变。
css如下：
```
.tag{ 
		width:300px;
	 	height:100px;
	 	position:relative; 
	 	background-color:#64A7D0;
	 }
	.arrow{ 
		position:absolute; 
		width:70px; 
		height:60px; 
		left:-70px; 
		bottom:10px;
	}
	.arrow *{ 
		display:block; 
		position:absolute; 
		border-style:dashed solid solid dashed; 
		font-size:0; 
		line-height:0; 
	}
	.arrow em{
		border-color:transparent #64A7D0 #64A7D0 transparent; 
		border-width:30px 35px;
	}

	.arrow span{ 
		border-width:20px 35px;
		border-color:transparent #FFF #FFF transparent; 
		bottom:0;
	}

```
### 伪类制作

为了减少结构的冗余，我们可以使用CSS3的伪类来达到一样的效果
```
.tag{
    width:300px;
    height:100px;
    border:5px solid #09F;
    position:relative;
    background-color:#FFF;
}
.tag:before,.tag:after{
    content:"";display:block;
    border-width:20px;
    position:absolute; bottom:-40px;
    left:100px;
    border-style:solid dashed dashed;
    border-color:#09F transparent transparent;
    font-size:0;
    line-height:0;
}
.tag:after{
    bottom:-33px;
    border-color:#FFF transparent transparent;
}
```