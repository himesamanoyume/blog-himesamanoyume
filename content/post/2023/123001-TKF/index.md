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

- [游戏本体 0.14.0.0.28375](https://ygt3z-my.sharepoint.com/:u:/g/personal/topidolproducer_ygt3z_onmicrosoft_com/EVQxM56DgwxGl_VOcNK2ezkB6zUqfM2bKB_vYTz2PY2x2A?e=JDQxJy)
- [降级补丁 0.14.0.0.28375 → 0.13.9.1.27622](https://ygt3z-my.sharepoint.com/:u:/g/personal/topidolproducer_ygt3z_onmicrosoft_com/ET3ZSu2wMDtPsXFJ-qMjvd4B_9PlwjcFsLkIcBam8OfK-w?e=HvhaLV)
- [大概免正版验证的联机补丁](https://ygt3z-my.sharepoint.com/:u:/g/personal/topidolproducer_ygt3z_onmicrosoft_com/EWKlVF3nT1xMiCgTBVosdNcBfqH5EhwdYsM-4ZJxJwE7vA?e=kegEbW)
- [专用启动器必需的运行环境](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-desktop-8.0.0-windows-x64-installer)
- [专用启动器](https://ygt3z-my.sharepoint.com/:u:/g/personal/topidolproducer_ygt3z_onmicrosoft_com/ESnFJVBZ1b1PsglaDqnDY4wBQaxcYEI3mXkr4cHbwUxK8w?e=8UfF4G)

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
- 连接好指定的局域网软件

**局域网联机软件相关暂未补全**

- 使用`SIT Manager`填写对应的`Address`,连接