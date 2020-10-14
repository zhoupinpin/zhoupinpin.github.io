---
title: mitmproxy的简单使用
date: 2020-10-14 21:53:09
tags:
    - 抓包
    - 数据
---
## 一、什么是抓包？怎么抓包？

1、抓包（packet capture）就是将网络传输发送与接收的数据包进行截获、重发、编辑、转存等操作，也用来检查网络安全。抓包也经常被用来进行数据截取等

2、一般常用的抓包软件优缺点如下:

（1）fiddler：免费，但是跨平台能力较差。在MAC上非常非常不好用。但是在windows上用起来感觉不错，重点是免费

（2）charles：跨平台不错，windows和mac上都能支持，遗憾的是这是一个收费软件。

（3）mitmproxy：跨平台能力不错、支持脚本扩展。是测试开发工程师常用的一款抓包工具，免费。只不过它是一个控制台的形式操作。
 
 (4) wireshark是非常流行的网络封包分析软件，功能十分强大。可以截取各种网络封包，显示网络封包的详细信息，但是只能查看封包，而不能修改封包的内容，或者发送封包。使用wireshark的人必须了解网络协议，否则就看不懂wireshark了。wireshark能获取HTTP，也能获取HTTPS，但是不能解密HTTPS，所以wireshark看不懂HTTPS中的内容，如果是处理HTTP,HTTPS 还是用Fiddler, 其他协议比如TCP,UDP 就用wireshark.(使用介绍: https://www.cnblogs.com/cocowool/p/wireshark_tcp_http.html#1-wireshark%E4%BB%8B%E7%BB%8D)

## 二、mitmproxy介绍

1、Mitmproxy是一个免费的开源交互式的HTTP/HTTPS代理。

2、mitmproxy就是用于MITM的proxy，MITM即中间人攻击（Man-in-the-middle attack）。用于中间人攻击的代理首先会向正常的代理一样转发请求，保障服务端与客户端的通信，其次会看看请求或者响应结果信息，记录其截获的数据或篡改数据，引发服务端或客户端特定的行为。

3、不同于fiddler或wireshark等抓包工具，mitmproxy不仅可以截获请求帮助开发者查看，分析，更加可以通过自定义脚本进行二次开发（篡改信息重新发送）。

4、mitmproxy还有两个关联组件。一个是mitmdump，它是mitmproxy的命令行接口，利用它我们可以对接Python脚本，用Python实现监听后的处理。另一个是mitmweb，它是一个Web程序，通过它我们可以清楚观察mitmproxy捕获的请求。

## 三、mitmweb的使用
windows环境 确保电脑和手机连接的同一个wifi
### 1、打开mitmweb(直接双击mitmweb图标即可)
同时会自动在浏览器中打开监控的界面
<img src="img/mitmweb-terminal.png" style="float: left; left: 0px;">

<img src="img/mitmweb-browser.png">

### 2、配置手机wifi的代理
图中的主机名即为电脑所在的ip，端口即为上图中所看到的mitmweb监听的端口
<img src="img/wifi-proxy.jpg" height="100px" width="200px" style="display: inline; float: left">