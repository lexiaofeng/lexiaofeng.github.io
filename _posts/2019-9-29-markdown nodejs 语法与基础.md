---
layout: post
title: node js
tags: 基础
stickie: true
---

## 实例

```
//搭建nodejs web服务器

//引入http模块
var http = require('http');

var hostname ='127.0.0.1';
var port = 3000;

//创建服务器
//req 表示请求(request) / res 表示响应 (response)
var server = http.createServer(function(req,res){
    //设置http头信息 文件类型是html；字符集 UTF8
    <font color=#FF0000 >res.setHeader("Content-Type" , "text/html;charset=UTF8");</font> 
   res.end('hi  这是我的第一次');
});

//运行服务器
server.listen(port,hostname,function(){
    console.log(`请访问：http://${hostname}:${port}`);
});
```



