---
title: '使用注册表快速登录miHoYo游戏'
date: 2023-09-26
keywords:
  - '笔记'
---

- Win+R,regedit
<!--more-->
- `计算机\HKEY_CURRENT_USER\SOFTWARE\miHoYo\原神`
- `计算机\HKEY_CURRENT_USER\SOFTWARE\miHoYo\崩坏：星穹铁道`


在操作前先将这两个地址下的注册表清空,以免混入太多用不到的项目导致文件太大

#### 原神

在注册表清空的情况下在登录界面登录第一个账号,登录完成后按F5刷新注册表

留下最主要的为`GENERAL_DATA_h2389025596`,`MIHOYOSDK_ADL_PROD_CN_h3123967166`两项

保留有这两项后导出即可实现快速登录

但如果有比如**保留分辨率设置**,以及**去除小红点**的需求,可以在登录完后立即进入游戏,将小红点清除，设置好分辨率选项后退出到登录界面

再F5刷新注册表,将其导出

##### 可能需要保存的项目

> 如果你希望切换到其他设备时不用清小红点和调设置,那么你需要在该账号里调整好设置之后,再把注册表导出,缺点是注册表占用大小翻5~15倍,但由于我们基本只在一两台设备里登录,而不会频繁清除注册表,因此往往也只是首次登录时稍微麻烦一会,长期下来在不频繁清除注册表的情况下没必要保留那么多项目

- 红点清除
- 音量设置
- 分辨率设置
- 画面设置,垂直同步关
- 圣遗物素材选为4星以下
- 武器素材选为4星以下
- 探索派遣

#### 星铁

同原神操作一样

留下最主要的关服为`MIHOYOSDK_ADL_PROD_CN_h3123967166`

b服为`MIHOYOSDK_ADL_PROD_CN_14_0_h4052138443`

有额外需求的操作仍然同上

##### 可能需要保存的项目

- 红点清除
- 调整音量
- 设置分辨率
- 设置自动战斗继承
- 设置显示行动值
- 战斗中开启二倍速,自动战斗
- 画面设置
- 模拟宇宙星神图鉴红点
- 模拟宇宙关闭简略描述
- 遗器素材选为4星以下

---

#### 配合批处理文件快速登录

> 实际上退出到登录界面直接登录更快,而注册表登录这种方式都需要**退出游戏后**再使用注册表,再打开游戏才能生效,只适合特殊群体,比如代练不想记老板的账号密码,则只需要登陆一次后导出注册表并标记老板信息,之后即可在不去记账号密码的情况登录老板账号

用记事本填入下列代码 

将`原神xx1`,`genshin-xx1.reg`,`D:\Genshin Impact\Genshin Impact Game\YuanShen.exe`这些改为自己对应的名称

然后记事本另存为.bat文件 编码选为`ANSI`

```bat
>nul 2>&1 "%SYSTEMROOT%\system32\cacls.exe" "%SYSTEMROOT%\system32\config\system"
if '%errorlevel%' NEQ '0' (
goto UACPrompt
) else ( goto gotAdmin )
:UACPrompt
echo Set UAC = CreateObject^("Shell.Application"^) > "%temp%\getadmin.vbs"
echo UAC.ShellExecute "%~s0", "", "", "runas", 1 >> "%temp%\getadmin.vbs"
"%temp%\getadmin.vbs"
exit /B
:gotAdmin
if exist "%temp%\getadmin.vbs" ( del "%temp%\getadmin.vbs" )
pushd "%CD%"
CD /D "%~dp0"

@echo off
echo 新设备使用miHoYoSDK.reg, 保存为.bat选择ANSI编码
echo  ————
echo 1、原神
echo 2、星铁
set /p c=请输入数字要关闭的游戏：
if %c%==1 taskkill /f /t /im YuanShen.exe
if %c%==2 taskkill /f /t /im StarRail.exe
echo  ————

@echo off
echo 1、原神xx1
echo 2、原神xx2
echo 3、星铁xx1
echo 4、星铁xx2
set /p a=请输入数字登录的账号：
if %a%==1 REG IMPORT genshin-xx1.reg
if %a%==2 REG IMPORT genshin-xx2.reg
if %a%==3 REG IMPORT starrail-xx1.reg
if %a%==4 REG IMPORT starrail-xx2.reg
echo  ————
@echo off
echo 1、启动原神
echo 2、启动星铁
echo 3、不启动
set /p b=请输入数字登录的账号：
if %b%==1 start "" "D:\Genshin Impact\Genshin Impact Game\YuanShen.exe"
if %b%==2 start "" "D:\Star Rail\Game\StarRail.exe"

exit
```

## 设备登录记录注册表

`计算机\HKEY_CURRENT_USER\Software\miHoYoSDK`

清空的话会需要首次登录验证

> 参考bilibili专栏《原神PC端如何多个账号自由切换，无需再次输入账号密码》[^1] 作者:猫猫和猫尾势不两立

[^1]: [原神PC端如何多个账号自由切换，无需再次输入账号密码](https://www.bilibili.com/read/cv11004659/)