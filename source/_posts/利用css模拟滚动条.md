---
title: 利用css模拟滚动条
date: 2016-03-10 20:08:02
tags: [css,模拟滚动条,摘抄]
---
## 模拟滚动条
 主要是好友看到我的博客的主题的模拟滚动条觉得不错，然后摘抄下来的，在这里做一下记录，就权当是笔记了。webkit支持拥有overflow属性的区域，列表框，下拉菜单，textarea的滚动条自定义样式，，不支持IE。
## webkit-scrollbar简介
### 啥是滚动条
滚动条是一个伪元素，可以自定义样式。这个伪类可以将webkit自身的滚动条渲染关闭，只按照用户自定义的css信息进行渲染。

```css
::-webkit-scrollbar {
   width: 13px;
   height: 13px;
}
```
例如上诉的代码所示，width和height属性分别表示纵向滚动条的宽度和横向滚动条的高。也可以指定为%百分比，在在这种情况下就代表了，滚动条占整个视窗的百分比
### 滚动条有啥
滚动条包括：滚动按钮和一个轨道。轨道本身又可以近一步被分为轨道碎片（track pieces）和一个滑块。轨道碎片指的是滑块上方和下面的区域。具体的细节如下：
>* ::-webkit-scrollbar 滚动条整体部分
* ::-webkit-scrollbar-thumb  滚动条里面的小方块，能向上向下移动（或往左往右移动，取决于是垂直滚动条还是水平滚动条）
* ::-webkit-scrollbar-track  滚动条的轨道（里面装有Thumb）
* ::-webkit-scrollbar-button 滚动条的轨道的两端按钮，允许通过点击微 调小方块的位置。
* ::-webkit-scrollbar-track-piece 内层轨道，滚动条中间部分（除去）
* ::-webkit-scrollbar-corner 边角，即两个滚动条的交汇处
* ::-webkit-resizer 两个滚动条的交汇处上用于通过拖动调整元素大小的小控件

### 伪类的设置
任何对象都可以设置：边框、阴影、背景图片等等，创建的滚动条任然会按照操作系统本身的设置来完成其交互的行为。
>* :horizontal(horizontal伪类适用于任何水平方向上的滚动条)
>* :vertical(vertical伪类适用于任何垂直方向的滚动条)
>* :decrement(decrement伪类适用于按钮和轨道碎片。表示递减的按钮或轨道碎片，例如可以使区域向上或者向右移动的区域和按钮)
>* :increment(increment伪类适用于按钮和轨道碎片。表示递增的按钮或轨道碎片，例如可以使区域向下或者向左移动的区域和按钮)
>* :start(start伪类适用于按钮和轨道碎片。表示对象（按钮 轨道碎片）是否放在滑块的前面)
>* :end(end伪类适用于按钮和轨道碎片。表示对象（按钮 轨道碎片）是否放在滑块的后面)
>* :double-button(double-button伪类适用于按钮和轨道碎片。判断轨道结束的位置是否是一对按钮。也就是轨道碎片紧挨着一对在一起的按钮。)
>* :single-button(single-button伪类适用于按钮和轨道碎片。判断轨道结束的位置是否是一个按钮。也就是轨道碎片紧挨着一个单独的按钮。)
>* :no-button(no-button伪类表示轨道结束的位置没有按钮。)
>* :corner-present(corner-present伪类表示滚动条的角落是否存在。)
>* :window-inactive(适用于所有滚动条，表示包含滚动条的区域，焦点不在该窗口的时候。)

### 常用的特殊状态的设置
```css
::-webkit-scrollbar-track-piece:start {
   /*滚动条上半边或左半边*/
}

::-webkit-scrollbar-thumb:window-inactive {
   /*当焦点不在当前区域滑块的状态*/

}

::-webkit-scrollbar-button:horizontal:decrement:hover {
   /*当鼠标在水平滚动条下面的按钮上的状态*/

}
```
## 本网站的滚动条代码示例
```css
::-webkit-scrollbar {
  width: 10px;
  height: 10px;
}
::-webkit-scrollbar-button {
  width: 0;
  height: 0;
}
::-webkit-scrollbar-button:start:increment,
::-webkit-scrollbar-button:end:decrement {
  display: none;
}
::-webkit-scrollbar-corner {
  display: block;
}
::-webkit-scrollbar-thumb {
  -webkit-border-radius: 8px;
  border-radius: 8px;
  background-color: rgba(0,0,0,0.2);
}
::-webkit-scrollbar-thumb:hover {
  -webkit-border-radius: 8px;
  border-radius: 8px;
  background-color: rgba(0,0,0,0.5);
}
::-webkit-scrollbar-track,
::-webkit-scrollbar-thumb {
  border-right: 1px solid transparent;
  border-left: 1px solid transparent;
}
::-webkit-scrollbar-track:hover {
  background-color: rgba(0,0,0,0.15);
}
::-webkit-scrollbar-button:start {
  width: 10px;
  height: 10px;
  background: url("../img/scrollbar_arrow.png") no-repeat 0 0;
}
::-webkit-scrollbar-button:start:hover {
  background: url("../img/scrollbar_arrow.png") no-repeat -15px 0;
}
::-webkit-scrollbar-button:start:active {
  background: url("../img/scrollbar_arrow.png") no-repeat -30px 0;
}
::-webkit-scrollbar-button:end {
  width: 10px;
  height: 10px;
  background: url("../img/scrollbar_arrow.png") no-repeat 0 -18px;
}
::-webkit-scrollbar-button:end:hover {
  background: url("../img/scrollbar_arrow.png") no-repeat -15px -18px;
}
::-webkit-scrollbar-button:end:active {
  background: url("../img/scrollbar_arrow.png") no-repeat -30px -18px;
}
```