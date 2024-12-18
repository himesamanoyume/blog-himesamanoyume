---
title: '谷歌云'
date: 2024-11-15T00:00:00+08:00
description: ''
keywords:
  - '文章'
---

<!--more-->

# 谷歌云免费试用300美金到期后，无限续期

1、注册一个新的谷歌账号

2、然后注册谷歌云，绑定信用卡，注意信用卡，必须为实体卡，国内visa也可以，虚拟信用卡大概率不通过

3、在结算->账号管理->重命名计费账户，可以将名字改为一个好记的名称，如日期0730

4、屏幕右侧点击添加主账号，主体设置为老的谷歌账号地址（输入邮箱地址），分配角色为billing account administrator；到此在新的谷歌云账号设置内容完毕

5、登录老的谷歌云账号，点击结算->账号管理，修改项目的结算账号，改为刚刚定义的新的结算账号，至此设置完毕，可以看到新的300美金了

### 关于结算账号

注意：切换结算账号会导致配额重置！！！

确定没事了之后再进行结算账号切换

现在有一件事需要验证，那就是当拥有配额，开了高级机器之后，在不删除机器的情况切换账号，这个机器是否会被强制删除

## 创建SSH

```
ssh-keygen -t rsa -f ~/.ssh/{KEY_FILENAME} -C {USERNAME}
```

> `KEY_FILENAME`：您的 SSH 密钥文件的名称。<br><br>例如，如果文件名为 my-ssh-key，则系统会生成一个名为 my-ssh-key 的私钥文件和一个名为 my-ssh-key.pub 的公钥文件。<br><br>`USERNAME`：虚拟机上的用户名。例如 cloudysanfrancisco 或 cloudysanfrancisco_gmail_com。<br><br>对于 Linux 虚拟机，除非您将虚拟机配置为允许 root 登录，否则 USERNAME 不能为 root。如需了解详情，请参阅以根用户身份连接到 Linux 虚拟机。

`ssh-keygen` 将您的私钥文件保存到 `~/.ssh/KEY_FILENAME`，并将公钥文件保存到 `~/.ssh/KEY_FILENAME.pub`

用户 `cloudysanfrancisco` 的公钥类似于以下内容：

```
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDAu5kKQCPF... cloudysanfrancisco
```

到生成的密钥路径处将不带后缀的那个文件打开，其中包含了私钥信息，下载下来

随后到GCP的云数据处添加SSH密钥，填入公钥

在第三方SSH客户端导入私钥文件,登录

*就是好像GCP的ssh登录即使sudo -i了也没有权限的样子，上传不了东西*

## DD脚本

针对第二第三个脚本：两个脚本各有所长,最高性能的AMD主机只有不带进度条的脚步能使用,原因是最高性能的主机必选网络接口,而当选择接口后带进度条的dd脚步就会卡住。然而即使使用不带进度条的脚本,只要谷歌云**开启了显示设备**,就能直接看到屏幕截图,所以其实无所谓,进度条指的是下载的进度条

即选择第四代AMD机器时,只能选不带进度条的脚本,第四代AMD以下配置的机器可以选带进度条的,速度很快,主要是下载下得快

但是四代机器用不带进度条脚本也仅仅是能安装的程度,镜像可能存在bug，导致即便安装成功也无法登录,原本的密码没法用

目前已经使用了winserver2022的nat.ee镜像,结果密码错误无法登录

所以下次有机会只能试试别的了

### 第一个，新找的不错的脚本，功能非常全面

[reinstall](https://github.com/bin456789/reinstall)

多的就不说了,直接进github看教程就完了

目前找到的唯一会自动安装gVNIC网卡的脚本，但是偏偏目前GCP似乎所有Windows的iso都会安装失败，无限重启

### 带进度条的dd脚本

[Github地址](https://github.com/minlearn/inst)

最简单的方式

```
wget -qO- inst.sh | bash
```

然后会要求你的输入target,这时就复制一个想要dd的直链进去即可

```

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

因为该系统资源站可能会改域名,下载不了东西就会导致vps无限等待

### 不带进度条的dd脚本

系统更新

```
apt update -y && apt install -y wget sudo
```

一键脚本(不要直接复制就用，注意代码里面有需要填的东西)

```
wget --no-check-certificate -qO InstallNET.sh 'https://moeclub.org/attachment/LinuxShell/InstallNET.sh' && bash InstallNET.sh --ip-addr {内网ip} --ip-gate {内网网关} --ip-mask 255.255.255.0  -dd 'https://oss.suntl.com/Windows/Win_Server2022_64_Administrator_nat.ee.gz'
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

换系统链接到[这](http://oss.suntl.com/?Windows)

运行脚本后尽快用远程控制输入公网ip进行连接后修改密码

否则容易被扫到改密

> 目前是发现使用Debian, c2d-highcpu, 128g ssd的成功率很高
