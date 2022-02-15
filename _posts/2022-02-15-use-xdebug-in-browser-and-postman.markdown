---
layout: default
title:  "PhpStorm 配置Xdebug 调试在浏览器和 Postman 中发起的请求"
date:   2022-02-15 10:36:50 +0800
categories: notes
---

### 安装 Xdebug

先查看是否已安装了 Xdebug 模块

```
➜  ~ php -m | grep xdebug
xdebug // 如果没有显示，就是未安装
```

如果没有安装的话，使用 pecl 安装 xdebug

```
➜  ~ pecl install xdebug
```

在`php.ini`中，添加如下配置

```
zend_extension="xdebug.so"
xdebug.mode=debug
xdebug.idekey = "phpstorm"
```

### 配置 PhpStorm

在 PhpStorm 中（我的版本是2021.3.2，其他版本选项可能略有不同）打开设置面板，在`PHP->调试`中启用`PHP 调试连接侦听`，然后点击`验证 Web 服务器上的调试器配置`，如果验证不通过，可以根据提示调整配置  

![Test PhpStorm Xdebug config](/images/2022-02-15/test_phpstorm_xdebug_config.jpg "验证 Web 服务器上的调试器配置")

### 在浏览器发起请求进行调试

在 [PhpStorm官方文档](https://www.jetbrains.com/help/phpstorm/2021.3/browser-debugging-extensions.html) 中下载浏览器拓展。

![Download Xdebug Helper](/images/2022-02-15/xdebug_download.png "下载Xdebug Helper")

在Xdebug一栏中，下载对应你的浏览器的拓展并安装。  

安装完成后，在浏览器中对你的项目发起请求，PhpStorm 会弹出对话框，点击`接受`后，就可以进行调试了。  

![Accept Xdebug](/images/2022-02-15/accept_xdebug.png "接受来自Xdebug的传入连接")

![Breakpoint in PhpStorm](/images/2022-02-15/helloworld.png "在PhpStorm中断点")

如果需要调试Ajax请求，则需要在请求参数中增加`XDEBUG_SESSION_START=PHPSTORM`  

### 在Postman发起请求进行调试

和调试Ajax请求类似，在Headers中增加`Cookie:XDEBUG_SESSION=PHPSTORM`即可  

### 遇到问题？

请查阅 [PhpStorm官方文档的“零配置调试教程”](https://www.jetbrains.com/help/phpstorm/2021.3/zero-configuration-debugging.html?utm_source=product&utm_medium=link&utm_campaign=PS&utm_content=2021.3)

