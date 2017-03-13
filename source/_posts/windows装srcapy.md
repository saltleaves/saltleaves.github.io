---
title: windows装scrapy步骤记录
date: 
tags: [python]
---

### 安装python

根据你的需求下载python安装包，安装python（本文基于python27）[下载地址](https://www.python.org/downloads/)
特别要注意选上pip和Add python.exe to Path，然后一路点“Next”即可完成安装。否则需要自己配环境变量,在 环境变量---"Path"中加入路径："安装目录/python27/;安装目录/python27/Scripts;"
在运行中输入"cmd"打开命令窗口，输入"python --version"，如果成功显示python版本号，则python安装成功！如果未显示，则重启计算机！　　

### 安装pywin32

根据需要下载相应的pywin32安装包 [下载地址](https://sourceforge.net/projects/pywin32/files/pywin32/Build%20217/)

### 安装pip

一般为python默认安装好的，在"安装目录/python27/Scripts"目录中有"pip.exe"则默认安装成功；
若python未默认安装，在 https://pip.pypa.io/en/latest/installing/ 下载"get-pip.py"的python程序
在运行中输入"cmd"打开命令窗口，输入"python get-pip.py"即可自动安装。
若你的用户名为中文导致安装出错，则在python安装目录"安装目录/python27/Lib/site-packages"中添加一个文本文件，命名为"sitecumtomize.py"，打开往文件内输入

```
1 import sys 
2 sys.setdefaultencoding('gd2312') 
```

保存关闭。
重启cmd命令窗口，输入"pip --version"，若显示pip版本号，则安装成功！

### 安装lxml
若系统未安装vs2008，则安装lxml 前，先安装vcforpython27 [下载地址](https://www.microsoft.com/en-us/download/details.aspx?id=44266。)
然后在安装lxml，[下载地址]( https://pypi.python.org/pypi/lxml/3.6.0#downloads )，下载lxml for 2.7，下载安装。
 
### 安装pyOpenSSL

重启cmd命令窗口，用pip安装openSSL，输入命令"pip install pyOpenSSL"
 
### 安装scrapy

准备工作完成，安装scrapy。重启cmd命令窗口，用pip安装openSSL，输入命令"pip install scrapy"
等待自动安装，安装完成后输入"scrapy"，提示scrapy的命令提示内容，则整个安装过程结束。