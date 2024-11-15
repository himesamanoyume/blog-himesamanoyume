---
title: '谷歌云'
date: 2024-11-15T00:00:00+08:00
description: ''
keywords:
  - '文章'
---

<!--more-->

### 谷歌云免费试用300美金到期后，无限续期

1、注册一个新的谷歌账号

2、然后注册谷歌云，绑定信用卡，注意信用卡，必须为实体卡，国内visa也可以，虚拟信用卡大概率不通过

3、在结算->账号管理->重命名计费账户，可以将名字改为一个好记的名称，如日期0730

4、屏幕右侧点击添加主账号，主体设置为老的谷歌账号地址（输入邮箱地址），分配角色为billing account administrator；到此在新的谷歌云账号设置内容完毕

5、登录老的谷歌云账号，点击结算->账号管理，修改项目的结算账号，改为刚刚定义的新的结算账号，至此设置完毕，可以看到新的300美金了

### 谷歌云DD Windows 一键脚本

系统更新

```
apt update -y && apt install -y wget sudo
```

一键脚本

```
wget --no-check-certificate -qO InstallNET.sh 'https://moeclub.org/attachment/LinuxShell/InstallNET.sh' && bash InstallNET.sh --ip-addr {内网ip} --ip-gate {内网网关} --ip-mask 255.255.255.0  -dd 'https://oss.sunpma.com/Windows/Win_Server2022_64_Administrator_nat.ee.gz'
```

用户名：Administrator
密码：nat.ee

用户名和密码根据链接上的决定

换系统链接到[这](https://oss.sunpma.com/?Windows)

运行脚本后尽快用远程控制输入公网ip进行连接后修改密码

否则容易被扫到改密
