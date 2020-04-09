---
title: 基于小米球的内网穿透
tags: [内网穿透]
categories: [运维部署]
date: 2020-04-09 16:46:12
photos: [http://ngrok.ciqiuwl.cn/img/ngrok_p.jpg]
top: 1
---

# 基于小米球的内网穿透
![ngrok](http://ngrok.ciqiuwl.cn/img/ngrok_p.jpg)
## 需求场景
* 需要免费内网穿透服务
* 管理内网服务器，内网web进行演示
* 快速开发微信程序和第三方支付平台调试
## 小毛球简介
>ngrok 服务可以分配给你一个域名让你本地的web项目提供给外网访问，特别适合向别人展示你本机的web demo 以及调试一些远程的API (比如微信公众号，企业号的开发) ngrok的官方服务可以在 这里查看 由于一些原因 有些同学可能打不开官方网站，国内访问不了，万幸的是ngrok 1.7版本的代码是开源的。 小米球就是基于ngrok的服务（小米球ngrok），来造福开发者。
* 为什么不直接使用[ngrok](https://dashboard.ngrok.com/get-started)？
  所用的服务器为美国服务器，会比较卡顿。
  
## 准备
1. 注册一个[小毛球账号](https://manager.xiaomiqiu.com/)，获取免费的Token
![token](token.jpg)
2. 在后台首页下载对应版本客户端
![download](download.jpg)
3. 将下载的压缩文件解压
![文件](jieyan.jpg)
4. 修改配置 ngrok.conf

| 属性名 | 解释 |
| ----  | ----  |
| auth_token | 换成注册从后获取的Token |
| subdomain | 外网访问的域名前缀,最好写一个不容易被别人重复的 |
| httpstun | 隧道名称  可以自定义 |
| http https | 协议 |
```
server_addr: "ngrok2.xiaomiqiu.cn:5432"
trust_host_root_certs: true
inspect_addr: disabled
auth_token: "2994ecZ4345249f7bAA94949889c82Ac"

tunnels:

    httptun:
      remote_port: 80
      subdomain: my-test
      proto:
        http: 127.0.0.1:8088
    httpstun:
      remote_port: 443
      subdomain: my-test
      proto:
        https: 127.0.0.1:8080
    tcptun:
      remote_port: 81
      proto:
        tcp: 127.0.0.1:81
```
>如果打开ngrok.conf发现格式是乱的，请尝试用其他
>文本工具(如:Editplus、Notepad++)打开试试!重新修正~

## 启动命令
linux 和MAC 如下
```
1、chmod +x ngrok

2、chmod +x ngrok.conf

3、./ngrok -log=ngrok.log -config ngrok.conf start httptun httpstun
```

## 执行结果如下：
![result](result.jpg)
浏览器输入 http://my-test.ngrok2.xiaomiqiu.cn
就是我们外网地址。
---
{% meting "60198" "netease" "playlist" "autoplay" "mutex:false" "listmaxheight:340px" "preload:none" "theme:#ad7a86"%}
