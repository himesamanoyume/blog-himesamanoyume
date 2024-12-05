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

### 带进度条的dd脚本

[Github地址](https://github.com/minlearn/inst)

最简单的方式

```
wget -qO- inst.sh | bash
```

然后会要求你的输入target,这时就复制一个想要dd的直链进去即可

```
wget -qO- inst.sh|bash -s - -选项名 选项值 -t 目标值

                          —————————————————————————————————————————————————
   * 指定debian镜像源:     | -m github/gitee/xxxx | -t debian               | * debian是原生方式
   * 指定第一张网卡名:      | -i enp0s1...         |    dummy                |   安装的纯净debian;
   * 指定静态网络配置:      | -n ip/cidr,gateway   |    或自定gz/xz/qcow2镜像  | * dummy是空目标仅供
   * 指定第一个硬盘名:      | -p sda...            |                         |   调试模式用;
   * 指定用户密码安装:      | -w mypass...         |                         | * 自定义镜像是dd方式
   * 指定安装完成动作:      | -o 1/2/3/4           |                         |   安装的raw系统硬盘格式经过
       不扩展磁盘:         |    1:noexpanddisk    |                         |   gzip/xz打包后托管的http/https地址;
       不注入网络:         |    2:noinjectnetcfg  |                         |   或者qcow2格式的cloudimage
       保持不重启:         |    3:noreboot        |                         |   托管的http/https地址
       不预先清除:         |    4:nopreclean      |                         |  
   * 指定使用IP6:          |  -6 1                |                         |
                          —————————————————————————————————————————————————                                             
                          * 以上选项可有可无可组合    * -t必须指定，且唯一
```

等到重启之后就可以到公网ip的网页看到VNC画面

前提是防火墙开放了5900端口

等到进度条走完,重启之后应该就能用RDP连接了

记得重新分配磁盘大小

---

> 此部分已弃用

因为该系统资源站似乎会炸,导致vps无限等待,下不完东西

### 谷歌云DD Windows 一键脚本

系统更新

```
apt update -y && apt install -y wget sudo
```

一键脚本(不要直接复制就用，注意代码里面有需要填的东西)

```
wget --no-check-certificate -qO InstallNET.sh 'https://moeclub.org/attachment/LinuxShell/InstallNET.sh' && bash InstallNET.sh --ip-addr {内网ip} --ip-gate {内网网关} --ip-mask 255.255.255.0  -dd 'https://oss.sunpma.com/Windows/Win_Server2022_64_Administrator_nat.ee.gz'
```

##### 报错Error! grub.cfg.解决方案

`cd /boot && ls -lha`

应该会看到只有一个grub文件夹,而grub2的配置文件通常为`/boot/grub2`

所以很有可能是由于没有grub2文件夹导致的

`mkdir /boot/grub2 && grub-mkconfig -o /boot/grub2/grub.cfg`创建一个grub2文件夹后再尝试即可

---

等待一段时间

用户名：Administrator
密码：nat.ee

用户名和密码根据链接上的决定

换系统链接到[这](https://oss.sunpma.com/?Windows)

运行脚本后尽快用远程控制输入公网ip进行连接后修改密码

否则容易被扫到改密

> 目前是发现使用Debian, c2d-highcpu, 128g ssd的成功率很高
