---
title: 'M7A-Private使用说明'
date: 2023-12-13T6:00:00+08:00
description: '内部软件 切勿外传'
keywords:
  - '文章'
---

适用于M7A Private v1.7.1.2 ~ 更高版本

<!--more-->

### 准备条件

- [点击下载并安装Python](https://www.python.org/ftp/python/3.11.1/python-3.11.1-amd64.exe)

M7A本体不需要Python环境可以直接运行,但是第三方使用的模拟宇宙项目是源码运行,因此需要Python

- 需要后台运行或多显示器可以尝试查看教程 [远程本地多用户桌面](https://www.bilibili.com/read/cv24286313/), 软件分别为:[SuperRDP2](https://github.com/anhkgg/SuperRDP), [SimpleRemote](https://gitee.com/zhudongyang/SimpleRemote)

按照教程新建一个用户,并用SimpleRemote以`1920*1080`分辨率连接,由于创建的新用户等同于重装系统一样,随后简单设置一下新用户的设置至符合你原先的使用习惯

<span class=important>切记每个新用户也都要安装一遍Python</span>

### 应用程序

在正式开始运行前,必须搞清楚以下应用程序的使用方式

- `March7th Assistant Server.exe`

脚本的服务端,Server必须比Client先启动,Client连接不上服务器则无法运行

在运行Server时,还将会开启`网页后台`,网页后台用于更方便地更改配置文件或者查看各种信息

网页后台地址根据控制台显示为准,你将会看见`Running on http://127.0.0.1:5000`以及另一个地址,两个地址在本机打开后都可以进入网页后台,但<span class=important>只有第二个地址比较特殊,在同一个网络环境下其他设备可以通过第二个地址进入后台</span>

- `March7th Assistant Register.exe`

用于获取注册表,Client的快速登录便是通过注册表直接导入来实现

- `March7th Assistant Client.exe`

脚本的客户端,如果Server没处于运行中就无法使用,如果没有填写注册表信息就无法使用

会自动更新第三方依赖项目,但不会更新本体自身

- `Update.exe`

专门用于更新M7A新版本本体

### 第三方依赖项目

- 模拟宇宙`Auto_Simulated_Universe`

需要Python运行,`March7th Assistant Client`首次运行时会自动下载

### Config.yaml

打开文件,每个项目后都有说明,通常不要手动更改,用网页后台修改能保证正确

### 使用流程

1. 运行`March7th Assistant Server`,首次生成`Config.yaml`配置文件

2. `Config.yaml`中找到`python_exe_path`和`game_path`,根据提示填写对应的信息

3. 使用`March7th Assistant Register`,登录账号,根据提示获取注册表,注册表地址在根目录`./reg`下

4. 进入网页后台,点击注册界面,将对应信息填好并保存

5. 使用`SimpleRemote`连接其他账户,在该账户下运行`March7th Assistant Client`
