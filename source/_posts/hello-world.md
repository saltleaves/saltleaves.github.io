---
title: windows系统下如何安装git
---
公司是使用Git进行版本控制，今天我准备好好调戏调戏它，顺便记录一下过程。安装包可以去[百度网盘](http://pan.baidu.com/s/1eQNL8Hk)下载。提取密码为：vp2t。当然也可以前往官网下载，这里使用的是2.5.1，64位的版本。

## 准备开始

### 安装过程我的选择如下
![安装过程图一](http://7xrkml.com1.z0.glb.clouddn.com/QQ%E6%88%AA%E5%9B%BE20160305200355.png)
               
![安装过程图二](http://7xrkml.com1.z0.glb.clouddn.com/QQ%E6%88%AA%E5%9B%BE20160305200446.png)

![安装过程图三](http://7xrkml.com1.z0.glb.clouddn.com/QQ%E6%88%AA%E5%9B%BE20160305200507.png)

对于上诉的选择有疑惑的只有第三章图：
 - 第一个选项:如果是跨平台项目.在windows系统安装.选择, 
 - 第二个选项:如果是跨平台项目.在Unix系统安装.选择, 
 - 第三个选项:非跨平台项目.选择.

### 检查本地是否曾经安装过git

```
   $ cd ~/. ssh
```

 如果提示：No such file or directory 说明你是第一次使用git;如果不是第一次使用，请执行下面的操作，清理原有的SSH密钥。

```
   $ mkdir key_backup
   $ cp id_rsa* key_backup
   $ rm id_rsa* 
```

### 第一次设置git

 - 填写自己的用户名（即托管代码时的用户名） 
```
$ git config --global user.name "yourname"
```

 - 填写自己的邮箱
```
$ git config --global user.email "yourmaill@yourmaili.com" 
```

### 生成密钥

```
ssh-keygen –t rsa –C “yourmaill@yourmaili.com”
```

打开本地的.ssh/id_rsa.pub，此文件里面内容为刚才生成人密钥。可以复制里面的内容到托管项目网站，添加SSH
