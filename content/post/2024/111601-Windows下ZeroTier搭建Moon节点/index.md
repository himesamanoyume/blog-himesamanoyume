---
title: 'Windows下ZeroTier搭建Moon节点'
date: 2024-11-16T00:00:00+08:00
description: ''
keywords:
  - '文章'
---

<!--more-->

### MOON节点机器

1. 安装ZeroTier

2. 以**管理员**打开cmd并cd至`C:\ProgramData\ZeroTier\One\`,然后可通过在该路径下输入`zerotier-one_x64.exe -i`查看版本信息

3. 输入`zerotier-one_x64.exe -i initmoon identity.public >>moon.json`生成`moon.json`文件

4. 修改`moon.json`内容

`"stableEndpoints": []`改为`"stableEndpoints": [ "{公网ip}/9993"]`

5. cmd输入`zerotier-one_x64.exe -i genmoon moon.json`生成`000xxx.moon`文件

6. 同目录下新建`moons.d`文件夹

7. 将`000xxx.moon`文件复制进`moons.d`文件夹内

8. 到服务中找到`ZeroTier One`,重新启动服务

> 公网服务器应该不需要开放防火墙端口

### LEAF节点机器

1. 安装ZeroTier

2. 以**管理员**打开cmd并cd至`C:\ProgramData\ZeroTier\One\`,然后可通过在该路径下输入`zerotier-one_x64.exe -i`查看版本信息

3. 输入`zerotier-one_x64.exe -q orbit xxx xxx`加入Moon节点

> 注意：`xxx`即为`000xxx.moon`中的`xxx`,要把前面的0删去

会提示`200 orbit OK`

4. 随后输入`zerotier-cli listpeers`查看是否能看到如`200 listpeers xxx {公网ip}/9993;13744;13608 136 1.14.2 MOON`的条目,即已正常加入moon节点

---

> 注意：不要将xxx泄露,否则别人将可以使用你的moon节点,对服务器流量造成影响或浪费