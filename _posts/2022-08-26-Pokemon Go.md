---
layout:     post
title:      Pokemon Go 狩猎ToolsBox
subtitle:   狩猎专帖，可以在这里下载到最新版本的狩猎与源工程文件。
date:       2022-08-26
author:     DeSoiat
header-img: img/post-bg-swift2.jpg
catalog: true
tags: 
    - Pokemon Go
    - Auto JS
---


# you-get 安装&使用

You-Get 是一个微型命令行实用程序，用于从 Web 下载媒体内容（视频、音频、图像）


# 安装


第一步 

从Python官网下载Python 

https://www.python.org/downloads/

---
第二步

安装Python 

![picture1](/img/youget/1.jpg)

在点击 Install Now 之前一定要勾选 Add Python 3.xx to PATH 不然CMD会报这样的错误

```bash
'python' 不是内部或外部命令，也不是可运行的程序
或批处理文件。
```
---
第三步

在安装Python之后 我们可以通过 CMD 来查看python 是否正确安装

Win + R

打开运行窗口后输入

cmd

在CMD 窗口中 我们可以输入

```bash
python --version
```
如果正确安装那么CMD就会返回当前python的版本型号。

![picture2](/img/youget/2.jpg)

---
第四步

我们现在可以通过Python来安装you-get了

在CMD中输入

```bash
pip install you-get
```

等待片刻后CMD就会提示安装完成

---
第五步

我们需要安装FFMPEG 用来自动合并下载后的视频和音频

下载 [FFMPEG](https://github.com/DeSoiat/DESOIAT.GITHUB.IO/raw/main/download/ffmpeg.rar)

之后解压到C盘根目录

---
第六步

window + s 键打开搜索栏

输入 ``` system variables ``` 点击 编辑系统环境变量 -> 环境变量 -> 在用户变量栏下 点击PATH -> 点击编辑 -> 点击新建 -> 输入 ``` C:\ffmpeg\bin ``` -> 点击确定

---
第七步

打开CMD 输入 ffmpeg -version 确定是否安装成功

成功安装的FFMPEG

![picture3](/img/youget/3.PNG)
