---
title: 如何用hexo搭建个人博客
date: 2016-03-06 21:32:17
tags: [hexo,博客]
---
## 准备工作
 > * 安装git:不会安装，请查看：[window系统下如何安装git](http://saltleaves.github.io/2016/03/01/hello-world/) 
 > * 安装node.js:官网下载安装
 > * 托管代码的网站：github或者gitcafe(天朝本土化的github)

## hexo基础命令讲解
首先，下面的的代码将不再重复叙述，先把各个hexo 的基本命令介绍一下：

```java
$ hexo g  //完整命令为hexo generate,用于生成静态文件
$ hexo s  //完整命令为hexo server,用于启动服务器，主要用来本地预览（localhost:4000）
$ hexo d  //完整命令为hexo deploy,用于将本地文件发布到github上
$ hexo n  //完整命令为hexo new,用于新建一篇文章
```
## 开始搭建
以下为正常情况下的安装流程，假如出现跟说好的不一样的情况，最后会有一部分的问题解答。
### 安装hexo 
在任意的地方鼠标右键，打开git bash输入
```
$ npm install hexo-deployer-git --save
$ hexo g
$ hexo d
```
### 下载网站所需文件
创建放置博客文件的文件夹：hexo文件夹。在自己想要的位置创建文件夹，例如**E:\hexo**，当然最好不要放在中文路径下。之后进入文件夹，即**E:\hexo**内，点击鼠标右键，选择Git Bash，执行以下命令，Hexo会自动在该文件夹下下载搭建网站所需的所有文件。 
```
$ hexo init
```
### 下载依赖包
```
$ npm install
```
### 查看结果
可以先看看刚刚下载的hexo文件带来了什么，在E:\hexo内执行以下命令
```
$ hexo g
$ hexo s
```
## 继续升级（选择主题）
可以从知乎或者其他的地方选择自己喜欢的主题，并且下载下来，放置在themes文件夹下，下面是以默认主题为例的修改配置文件：
 * 博客的配置文件:在自己定义的目录（E:\hexo）的_config.yml
 * 主题的配置文件:E:\hexo\themes\landscape\_config.yml

## 部署到github
### 注册github账号
已有的可以跳过，没有的，请[在此](https://github.com/)注册，这里就不介绍了
### 创建Repository
 需要注意的是Repository的名字，需要和你的github的账户名相同，由于我的已经创建过了，所以红色警告无须在意。
![创建过程示例](http://7xrkml.com1.z0.glb.clouddn.com/QQ%E6%88%AA%E5%9B%BE20160308215634.png)

### 配置连接到github
打开你刚刚创建的Repository，选择SSH，然后复制。
![创建过程示例](http://7xrkml.com1.z0.glb.clouddn.com/QQ%E6%88%AA%E5%9B%BE20160308220147.png)
之后打开博客的配置文件_config.yml,一般是在最后，修改为以下代码，需要注意的是：后面要加空格
```
deploy:
  type: git
  repo: git@github.com:saltleaves/saltleaves.github.io.git
  branch: master
```
### 推送到github
```
$ hexo g
$ hexo d
```     
运行之后，我们就可以打开自己的网页查看了，网页名字即xxx.github.io(xxx为帐户名)      
## 跟说好的不一样呢
问题：右键菜单中没有 git bash 选项
> * 进入开始菜单找到 git bash ，然后通过 cd 进入相应目录执行命令。

问题：在github部署完成之后，马上访问可能出现404错误
> * 等待10分钟左右，查看邮箱是否有验证邮件

问题：配置连接git后，出现error deployer not found:github 的错误
> * 这个问题常常出现在hexo阶段命令行与本文不一样的人，可以尝试使用本文中的方法

