---
layout: default
title: 程序员必备技能：翻墙
description: 不会翻墙的程序员不是一个好司机
category: 技术分享
---

## 什么是“墙”

墙指的就是
> 防火长城（英语：Great Firewall of China，常用简称：GFW，中文也称中国国家防火墙，中国大陆民众俗称防火墙等），是对中华人民共和国政府在其互联网边界审查系统（包括相关行政审查系统）的统称。--[维基百科](https://zh.wikipedia.org/wiki/%E9%98%B2%E7%81%AB%E9%95%BF%E5%9F%8E)

然后这个墙有一个[过滤网站列表](https://zh.wikipedia.org/wiki/%E4%B8%AD%E5%8D%8E%E4%BA%BA%E6%B0%91%E5%85%B1%E5%92%8C%E5%9B%BD%E8%A2%AB%E5%B0%81%E9%94%81%E7%BD%91%E7%AB%99%E5%88%97%E8%A1%A8)凡是在这个列表中的网站，正常情况下是不能访问的。

当然了，google，YouTube，Facebook，Twitter也都在这个列表中。github曾经也进去过，后来又出来了。。。

## 什么是翻墙

翻墙有一个高大上的名字叫[突破网络审查](https://zh.wikipedia.org/wiki/%E7%AA%81%E7%A0%B4%E7%BD%91%E7%BB%9C%E5%AE%A1%E6%9F%A5)，就是利用境外未封锁代理服务器或者伪装访问链接的手段来绕过长城防火墙。

我们今天要介绍的[xxnet](https://github.com/XX-net/XX-Net)就是利用google app engine作为代理服务器来绕过长城防火墙。

在介绍xxnet之前，先介绍下GoAgent，因为xxnet就是在GoAgent的技术上进行封装，增加图形化界面，提升用户体验的。

## GoAgent

> GoAgent是使用跨平台语言Python开发、基于GPL自由软件协议的代理软件。它利用Google App Engine（GAE）的服务器充当代理。该软件在中国大陆被广泛用于突破大陆官方创建的防火长城（GFW），以浏览被封锁的内容。--[维基百科](https://zh.wikipedia.org/wiki/GoAgent)

GoAgent的运行原理与其他代理工具基本相同，使用特定的中转服务器完成数据传输。它使用Google App Engine的服务器作为中传，将数据包后发送至Google服务器，再由Google服务器转发至目的服务器，接收数据时方法也类似。由于服务器端软件基本相同，该中转服务器既可以是用户自行架设的服务器，也可以是由其他人架设的开放服务器。

基于GoAgent的派生项目有很多，xxnet就是其中一个，xxnet使用起来很方便，有两种模式

- 全局代理 即所有访问通过gae的IP进行代理访问
- 智能代理 即根据所访问的网站是否被封锁，被封锁的通过gae代理访问，否则正常访问

## XX-NET

这是官方的[使用文档](https://github.com/XX-net/XX-Net/wiki/How-to-use)

在这重点讲一下 如何创建自己的google appid，从而更快更方便使用xxnet

**每个google appid的流量为每24小时1G流量，每人可申请8个google appid，这对于一般程序员来说足够使用了**

### 登录Google帐户

[https://accounts.google.com](https://accounts.google.com) (没有账号，请自行注册)

![google_account.jpg](https://suchao2007.github.io/assets/article_img/google_account.jpg)

> 如果不能访问google，请先使用开放appid

### 创建AppID

- 打开[https://console.developers.google.com](https://console.developers.google.com) ，左击顶部Project，然后左击创建项目

![create_google_appid.jpg](https://suchao2007.github.io/assets/article_img/create_google_appid.jpg)

- 输入项目名称后，会自动帮你匹配可用ID，然后左击建立

![create_google_appid_2.jpg](https://suchao2007.github.io/assets/article_img/create_google_appid_2.jpg)

**生成的项目ID就是之后要用的appid**

### 部署服务端

- 打开XX-Net的设置页：[http://127.0.0.1:8085](http://127.0.0.1:8085) ，切换到部署服务端

![setup_server.jpg](https://suchao2007.github.io/assets/article_img/setup_server.jpg)

- 弹出授权窗口时，点击Allow，然后就会进行服务端的部署

- 部署完成后，切换到配置，输入部署好的AppID后点击保存

- 切换到状态来确认状态

![proxy_status.jpg](https://suchao2007.github.io/assets/article_img/proxy_status.jpg)

**至此，你就可以自由的上天了。。。**

推荐一首 电影《被解救的姜戈》插曲《freedom》，feel good！