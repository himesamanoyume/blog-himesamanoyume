---
title: '傻逼EA App安装笔记'
date: 2025-08-22T13:00:00+08:00
description: ''
keywords:
  - '文章'
---

自从我将系统Temp位置调整为Ramdisk中后，EA App安装就必定会出错，不得以只能写下这篇恐将伴随一生的文章笔记来记录处理办法

<!--more-->

1. 卸载EA App，并去EA App官网下载最新EAappInstaller
2. 安装过程中肯定是报错
3. 用`Everything`搜索`BootstrapperApplicationData`
4. 找到其中的EAapp安装程序下载地址

```xml
<WixPayloadProperties Payload="EAapp_13.535.0.6048_5312bacba_6afcbc30_3810.msi" Package="EAapp_13.535.0.6048_5312bacba_6afcbc30_3810.msi" Name="EAapp-13.535.0.6048-3810.msi" Size="234213376" DownloadUrl="https://origin-a.akamaihd.net/EA-Desktop-Client-Download/installer-releases/EAapp-13.535.0.6048-3810.msi" LayoutOnly="no" />
```

5. 直接浏览器下载这个完整的msi安装程序进行安装
6. 此时安装应该还是会报错，但是关闭后直接启动EAapp应该是能正常启动程序的
7. 然后用Steam登录避免傻逼EA重置我的密码