---
layout:     post
title:      整理下在GOODNIGHTGUI中遇到的问题与解决方法
subtitle:   整理下在GOODNIGHTGUI中遇到的问题与解决方法
date:       2022-01-10
author:     DeSoiat
header-img: img/jpg/11.jpg
catalog: true
tags: 
    - JAVA
    - CSS
---


# Issues 1 ：创建TextArea 后尝试加入到Root提示 require type “Node”  Provided “TextArea”

个人解决方法 添加 javafx.scene.control.TextArea

```
javafx.scene.control.TextArea textArea1 = new javafx.scene.control.TextArea();
```


---

# Issues 2 ：尝试添加CSS 提示找不到文件

尝试过以下代码很好用（本地）但是一但打包成JAR 就无法正常工作
```
File css = new File("resources/style.css");
spreadsheet.getStylesheets().add("file:///" + css.getAbsolutePath().replace("\\", "/"));
```

也尝试过这个代码同样会出现error
```
scene.getStylesheets().add(getClass().getResource("/stylesheet.css").toExternalForm())
```

最后解决方法是 将本地css上传至网络库后使用URL访问 优点是 稳定 易更新 缺点是程序需要联网
```
String guiCss = "https://raw.githubusercontent.com/DeSoiat/GoodNightGUI/main/src/main/resources/com/desoiat/goodnightgui/css/gui.css";
play.getStylesheets().add(guiCss);
```

# Issues 3 ：尝试为root添加背景图

遇到跟css一样的问题路径识别失败 我需要重新读一次IO了
解决方法 更改图片为URL链接
```
JAVA部分
root.setId("stack-pane");
root.getStylesheets().add(guiCss);

css部分
#stack-pane{
    -fx-background-image: url("https://github.com/DeSoiat/DESOIAT.GITHUB.IO/blob/main/img/jpg/25.jpg?raw=true");
    -fx-background-repeat: no-repeat;
    -fx-background-position: center center;
}
```

# Issues 4 ：将毫秒转换为 小时，分，秒格式

解决代码

```
public static void convertMillis(int Millis){
        String convert = String.format("预计需要 %d 小时, %d 分, and %d 秒",

                Millis/(1000*60*60), (Millis%(1000*60*60))/(1000*60), ((Millis%(1000*60*60))%(1000*60))/1000);

        System.out.println(convert);
    }
 ```
 
# Issues 5 ：按键并发

最初设计是一个设定按钮 一个开始按钮 后来通过测试发现点击设定按钮也会触发播放 但是设定按钮是必要的所以 解决方法保留 设定按钮功能 取消其GUI显示 通过开始按钮来触发设定。

# Issues 6 ：javafx 无法打包成JAR

尝试打包 提示 Can't build artifact - fx:deploy is not available in this JDK

解决方法 建立一个新CLASS 取名为 mian 或者 main2 从新class 触发 主class 原因视乎javafx 不太喜欢extend

```
package com.desoiat.goodnightgui;

public class main {
    public static void main(String[] args) {
        goodNightGUI.main(args);
    }
}
```
之后 选择 fiel -> project structure -> Artifacts -> add -> jar -> from modules -> 选择新建的MAIN class 创建之后还需呀导入JAVAFX 所需的DLL文件可以从javafx bin文件中获得 之后按正常流程 bulid artifacts 就可以。

# Issues 7 ：JAVAFX 使用 Thread.sleep(totalTime);

JAVAFX 使用 Thread.sleep(totalTime); 会导致整个GUI陷入冻结状态 目前仍在解决 个人想法是创建个新线程 然后需要sleep的线程与GUI分开







