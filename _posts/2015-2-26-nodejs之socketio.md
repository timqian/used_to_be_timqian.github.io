---
layout: post
title: Nodejs之socket.io(3)
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
