---
title: 阿里云课程之API请求与认证
date: 2020-09-15 09:20:37
tags:
- API
top_img: https://wx1.sbimg.cn/2020/09/15/9VYb6.png
cover: https://wx1.sbimg.cn/2020/09/15/9VYb6.png
copyright_author: 李瑞
copyright_author_href: https://lirui-1997.github.io/
copyright_info: 本博客所有文章除特别声明外，均采用  <a href="https://creativecommons.org/licenses/by-nc-sa/4.0/">CC BY-NC-SA 4.0 </a> 许可协议。转载请注明出处！
---

## Web API 协议及 HTTP 请求

### Web API 协议

Web API 一般采用 HTTP 作为底层协议，HTTP 请求机制如下：
- 客户端向服务器发送一个请求
- 服务端给客户端一个响应，告诉客户端是否可以完成它请求的工作

![image-20200915092401128.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/API请求与认证/image-20200915092401128.png)

### HTTP 请求包含的内容

为了构造有效的请求，客户端需要包含四个部分：
- URL（API 调用地址）
- 请求方式
- Header（请求头）
- Body（请求主体）

![image-20200915093412019.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/API请求与认证/image-20200915093412019.png)

## API 请求方式

请求方式告诉服务器客户端希望它采取什么动作。常见的请求方式有四种：
- GET：请求服务器获取一个资源
- POST：请求服务器创建一个新的资源
- PUT：请求服务器编辑或更新一个已存在的资源
- DELETE：请求服务器删除一个资源

请求头（Headers）：提供了请求的元信息，是一个简单的项目列表，其中有客户端发送请求的时间和请求主体大小、身份认证等信息。

请求体（Body）：包含了客户端希望发送给服务器的数据。

## 状态返回码

### 成功状态

当成功调用 API 后，除了返回数据外，还会包含一个状态码，处理成功返回2xx：

|          HTTP 状态码           |                   语义                   |
| :----------------------------: | :--------------------------------------: |
|         200 OK - [GET]         |       服务器成功返回用户请求的数据       |
| 201 CREATED - [POST/PUT/PATCH] |          用户新建或修改数据成功          |
|       202 Accepted - [*]       | 表示一个请求已经进入后台排队（）异步任务 |
|   204 NO CONTENT - [DELETE]    |             用户删除数据成功             |

### 服务端错误码

API 未调用成功，则返回错误码。服务端错误码是5xx，表示服务不可用（此时一般建议重试或联系商品页面的 API 服务商）。

|             错误代码             | HTTP 状态码 |       语义       |                           解决方案                           |
| :------------------------------: | :---------: | :--------------: | :----------------------------------------------------------: |
|          Internet Error          |     500     | API 网关内部错误 |                          建议重试。                          |
| Failed To Invoke Backend Service |     500     |   底层服务错误   | API 提供者底层服务错误，建议重试，如果重试多次仍不可用，可联系 API 服务商解决。 |
|       Service Unavailable        |     503     |    服务不可用    |                        建议稍后重试。                        |
|          Async Service           |     504     |   后端服务超时   |                        建议稍后重试。                        |

### 客户端错误码

客户端错误码为4xx，表示业务报错。此时一般为参数错误、签名错误、请求方式有误或被流控限制等业务类错误，建议详细查看错误码，针对性解决问题。

参考：错误代码表 https://help.aliyun.com/document_detail/43906.html

*注意：有些 API 自定义了错误码，具体请查看该 API 文档中的描述。*

## API 数据格式

![image-20200915095925547.png](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/API请求与认证/image-20200915095925547.png)

目前最新的 API 大多数使用 JSON 数据格式。JSON（JavaScript Object Notation）是一种轻量级的数据交换格式，采用完全独立于语言的文本格式，易于人阅读和编写，同时也易于机器解析和生成，是一种理想的数据交换语言。

**JSON** 数据格式表示方法

1. 表示对象

JSON 最常用的格式是对象的键值对。

```JSON
{"name":"黑龙江"，"city":"哈尔滨"}
```

2. 表示数组

和普通的 JS 数组一样，JSON 表示数组的方式是使用方括号 []。
```JSON
{
	"name":"中国"
	"province":[{
		"name":"黑龙江"
		"city":"哈尔滨"
	},{
		"name":"广东"
		"city":"广州"
	}]
}
```

## API 身份认证及签名认证

### API 简单身份认证（APPCODE 方式）

可以通过 APPCODE 的方式，实现到被调用接口的身份认证，获取访问相关 API 的调用权限。使用方法：
- 请求 Header 中添加的 Authorization 字段；
- 配置 Authorization 字段的值为 “APPCODE + 半角空格 + APPCODE值”。

格式：
- Authorization:APPCODE AppCode值

示例：
- Authorization:APPCODE 3F2504E04F8911D39A0C0305E82C3301

### API 签名认证（AppKey & AppSecret）

AppKey 和 AppSecret 相当于当前账户的另一套账号和密码机制。在云市场购买API之后，就可以在控制台找到对应的 AppKey 和 AppSecret 。

![image-20200915102508920.png)](https://cdn.jsdelivr.net/gh/LiRui-1997/hexo/image/API请求与认证/image-20200915102508920.png))

具体签名认证方法请参见**请求头部字段**以及**请求签名说明文档**。











