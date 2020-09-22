---
title: 阿里云课程之API调试与调用
date: 2020-09-15 11:02:20
tags:
- API
top_img: https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/封面/微信图片_20200922105439.png
cover: https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/封面/微信图片_20200922105434.png
copyright_author: 李瑞
copyright_author_href: https://lirui-1997.github.io/
copyright_info: 本博客所有文章除特别声明外，均采用  <a href="https://creativecommons.org/licenses/by-nc-sa/4.0/">CC BY-NC-SA 4.0 </a> 许可协议。转载请注明出处！
---

## API 调试

阿里云 API 市场提供了在线调试功能，以便用户在不用写调用代码的前提下进行快速测试。

![image-20200915110550037.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/API调试与调用/image-20200915110550037.png)

![image-20200915110630847.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/API调试与调用/image-20200915110630847.png)

## API 调用步骤

![image-20200915110711621.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/API调试与调用/image-20200915110711621.png)

要条用 API 需要三个基础条件：
- API：您即将要调用的 API ，明确 API 参数定义；
- 应用 app：作为您调用 API 时的身份，有 AppKey 和 AppSecret 用于验证您的身份；
- API 和 App 的权限关系：App 想调用某个 API 需要具有该 API 的权限，这个权限通过授权的功能来建立。

### 获取 API 文档

- 在云市场选择 API ，在 API 产品页面下即可找到该 API 的使用说明（文档）
- 购买 API 服务成功后，进入云市场的管理控制台，就会看见购买的所有 API 服务。（如果还没有开通 API 网关服务，则会同时开通）
- 可以跳转到 API 网关的控制台，在已购买 API 页面，展示购买的所有 API 服务列表，以及使用情况概况。

![image-20200915111437549.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/API调试与调用/image-20200915111437549.png)

### 创建应用

- 应用（APP）是调用 API 服务时的身份。每个 APP 有一组 Key 和 Secret，可以理解为账号密码，调用 API 的时候需要将 AppKey 做参数传入，AppSecret 用于签名计算，网关会校验这对秘钥对你进行身份认证
- 可以在 API 网关控制台**应用管理**页面创建 APP ，创建成功后，系统会为 APP 分配一对 AppKey 和 AppSecret。

![image-20200915111621047.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/API调试与调用/image-20200915111621047.png)

### 获得授权

- 授权，是指授权 APP 调用某个 API 的权限。您的 APP 需要获得 API 的授权才能调用该 API。
- 如果你在市场购买了 API ，就可以指定将已购买的 API 授权给哪些 APP，然后这些 APP 才能调用该 API。
- 如果您没有 APP，购买时云市场会为您创建一个 APP，并且授权。

![image-20200915112231907.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/API调试与调用/image-20200915112231907.png)

### 调用 API

- 可以直接用 API 文档中提供的多语言调用示例来调用，如下图所示；
- 也可以自行编辑 HTTP(s)请求来调用 API。

![image-20200915112435699.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/API调试与调用/image-20200915112435699.png)

## API 调用注意事项

- 每个账号下 APP 个数上限为10个，APP 名称应为账号下唯一；
- 调用 API 的流控限制为，单个 IP，QPS 不超过100；
- 您有权操作购买的 API 与 APP 的授权和解除授权。由于服务提供方授权给你的 APP 的 API，你无权操作结束授权；
- 你的请求需要包含签名信息，请参照阿里云相关文档。