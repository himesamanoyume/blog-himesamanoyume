---
title: 'Nginx+IPv6+DDNS-GO实现公网访问'
date: 2024-10-19T12:00:00+08:00
description: '适用于Windows系统'
keywords:
  - '文章'
---

ipv6真好,去你妈的公网ipv4,电信死都不肯给

<!--more-->

### 本文不是教程,而是本人用于回想当时的步骤

##### 跑通流程

首先你的路由器得支持ipv6，方法自找，打开ipv6后还要在电脑的Internet属性启用ipv6协议

然后你应该就会看到自己的ipv6地址，此时可以去各种ipv6测试网站检测ipv6是否正常

然后在github下载ddns-go，并作为服务安装，保证开机后一直处于运行中

拿到DDNS服务商的密钥，在DDNS-GO管理界面输入对应的域名和密钥，选择通过api获取ipv6地址

保存后就能时刻保持域名指向本机的ipv6地址了

下载nginx的windows版本，在nginx.conf中添加配置

```conf
server{
    listen [::]:对外访问的端口; # ipv6要加[::]，有公网ipv4就只写端口
    server_name 对外访问的域名; # 应为ddns-go中解析ipv6的域名
    location / {
        proxy_pass http://localhost:本机对应服务的端口;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```

然后可通过在nginx根目录下cmd输入`start nginx`启动

注意需要老cmd的管理员模式

修改配置后重启则输入`nginx -s reload`

`taskkill /f /t /im nginx.exe`是终止所有在运行的nginx程序

记得防火墙开放本机对应服务的端口，嫌麻烦就直接关闭防火墙

此时在浏览器输入`对外访问的域名:对外访问的端口`即可访问

当然别忘了ipv6访问就要求对方也要开启了ipv6

---

##### 通过https访问确保安全性

可以去cloudflare、阿里云等地方弄一个自签名证书

并将对应服务商的ssl加密机制修改为`当源服务器支持SSL认证但未使用有效的公开可信的证书时`类似的模式

然后下载下来，再修改nginx.conf

```
server{
    listen [::]:对外访问的端口 ssl; # 多加一个ssl
    server_name 对外访问的域名;

    ssl_certificate 证书.pem的位置;
    ssl_certificate_key 密钥.pem的位置;

    location / {
        proxy_pass http://localhost:本机对应服务的端口;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
}
```

修改配置后重启`nginx -s reload`

此时就可以通过https进行访问，但是浏览器会提示不安全

这是因为自签名证书不是由公认的颁布证书的机构颁布给你的，因此不会被浏览器信任

当前正是处于`当源服务器支持SSL认证但未使用有效的公开可信的证书时`的情况

而https一旦开启了，其连接安全性是已经能够得到保证的，即端到端加密，所以无视不安全警告即可

除非你肯到受信任的公认证书机构获得证书

###### 结语

注意似乎不能开启CDN代理（小黄云）,因为你在国内,除非不是

所以你的ipv6地址被cloudflare的ip隐藏起来后要走境外的流量，这就会被ICP备案墙掉或者拦截

试了一下也很难做到http重定向为https，别搞了

---

- CDN各种尝试都失败了

- 老老实实多输入https吧