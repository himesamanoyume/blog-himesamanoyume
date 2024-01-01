---
title: 'TKF'
date: 2023-12-30T14:00:00+08:00
keywords:
  - '文章'
---

> 用于内部阅读

<!--more-->

现在处于**试验阶段**

### 链接

密码h***

推荐用IDM插件搭配IDM下载Onedrive相关文件

- [[Onedrive] 游戏本体 0.14.0.0.28375 [23.9GB]](https://ygt3z-my.sharepoint.com/:u:/g/personal/topidolproducer_ygt3z_onmicrosoft_com/EVQxM56DgwxGl_VOcNK2ezkB6zUqfM2bKB_vYTz2PY2x2A?e=JDQxJy)
- [[Onedrive] 降级补丁 0.14.0.0.28375 → 0.13.9.1.27622 [2.45GB]](https://ygt3z-my.sharepoint.com/:u:/g/personal/topidolproducer_ygt3z_onmicrosoft_com/ET3ZSu2wMDtPsXFJ-qMjvd4B_9PlwjcFsLkIcBam8OfK-w?e=HvhaLV)
- [[Onedrive] 大概免正版验证的联机补丁 [500KB]](https://ygt3z-my.sharepoint.com/:u:/g/personal/topidolproducer_ygt3z_onmicrosoft_com/EWKlVF3nT1xMiCgTBVosdNcBfqH5EhwdYsM-4ZJxJwE7vA?e=kegEbW)
- [专用启动器必需的运行环境](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-desktop-8.0.0-windows-x64-installer)
- [[Onedrive] 专用启动器 [31.2MB]](https://ygt3z-my.sharepoint.com/:u:/g/personal/topidolproducer_ygt3z_onmicrosoft_com/ESnFJVBZ1b1PsglaDqnDY4wBQaxcYEI3mXkr4cHbwUxK8w?e=8UfF4G)
- [Radmin LAN 局域网联机软件](https://download.radmin-lan.cn/download/files/Radmin_LAN_1.4.4642.1.exe)

### 步骤

- 创建一个目录(所有目录名不能为中文),名称自定,用`{Root}`来指代
- 将**游戏本体**解压到`{Root}`下,该目录用`{Game}`指代
- 将**降级补丁**解压并将里面的文件粘贴到`{Game}`下,运行`patcher.exe`,会自动更新补丁
- 下载并安装**专用启动器必需的运行环境**
- 将**专用启动器**解压到`{Root}`下,用`{Launcher}`指代
- 启动`{Launcher}`下的`SIT Manager.exe`
- - 点击`Settings`
- - `EFT Settings`中选择`EFT Path`的路径为`{Game}`
- - 点击`Tools`,选择`Install SIT`
- - 选择`StayInTarkov.Client-1.9.8742.42820 - Tarkov Version: 0.13.9.1.27622`,安装
- 用**大概免正版验证的联机补丁**替换掉`{Game}/BepInEx/plugins`下的`StayInTarkov.dll`
- 下载安装**Radmin LAN 局域网联机软件**
- - 网络→加入网络→私人网络
- - 填写对应名称和密码
- 使用`SIT Manager`填写对应的`Address`为`http://{Radmin中服主的IP}:6969`
- `SIT Manager` Connect, 尼基塔原神 启动!

### 联机创房

选择区域后一直下一步,最后才会有创房或者加入别人的房间

创房或者加入别人房间后,左上角应当出现在线连接情况,如果未出现或者搜不到别人的房间说明安装不成功,但是**如果能登录游戏说明已经连接上了服务器**,只是无法联机