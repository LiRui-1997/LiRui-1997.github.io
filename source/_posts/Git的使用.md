---
title: DevOps日记之Git的使用
date: 2020-09-16 09:31:38
tags:
- DevOps
- Git
top_img: https://wx1.sbimg.cn/2020/09/11/9YETo.png
cover: https://wx1.sbimg.cn/2020/09/11/9YETo.png
copyright_author: 李瑞
copyright_author_href: https://lirui-1997.github.io/
copyright_info: 本博客所有文章除特别声明外，均采用  <a href="https://creativecommons.org/licenses/by-nc-sa/4.0/">CC BY-NC-SA 4.0 </a> 许可协议。转载请注明出处！
---

## 本地仓库

### 工作流程

Git 本地操作的三个区域：
- Git Repository（Git 仓库）：最终确定的文件保存到仓库，成为一个新的版本，并且对他人可见；
- 暂存区：暂存已经修改的文件最后统一提交到 git 仓库中；
- 工作区（Working Directory）：添加、编辑、修改文件等动作。

![image-20200916093916154.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/Git的使用/image-20200916093916154.png)

### 本地仓库操作

仓库又名版本库，英文名 repository ，可以简单理解成是一个目录，用于存放代码的，这个目录里面的所有文件都可以被 Git 管理起来，每个文件的修改、删除等操作 Git 都能跟踪到。

1. 首次使用 git 需要

```shell
$ git config --global user.name "用户名"
$ git config --global user.email "邮箱地址"
```

2. 创建仓库

注意：为避免出现意料之外的错误，请不要使用包含中文的目录名作为仓库（父目录亦是如此）

- 创建空目录

```shell
$ mkdir repository
```

- 在命令行中进入项目目录 repository

```shell
$ cd repository
```

- Git 仓库初始化（让 Git 知道它需要来管理这个目录）

```shell
$ git init
```
执行后会在项目目录下创建 “.git” 的隐藏目录，这个目录是 Git 创建的，不能删除，也不能随意更改其中的内容。

3. Git 常用指令操作

- 查看当前状态：git status
- 添加到缓存区：git add 文件名
	- 说明：git add 指令，可以添加一个文件，也可以同时添加多个文件
	- 语法1：```git add 文件名```
	- 语法2：```git add 文件名1 文件名2 文件名3 ...```
	- 语法3：```git add .```  添加当前目录至缓存区
- 提交至版本库：git commit -m “注释内容”
- 对于后续要提交的文件，重复使用 git add 与 git commit 指令即可

### 版本回退

版本回退分为两步进行：
1. 查看版本：确定需要回到的时刻点
```shell
$ git log
$ git log --prety=oneline
```
2. 回退操作
```shell
$ git reset --hard 提交编号
```
注意：版本回退后，如果想再回到之前最新的版本，则需要使用指令去查看历史操作，以得到最新的 commit id 。
```shell
$ git reflog
```

## 远程仓库

### 创建远程仓库

线上仓库的创建以 Github 为例。

### 两种常规使用方式

#### 基于 http 协议
- 创建一个空目录并进入
- 使用 clone 指令克隆线上仓库至本地

```shell
$ git clone http协议的线上仓库地址
```

- 在仓库上做对应的操作（提交暂存区、提交本地仓库、提交线上仓库、拉取线上仓库）

```shell
$ git push
$ git pull
```
在首次往线上仓库提交内容的时候出现了 403 的致命错误，因为不是所有人都可以往线上仓库提交内容，必须先鉴权。修改 “.git/config” 文件内容：
```
# 将
[remote "origin"]
	url = https://github.com/用户名/仓库名.git
修改为：
[remote "origin"]
	url = https://用户名:密码@github.com/用户名/仓库名.git
```

#### 基于 ssh 协议

该方式与前面 https 方式相比，只是影响 github 对于用户的身份鉴权方式，对于 git 的具体操作（如本地提交、添加注释、提交远程等操作）没有任何影响。

- 生成客户端公私钥文件（需先自行安装 OpenSSH）

```
ssh-keygen -t rsa -c "注册邮箱"
```

- 将公钥文件内容（id_rsa.pub）上传到 Github
- 执行后续 git 操作
```shell
$ git clone SSH协议的线上仓库地址
```

### 分支管理

![image-20200916145443724.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/Git的使用/image-20200916145443724.png)

- 查看分支：
```shell
$ git branch    
```

- 创建分支：
```shell
$ git branch 分支名  
```

- 切换分支：
```shell
$ git checkout [-d] 分支名  
```

- 删除分支（先退出要删除的分支）
```shell
$ git branch -d 分支名  
```

- 合并分支
```shell
$ git merge 被合并的分支名 
```

![image-20200916150622912.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/Git的使用/image-20200916150622912.png)

## 忽略文件

忽略文件需要新建一个名为 .gitignore 的文件，该文件用于声明忽略文件或者不忽略文件的规则，规则对当前目录及其子目录生效。

常见规则写法有如下几种：
```
1. /mtk/           # 过滤整个文件夹
2. *.zip           # 过滤所有.zip文件
3. /mtk/do.c       # 过滤某个具体文件
4. !index.php      # 不过滤具体某个文件
```
































