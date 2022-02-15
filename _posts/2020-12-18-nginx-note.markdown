---
layout: default
title:  "Nginx相关知识笔记"
date:   2020-12-18 15:02:21 +0800
categories: notes
excerpt: 一些Nginx配置项的备忘录
---
#### 1.worker_processes： 
worker的数量。该数值与CPU数量相等最适宜，大于CPU数量会造成上下文切换消耗，小于CPU数量则无法完全利用CPU资源。  

#### 2.worker_connections:
一个worker的连接数量。一次请求占用的连接数为2个(静态资源访问）或者4个（反向代理）。  
静态资源访问：客户端请求Nginx(占用1个连接数)，worker返回给客户端（占用1个连接数），__共2个连接数__ 。  
反向代理：客户端请求Nginx(占用1个连接数)，worker请求php-fpm或其他服务器，并接收它们的返回（占用2个连接数），worker返回给客户端（占用1个连接数），__共4个连接数__。  

#### 3.Nginx的最大并发数：
假设NGINX有4个worker进程，每个worker支持最大连接数为1024。  
静态资源访问的最大并发数=`worker_processes*worker_connections/2 = 4*1024/2 = 2048`  
静态资源访问的最大并发数=`worker_processes*worker_connections/4 = 4*1024/4 = 1024`
