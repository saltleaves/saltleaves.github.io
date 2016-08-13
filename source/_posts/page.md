---
title: 面试知识点：HTML5
date: 2016-08-10 20:59:00
tags: [html,面试]
---

## 随便说两句
现在的招聘人员啊，招聘要求不写几句html5都不好意思说自己是招前端，结果这个问题的热度也就跟杭城的天气一样，那是居高不下啊。前不久某只犬类动物投简历还问及了，只好炒冷饭，防止自己以后忘记了。 

## 属性举例

### 使用 HTML5 表单和输入框
HTML5 有很多的新表单属性，很多的小伙伴都已经熟练地掌握了，虽然不是所有的浏览器都支持，但是还是很好用滴：
>- autofocus 使得页面加载完毕后自动为某个输入框设置输入焦点
- placeholder 允许你为输入框设置默认文本，并在获取焦点时自动清除
- required 属性要求必须填写值后才能提交表单
- pattern 可以通过正则表达式指定输入框允许输入的内容


因为这些功能都是内置的，无需使用 JavaScript 方法来实现，第一是节省开发时间，同时也让页面具有更好的适应性。

### 使用 CSS 转换效果

不好意思混入了奸细，使用 CSS 转换效果来替换 JavaScript 的方法可以提升页面元素在两种状态进行转换的速度，通过使用totheleft 和 totheright 你可以迅速移动一个框。例如：

```
div.box { 
	left:50px; 
//for webkit browsers 
	-webkit-transition: all 0.3s ease-out; 
//for mozilla 
	-moz-transition: all 0.3s ease-out; 
//for opera 
	-o-transition: all 0.3s ease-out; 
//other browsers 
	transition: all 0.3s ease-out;
}
div.box.totheleft {
 left: 0px;
}
div.box.totheright {
 left: 80px;
}
```

### 使用 HTML5 Web 存储
当你需要在浏览器上存储一些数据时，你可能会首先考虑到 Cookie，但是 Cookie 在每次浏览器请求时都会附带上。这时 HTML5 更有效的方法就是本地存储 —— Web Storage出现啦，啦啦啦啦~它有两个 Web Storage 对象分别是：sessionStorage 和 localStorage ，这些存储的数据是不会通过 HTTP 请求来传输的，因此不会对请求的时间参数任何影响，下面是一小段示例代码：

```
//check to see if localstorage is present (browser supports HTML5)
	if (('localStorage' in window) && window.localStorage !== null) { 
//store items
	 	localStorage.wishlist = '["Bear", "Cow", "Pig"]';
	}
```

从上面代码我们可看到，比使用 Cookie 的方法更加简单，无需指定失效时间。

### 使用 Web Workers

Web Workers 是 HTML5 规范内容之一，用于提供后台脚本运行支持。相当于是多线程的处理环境。示例代码：

```
var worker = new Worker('doWork.js');
worker.addEventListener('message', function(e) {
	console.log('Worker said: ', e.data);
}, false);
worker.postMessage('Hello World'); // Send data to our worker.
```
Web Workers 可在很多场景下使用，例如图片处理、文本格式和以及大文件接收和处理等等。

### 使用 Web Sockets

Web Sockets 用来实现跟远程主机的双路通讯，例如在 Web 浏览器和远程服务器之间，这是一个非常轻量级的通讯架构，带宽占用以及性能方面比标准 HTTP 要减少 3~5 倍。因为 Web Sockets 必须使用 80 端口，因此 Web Sockets 不仅用来创建跟快速的通讯接口，还可以在 HTTP 之上实现跟高级的双路通讯。
目前遇到过使用场景是在线客服。

### 使用应用程序缓存
应用程序缓存可以让你创建完全支持离线浏览的 Web 应用，降低服务器负载以及更快的体验速度。可通过缓存的 manifest 文件来指定要缓存的文件，manifest 只是一个简单的文本文件，下面是一个示例：

```html
  CACHE MANIFEST# 2016-08-08:v3
  #Explicitly cached entries
  index.htm
  style.css
  #offline.htm will be displayed if the user is offline
  FALLBACK:/ /offline.htm
```
你需要在HTML页面中启用缓存

```html
<html manifest="http://www.example.com/example.appcache">
  ...
</html>
```
Manifest 缓存文件可以定义缓存任意的文件扩展名，但你需要在 Web 服务器上设置对应的 MIME 类型，例如在 Apache 上：
AddType text/cache-manifest .appcache
使用应用程序缓存，你只需要简单几步就可以创建离线的 Web 应用，访问是非常快速，适合用来处理一些不经常更新的静态文件。