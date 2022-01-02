---
layout:     post
title:      Git LFS的使用
subtitle:   使用Git LFS上传大于25MB的文件至GITHUB库
date:       2022-01-02
author:     DeSoiat
header-img: img/jpg/11.jpg
catalog: true
tags: 
    - Git
    - CMD
    - Github
---


# 前置需求

[Git](https://github.com/DeSoiat/DESOIAT.GITHUB.IO/raw/main/download/Git-2.34.1-64-bit.exe)

[Git Large File Storage](https://github.com/DeSoiat/DESOIAT.GITHUB.IO/raw/main/download/git-lfs-windows-v3.0.2.exe)

[GitHub Desktop (可选）](https://github.com/DeSoiat/DESOIAT.GITHUB.IO/raw/main/download/GitHubDesktopSetup-x64.exe)

---

# Git 配置

CMD中配置 GIT的 用户名与邮箱

```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"

```
# 克隆库到本地

可以使用 Github desktop 直接克隆到本地

或者使用 GIT clone 命令行克隆

甚至你可以进入网页的GITHUB仓库 下载zip


# Git LFS使用流程

我已经提前在根目录中 创建了 download 文件夹 并且放入了我想上传的文件

第一步

先CD 到目标文件的根目录下 后输入 git status 检查一下

```
CD C:\Users\DeSoiat\Documents\GitHub\DESOIAT.GITHUB.IO
git status
```
![picture1](/img/gitlfs/1.PNG)

第二步

对目录安装 git lfs

```
git lfs install
```
![picture2](/img/gitlfs/2.PNG)



第三步

添加文件类型跟踪  git lfs track "*.文件后缀"

```
git lfs track "*.exe"
git lfs track "*.7z"
git lfs track "*.rar"
git lfs track "*.iso"
git lfs track "*.zip"
git lfs track "*.doc"
git lfs track "*.txt"
git lfs track "*.jpg"
git lfs track "*.png"
```
![picture3](/img/gitlfs/3.PNG)

第四步

添加 文件夹 之后 再次查看状态

```
git add download/*
git status
```
![picture4](/img/gitlfs/4.PNG)


第五步 

添加 .gitattributes

```
git add .gitattributes
```
再次 查看状态

![picture5](/img/gitlfs/5.PNG)



第六步

commit

```
 git commit -m “description”
 ```
 
 ![picture6](/img/gitlfs/6.PNG)
 
第七步

更新上传至仓库

```
git push origin
```
如果遇到 这个报错 那就需要第八步

![picture7](/img/gitlfs/7.PNG)

第八步

更新本地仓库

```
git pull
```
然后再次上传

```
git push
```
![picture8](/img/gitlfs/8.PNG)

最后我们就可以去仓库中查看文件了

![picture9](/img/gitlfs/9.PNG)


 
 











