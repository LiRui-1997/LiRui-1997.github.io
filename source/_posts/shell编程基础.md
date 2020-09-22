---
title: DevOps日记之shell编程基础
date: 2020-09-18 09:11:55
tags:
top_img: https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/封面/微信图片_20200922105439.png
cover: https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/封面/微信图片_20200922105439.png
copyright_author: 李瑞
copyright_author_href: https://lirui-1997.github.io/
copyright_info: 本博客所有文章除特别声明外，均采用  <a href="https://creativecommons.org/licenses/by-nc-sa/4.0/">CC BY-NC-SA 4.0 </a> 许可协议。转载请注明出处！
---

![image-20200916093916154.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/Git的使用/image-20200916093916154.png)

## 编程基础

- 程序：指令+数据
- 程序编程风格
	- 过程式：以指令为中心，数据服务于指令
	- 对象式：以数据为中心，指令服务于数据
- shell程序：提供了编程能力，解释执行
- 编程逻辑处理方式：
	- 顺序执行
	- 循环执行
	- 选择执行
- shell编程：过程式、解释执行
	- 编程语言的基本结构：
		- 各种系统命令的组合
		- 数据存储：变量、数组
		- 表达式：a + b
		- 语句：if
- shell脚本：包含一些命令或声明，并符合一定格式的文本文件
- 格式要求：首行shebang机制
	- #!/bin/bash
	- #!/usr/bin/python
	- #!/sur/bin/perl
- shell脚本的用途：
	- 自动化常用命令
	- 执行系统管理和故障排除
	- 创建简单的应用程序
	- 处理文本或文件

## 脚本基本格式

- 脚本的基本结构
```shell
#!shebang
configuration_variables
function_definitions
main_code
```

## 变量

## 运算

## 条件测试

## 配置用户环境