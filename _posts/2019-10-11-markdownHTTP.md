---
layout: post
title: HTTP
tags: 基础
stickie: true
---

# HTTP

## 一、HTTP是什么？

### 1、概述

HTTP 全称是 `HyperText Transfer Protocal`，即：超文本传输协议，从 1990 年开始就在 WWW 上广泛应用，是现今在 WWW 上应用最多的协议，HTTP 是应用层协议，当你上网浏览网页的时候，浏览器和 web 服务器之间就会通过 HTTP 在 Internet 上进行数据的发送和接收。HTTP 是一个基于请求/响应模式的、无状态的协议。即我们通常所说的 Request/Response

####传统上来说TCP/IP被认为是一个四层协议

### 2、特点

- 支持客户端/服务器模式
- 简单快速：客户向服务器请求服务时，只需传送请求方法和路径。由于 HTTP 协议简单，使得 HTTP 服务器的程序规模小，因而通信速度很快
- 灵活：HTTP 允许传输任意类型的数据对象。正在传输的类型由 Content-Type 加以标记
- 无连接：无连接的含义是限制每次链接只处理一个请求。服务器处理完客户的请求，并收到客户的应答后，即断开链接，采用这种方式可以节省传输时间
- 无状态：HTTP 协议是无状态协议。无状态是指协议对于事物处理没有记忆能力。缺少状态意味着如果后续处理需要前面的信息，则它必须重传，这样可能会导致每次连接传送的数据量增大。另一方面，在服务器不需要先前信息时它的应答就比较快

## 

## 二、URL详解

### 1、简介

URL（Uniform Resource Locator）是统一资源定位符的简称，有时候也被俗称为网页地址（网址），如同是网络上的门牌，是因特网上标准的资源的地址

### 2、基本组成

通用的格式：scheme://host[:port#]/path/…/[?query-string][#anchor]


![](/Users/lexiaofeng/Desktop/lexiaofeng.github.io/img/4.jpg.png)





## 三、HTTP之请求篇

HTTP 的请求报文分为三个部分：**请求行**、**请求头**、**请求体**

![](/Users/lexiaofeng/Desktop/lexiaofeng.github.io/img/5.jpg.png)



### 1、请求行

请求行（Request line）分为三个部分：**请求方法**、**请求地址**和**协议版本**

#### 请求方法

HTTP/1.1 协议中共定义了八种方法（也叫“动作”）来以不同的方式操作指定的资源

![](/Users/lexiaofeng/Desktop/lexiaofeng.github.io/img/6.jpg.png)



其中，最常见的是 GET 和 POST 方法，如果是 RESful 接口的话一般会用到 PUT、DELETE、GET、POST（分别对应增删查改），



### 2、请求头

请求头可用于传递一些附加信息，格式为：`键: 值`，注意**冒号后面有一个空格**：

![](/Users/lexiaofeng/Desktop/lexiaofeng.github.io/img/7.jpg.png)

![](/Users/lexiaofeng/Desktop/lexiaofeng.github.io/img/8.jpg.png)

![](/Users/lexiaofeng/Desktop/lexiaofeng.github.io/img/9.jpg.png)



### 请求体

请求体（又叫请求正文）是 post 请求方式中的请求参数，以 key = value 形式进行存储，多个请求参数之间用&连接，如果请求当中请求体，那么在请求头当中的 Content-Length 属性记录的就是该请求体的长度



## 四、HTTP之响应篇

HTTP 响应的格式上除状态行（第一行）与请求报文的请求行不一样之外，其他的就格式而言是一样的，但排除状态行和请求行的区别，从 Header 上还是可以区分出 HTTP 请求和 HTTP 响应的区别的，怎么区别就要看前面的 Header 啦



### 1、响应状态行

#### 状态码

状态码（就是上图中的响应码），如果想查看各种状态码具体的含义，可以看一下这篇文章[HTTP状态码对照表](https://link.juejin.im/?target=http%3A%2F%2Ftool.oschina.net%2Fcommons%3Ftype%3D5)，当然这么多状态码要想全部都记住的话，还是比较困难的。

![](/Users/lexiaofeng/Desktop/lexiaofeng.github.io/img/10.jpg.png)

### 2、响应头

响应头同样可用于传递一些附加信息

![](/Users/lexiaofeng/Desktop/lexiaofeng.github.io/img/11.jpg.png)





### 3、响应体

响应体也就是网页的正文内容，一般在响应头中会用 Content-Length 来明确响应体的长度，便于浏览器接收，对于大数据量的正文信息，也会使用 chunked 的编码方式。