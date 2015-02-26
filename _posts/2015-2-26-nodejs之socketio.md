---
layout: post
title: Nodejs之初始socket.io(3)
categories: 
- 技术
tags:
- nodejs
---

##简介

###Websocket
[Websocket](http://en.wikipedia.org/wiki/WebSocket)是一种通信的协议。通过这种协议，浏览器和服务器之间的连接可以持久打开。这突破了HTTP协议无连接，无状态的限制(无连接：无连接的含义是限制每次连接只处理一个请求。服务器处理完客户的请求，并收到客户的应答后，即断开连接。无状态：指协议对于事务处理没有记忆能力)。由于连接持久打开，使得web服务器和服务器之间可以快速，双向交换数据。

###Socket.io
[Socket.io](http://socket.io/)是nodejs的一个模块，它提供了通过Websocket进行通信的一种简单方式。它提供了服务器和客户端双方的组件，并且解决了浏览器支持的问题，使得构建实时通信应用程序变得十分简单。

##最简单的使用方式

> 监听客户链接和断开事件。（代码在cloud9上测试通过）

假设已经安装好了socket.io模块，服务端代码可以这样写：

	//服务端代码
	var http = require('http'),
	  fs = require('fs');
	//创建server对象，提供html文档
	var server = http.createServer(function (req, res) {
	  fs.readFile('./index.html', function(error, data) {
	    res.writeHead(200, { 'Content-Type': 'text/html' });
	    res.end(data, 'utf-8');
	  });
	})
	//监听端口
	server.listen(process.env.PORT || 3000, process.env.IP || "0.0.0.0", function(){
	  var addr = server.address();
	  console.log("Server listening at", addr.address + ":" + addr.port);
	});
	//将Socket.io绑定在服务器上
	var io = require('socket.io').listen(server);
	//通过io.sockets对象的on()函数，监听'connection'事件，并且附上回调函数用以监听'disconnect'事件
	io.sockets.on('connection', function (socket) {
	  console.log('User connected');
	  socket.on('disconnect', function () {
	    console.log('User disconnected');
	  });
	});

客户端代码，在index.html中添加如下代码即可连接到服务器：

	<script src="/socket.io/socket.io.js"></script>
	<script>
	    var socket = io.connect('监听的网址及端口号');
	</script>

##理解代码

###服务端
在本例中，server监听端口，socket.io监听server，而事实上，socket.io 也可单独工作。

`var io = ...` 这一行，请求了socket.io 模块，并将其附加到服务器上；

`io.sockets.on()`函数用以监听各种事件，这里监听了客户端的`connection` 事件。

###客户端
*第一行将socket.io 库包含进来；当客户端网页来自同一服务器，只要有这一行，socket.io库会自动为你提供包括连接，发送/接收消息所需的所有代码。*(Really?? not sure。。)

`var socket = io.connect()` 用以将网页与服务器连接起来，而该事件可以被服务器监听到。
