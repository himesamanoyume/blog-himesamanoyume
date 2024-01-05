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
- [.NET Runtime 专用启动器必需的运行环境](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-desktop-8.0.0-windows-x64-installer)

如果<ruby>专用启动器<rt class="ttt" data-rt="SIT Manager.exe"></rt></ruby>能正常启动的话也可以不安装,但可能会出现界面错乱

- [[Onedrive] <ruby>专用启动器<rt class="ttt" data-rt="SIT Manager.exe"></rt></ruby> [31.2MB]](https://ygt3z-my.sharepoint.com/:u:/g/personal/topidolproducer_ygt3z_onmicrosoft_com/ESnFJVBZ1b1PsglaDqnDY4wBQaxcYEI3mXkr4cHbwUxK8w?e=8UfF4G)
- [Radmin LAN 局域网联机软件](https://download.radmin-lan.cn/download/files/Radmin_LAN_1.4.4642.1.exe) / 带公网的服务器
- 只需服主下载:[[Onedrive] SITCoop 服务端Mod 1.9.8742.42820 [15.1MB]](https://ygt3z-my.sharepoint.com/:u:/g/personal/topidolproducer_ygt3z_onmicrosoft_com/ESsbNUTozU1GuLdhL24CbGwB4HefiDrfS3s2AmkLSJNv1g?e=YoSJkF)
- 只需服主下载:[[Onedrive] 服务端SPT-AKI 3.8.0 [81.1MB]](https://ygt3z-my.sharepoint.com/:u:/g/personal/topidolproducer_ygt3z_onmicrosoft_com/EVhfOJG7LxVNk0K2BSGlmnkBeZzB4vVWRJO1Yl4a7vMUIg?e=bJpRUg)


## 步骤

- 创建一个目录(所有目录名不能为中文),名称自定,用`{Root}`来指代

### 玩家步骤

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

#### 如果是局域网联机

- 下载安装**Radmin LAN 局域网联机软件**
- - 网络→加入网络→私人网络
- - 填写私人网络对应的名称和密码(由创建私人网络的房主提供)

#### 公网服务器

- 无需特殊操作

#### 连接

- 防火墙打开`6969`和`6970`端口
- 使用`SIT Manager`填写对应的`Address`为`http://{Radmin中服主的IP/服务器公网IP}:6969`
- 若服主已开服,`SIT Manager` Connect进入游戏

---

### 服主步骤

- 启动`{Launcher}`下的`SIT Manager.exe`
- - 点击`Settings`
- - `EFT Settings`中选择`SPT-AKI Path`的路径为`{Server}`
- 直接运行`{Server}/Aki_Server.exe`或者在`SIT Manager`的Server中直接Start Server,此时将会生成服务器配置文件
- - 看到**玩得开心**或者**happy playing**即可关闭
- 将**服务端Mod**解压到`{Server}/user/mods`下,重命名该文件夹为`SITCoop`
- 再次Start Server,此时将会生成服务器Mod的配置文件
- - 看到**玩得开心**或者**happy playing**即可关闭

#### 如果是局域网联机

- 下载安装**Radmin LAN 局域网联机软件**
- - 网络→创建私人网络
- - 填写名称和密码,并提供给想要加入的玩家

#### 公网服务器

- 无需特殊操作

#### 修改配置文件

- 打开`{Server}/Aki_Data/Server/configs/http.json`,进行修改:
```json
{
  "ip": "0.0.0.0",
  "port": 6969,
  "webSocketPingDelayMs": 90000,
  "logRequests": true,
  "serverImagePathOverride": {	}
}
```
- 打开`{Server}/user/mods/SITCoop/config/coopConfig.json`,进行修改:
```json
{
  "protocol": "http",
  "externalIP": "{你的Radmin IP/公网服务器IP}",
  "webSocketPort": 6970,
  "webSocketTimeoutSeconds": 5,
  "webSocketTimeoutCheckStartSeconds": 120
}
```
- 启动服务器,完成开服
