---
title: 'Windows重装应用清单'
date: 2023-09-25T6:00:00+08:00
keywords:
  - '工具'
---

**表中内容只适配我本人**

<!--more-->

目的是达成常用应用与设置的快速回忆补正

<style>
    .post-detail-txt .table-wrapper{
        word-break: break-word;
    }

</style>

## 固定到开始屏幕路径

`C:\Users\(YourUserName)\AppData\Roaming\Microsoft\Windows\Start Menu\Programs`

## 常用应用清单

名称|安装包|应用程序目录|说明|无需重装
:--:|:--:|:--:|:--:|:--:
QQNT|QQ9.9.3.17153_x64.exe|E:\Program Files (x86)\Tencent\QQNT| |&check;
Snap.Hutao|Microsoft Store安装|
v2rayN|v2rayN.zip|D:\v2rayN|记得添加开机自启,需要先安装.NET|&check;
RawAccel|RawAccel_v1.6.1.zip|E:\MySoftware\RawAccel|C:\Users\28583\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup 自启动|
Steam|SteamSetup.exe|
MEGAsync|MEGAsyncSetup64.exe|
Steam++|Microsoft Store安装| |令牌:Steam++  Authenticators 2022-08-02 1708080634495.mpo
.NET|windowsdesktop-runtime-6.0.22-win-x64.exe|
GeForce Experience|GeForce_Experience_v3.27.0.112.exe
小米妙享|小米妙享破解包.7z| | |?
Everything|Everything-1.4.1.969.x64-Setup.exe|E:\Program Files\Everything| |&check;
百度云盘|BaiduNetdisk_7.18.1.3.exe|E:\MySoftware\BaiduNetdisk| |&check;
XiaomiCloud|XiaomiCloud-2.5.1.exe|
Teamspeak3|TeamSpeak_3.5.6_win64.exe|E:\Program Files\TeamSpeak 3| |&check;
Github Desktop|GitHubDesktopSetup-x64.exe| 
电脑管家|QQPCDownload310053.exe|E:\Program Files (x86)\Tencent\QQPCMgr|注册表失效因此要重装|
网易云音乐|cloudmusicsetup2.7.6.198710.exe|E:\Program Files (x86)\Netease\CloudMusic| |&check;
UnityHub|UnityHubSetup.exe|E:\Program Files\Unity Hub| |&check;
EpicGames|EpicInstaller-14.2.1.msi|D:\EpicGames\Epic Games| |&check;
EA app|EAappInstaller.exe| | |
Ubisoft Connect|UbisoftConnectInstaller.exe|E:\MySoftware\Ubisoft Game Launcher| |&check;
Razer Synapse|RazerInstaller.exe|
向日葵|SunloginClient_13.1.1.54688_x64.exe|E:\MySoftware\SunloginClient| |?
雷神加速器|LeiGodSetup.8.0.2.4.exe|E:\Program Files (x86)\LeiGod_Acc| |&check;
Xbox| | |Microsoft Store下载/XboxInstaller.exe|?
Battle.Net|Battle.net-Setup.exe|E:\MySoftware\Battle.net| |&check;
VScode|VSCodeSetup-x64-1.48.1.exe| |建议直接默认安装在c盘,重装后注册表问题丢失懒得管
Adobe PS|E:\MyInstaller\Adobe Photoshop 2022 SP\Set-up.exe|E:\PS2022\Adobe Photoshop 2022| |&check;
Adobe PR|E:\MyInstaller\adobe_premiere_2022\Set-up.exe|E:\MySoftware\Adobe Premiere Pro 2022| |&check;
Adobe AU|E:\MyInstaller\AU2022\Set-up.exe|E:\MySoftware\Adobe Audition 2022| |&check;
Wub|Wub.exe|D:\WindowsReinstall| |&check;
Genshin/StarRail|计算机\HKEY_CURRENT_USER\Software\miHoYo(miHoYoSDK)
StarRail Unlock120FPS|KCN_Star_Rail_Unlock_V1.0.1.exe| | |&check;
Hugo|hugo_extended_0.118.2_windows-amd64.zip|C:\Program Files\Hugo|将zip解压至此目录并添加进系统变量Path
jdk17|jdk-17_windows-x64_bin.exe|
PotPlayer|PotPlayerSetup64_135.exe|
Python|python-3.11.1-amd64.exe|
搜狗|_sogou_pinyin_guanwang_134c.exe| |安装位置选为E:\Program Files (x86)|
QTTabBar|QTTabBar.exe| |QTTabBarConfig-2023-4-24.xml
Bandizip|BANDIZIP-SETUP-STD-ALL.EXE|E:\MySoftware\Bandizip|Bandizip.v7.xx.x64.Patch.20201104.exe放入目录启用|&check;
Office365|OfficeSetup.exe
Dolby Access|Microsoft Store安装
Wegame|WeGameSetup5.6.0.7079_launcher_0_0.exe|D:\OtherGames\WeGame| |&check;
Wechat|WeChatSetup.exe|E:\Program Files\Tencent\WeChat| |&check;
Steamtools|SteamtoolsSetup.exe| | |&check;


## 疑难杂症笔记

症状|解决方法
:-:|:-:
Wireless-AC 9260网卡Wifi无法连接|设备管理器中删除蓝牙与网络适配器中的`英特尔(R) 无线 Bluetooth(R)` `Intel(R) Wireless-AC 9260 160MHz`,再安装`WiFi-22.250.1-Driver64-Win10-Win11.exe`后关机并断电,再开机
虚拟机安装系统时镜像不识别DVD|按F12
WinPE下安装Windows到指定系统盘时无法安装|拔掉移动硬盘
安装Windows到指定系统盘时格式不对(Legacy MBR/UEFI GPT)|WinPE下用`diskpart`,`list disk`,`select disk (number)`,`clean`,`convert (mbr/gpt)`转换格式

## 设置修改笔记

#### Windows11

设置|做法
:-:|:-:
日期显示星期几|控制面板->时钟和区域(更改日期、时间或数字格式)->其他设置->日期->日期格式**短日期**更改为`yyyy/M/d dddd`

#### Windows10