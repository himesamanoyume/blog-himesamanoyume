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
- [[Onedrive] 免正版验证的联机补丁 [500KB]](https://ygt3z-my.sharepoint.com/:u:/g/personal/topidolproducer_ygt3z_onmicrosoft_com/EWKlVF3nT1xMiCgTBVosdNcBfqH5EhwdYsM-4ZJxJwE7vA?e=kegEbW)
- [.NET Runtime 专用启动器必需的运行环境](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/runtime-desktop-8.0.0-windows-x64-installer)

如果<ruby>专用启动器<rt class="ttt" data-rt="SIT Manager.exe"></rt></ruby>能正常启动的话也可以不安装,但可能会出现界面错乱

- [[Onedrive] <ruby>专用启动器<rt class="ttt" data-rt="SIT Manager.exe"></rt></ruby> [31.2MB]](https://ygt3z-my.sharepoint.com/:u:/g/personal/topidolproducer_ygt3z_onmicrosoft_com/ESnFJVBZ1b1PsglaDqnDY4wBQaxcYEI3mXkr4cHbwUxK8w?e=8UfF4G)
- [Radmin LAN 局域网联机软件](https://download.radmin-lan.cn/download/files/Radmin_LAN_1.4.4642.1.exe) / 带公网的服务器
- 只需服主下载:[[Onedrive] SITCoop 服务端Mod 1.9.8742.42820 [15.1MB]](https://ygt3z-my.sharepoint.com/:u:/g/personal/topidolproducer_ygt3z_onmicrosoft_com/ESsbNUTozU1GuLdhL24CbGwB4HefiDrfS3s2AmkLSJNv1g?e=YoSJkF)
- 只需服主下载:[服务端SPT-AKI 3.7.6 Release-26535](https://dev.sp-tarkov.com/attachments/d549e35d-998c-4986-8c78-64571a6e083c)


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
- 用**免正版验证的联机补丁**替换掉`{Game}/BepInEx/plugins`下的`StayInTarkov.dll`

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

---

## 进阶

以上是基础流程,下面为进阶版,将为服务端和客户端新增改变AI逻辑的mod

由于SIT模组的代码为专门编写,因此不兼容一般的SPT模组,所以必须使用被SIT开发组特别编译过的能够兼容SIT的mod版本,才能使用

以下是整合包链接:

- [[Onedrive] ExtendMod [45.4MB]](https://ygt3z-my.sharepoint.com/:u:/g/personal/topidolproducer_ygt3z_onmicrosoft_com/EfksY34CqfVGhbso0b1LyK0Bm5upJJmQyAUQXL9I3dYhFg?e=RWa60e) (v2024.1.8)

整合包分为`GameSide`,`ServerSide`

将`GameSide`里的内容直接放入到`{Game}/`下,GameSide为所有人都需要安装

将`ServerSide`里的内容直接放入到`{Server}/`下,ServerSide则只需要服主安装

目前ExtendMod中包含:

- [SAIN/原文链接](https://hub.sp-tarkov.com/files/file/1062-sain-2-0-solarint-s-ai-modifications-full-ai-combat-system-replacement/):大型AI逻辑改变MOD,完全取代战斗逻辑,F6打开图形配置界面
- - 会根据声音做出反应,如听到枪声会前往侦察,听到玩家掏手雷会主动出击
- - 交战时AI会做出更符合玩家的操作,如受伤会冲刺躲藏到掩体后回状态,从掩体后进行侧身攻击或者盲射
- - 索敌范围会受到天空亮度和天气影响,会被植物遮挡视线,不再能够透视
- - 会出现小组集体行动
- `BigBrain`:前置MOD
- `Waypoints`:前置MOD
- [LootingBots/原文链接](https://hub.sp-tarkov.com/files/file/1096-looting-bots/):掠夺BOT,AI逻辑改变MOD
- - AI会定期检测周围的战利品,会像玩家一样进行搜刮,同时换掉身上的武器装备,也会将搜刮到的高价值物品放入背包
- - AI PMC不再会以身上直接带着高价值物品的状态出生
- `ConfigurationManager`:mod配置管理器(未安装SAIN时在游戏中F1打开,安装SAIN后为F12打开)

**将来整合包会加入的MOD**

- [QuestingBots/原文链接](https://hub.sp-tarkov.com/files/file/1534-questing-bots/#overview)`SIT尚未完成适配`:AI逻辑改变MOD
- - 模拟线上战局玩家数量的AI PMC会在开局时刻立即生成在随机PMC复活点
- - AI PMC会随机获得塔科夫中真实的任务作为目标,将会尝试前往任务地点放置物品,或者击杀敌人等来完成任务,不再简单地在出生区域巡逻;
- - 可能会出现组队PMC,其他成员陪同完成队长PMC的任务
- - 如果出生时距离过近可能会让PMC直接突脸玩家,且如果靠近空投区域也会去抢空投

> 整合包的内容必须适配本文提到的服务端版本和游戏版本,若全程都已按照本文教程安装,那么整合包应该可以直接使用