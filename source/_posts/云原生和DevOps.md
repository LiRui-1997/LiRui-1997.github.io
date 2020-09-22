---
title: 阿里云DevOps之云原生和DevOps
date: 2020-09-11 09:15:22
tags:
- 云原生
- 容器
- 微服务
- DevOps
- CI/CD
top_img: https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/封面/微信图片_20200922105439.png
cover: https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/封面/111.png
copyright_author: 李瑞
copyright_author_href: https://lirui-1997.github.io/
copyright_info: 本博客所有文章除特别声明外，均采用  <a href="https://creativecommons.org/licenses/by-nc-sa/4.0/">CC BY-NC-SA 4.0 </a> 许可协议。转载请注明出处！
---

## 云原生的基本概念

### 云原生的定义

>“云原生技术有利于各组织在公有云、私有云和混合云等新型动态环境中，构建和运行可弹性扩展的应用。云原生的代表技术包括容器、服务网格、微服务、不可变基础设施和声明式API。”
>-- 引自 Cloud Native Computing Foundation homepage https://www.cncf.io
>

- 云原生的定义一直在变
	- 不同组织有不同的定义：Pivotal & CNCF
	- 同一个组织在不同时间点有不同的定义
	- 同一个人在不同时间点也有不同的定义
- 云原生的定义未来还会变
	- CNCF 最新定义：版本V1.0

![image-20200831173938870.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/云原生和DevOps/image-20200911092316230.png)

### 云原生的服务模型

![image-20200911092602328.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/云原生和DevOps/image-20200911092602328.png)

### 云原生应用的关注点

![image-20200911092655761.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/云原生和DevOps/image-20200911092655761.png)

## 微服务

微服务架构演进：

![image-20200911092754680.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/云原生和DevOps/image-20200911092754680.png)

微服务架构带来很多好处：
- 独立的可扩展性：每个微服务都可以独立进行横向或纵向扩展，根据业务员实际增长情况来进行快速扩展；
- 独立的可升级性：每个微服务都可以独立进行服务升级、更新，不用依赖于其他服务，结合持续集成工具可以进行持续发布，开发人员就可以独立快速完成服务升级发布流程；
- 语言无关性：研发人员可以选用自己最为熟悉的语言和框架来完成他们的微服务项目；
- 故障和资源的隔离性：在系统中出现不好的资源操作行为时，将仅仅只会影响单个微服务。

微服务带来的挑战：
- 分布式系统的复杂性
	- API数目成倍增加
	- 调试分布式系统很复杂
	- 跨服务的重构会很困难
	- 很难在测试中重建和生产环境一致的环境
- 微服务的运维开销更大
	- 多个服务需要多种编译语言运行环境
	- 多个服务需要集群来处理故障转移，负载均衡
	- 需要高质量地服务监控和运维基础设施
	- 对健壮和自动化的部署要求更高
- 对团队的要求更高
	- 组织结构需要转型到自治的，跨功能的团队
	- 团队的技术能力，技术栈需要扩展
	- 要求团队更高的DevOps水平

## 容器

与系统其它部分隔离开的一些列进程。

容器提供了一种逻辑打包机制，以这种机制打包的应用可以脱离其实际运行的环境。

![image-20200911093933515.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/云原生和DevOps/image-20200911093933515.png)

![image-20200911094028496.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/云原生和DevOps/image-20200911094028496.png)

## CI/CD 及 DevOps

CI：Continuous Integration 持续集成
CD：Continuous Deployment 持续部署
DevOps从字面上直观理解：开发运维一体化

![image-20200911094337798.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/云原生和DevOps/image-20200911094337798.png)

### CI 持续集成流程

持续集成指的是：
1. 开发人员频繁地向代码库提交代码
2. 提交的代码需要经过构建、测试验证并及时得到结果反馈

![image-20200911094542604.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/云原生和DevOps/image-20200911094542604.png)

### CD 持续部署/持续交付

CD Continuous Deployment 持续部署的主要目标：
- 持续部署是持续集成的延伸，将集成后的代码部署到生产环境；
- 频繁部署确保可以小批次发布，在发布问题时可以轻松排除故障。

![image-20200911094853882.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/云原生和DevOps/image-20200911094853882.png)

### DevOps 的定义

维基百科：是一组过程、方法和系统的统称，用于促进开发（应用程序/软件工程）、技术运营和质量保障（QA）部门之间的沟通、协作与整合。

DevOps 经常被描述为“开发团队与运营团队之间更具协作性、更高效的关系”。

![image-20200911095222552.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/云原生和DevOps/image-20200911095222552.png)

### 阿里DevOps策略：打造一站式DevOps效能平台交付流水线

![image-20200911095329113.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/云原生和DevOps/image-20200911095329113.png)






