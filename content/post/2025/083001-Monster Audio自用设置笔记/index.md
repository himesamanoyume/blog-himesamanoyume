---
title: 'Monster Audio自用设置笔记'
date: 2025-08-30T00:00:00+08:00
description: ''
keywords:
  - '文章'
---

Monster Audio是一款国产免费机架软件

<!--more-->

## 准备工作

- 安装Monster Audio
- 安装ASIO4ALL
- 准备[Supertone Clear插件](https://plugincrack.com/vst/supertone-clear/)(至关重要)

## 正式操作

1. 启动 Monster Audio，选择ASIO4ALL声卡，然后**一定要记得先调声卡控制面板**。
  - 对我而言，需要点击声卡控制面板右下角的齿轮，再打开罗技PRO X、VB-Audio VoiceMeeter VAIO
2. 现在音轨输入处已经可选PRO X
3. 音轨-给别人听，输出选择`Monster Mic L、 R`
4. 音轨-给自己听，输出选择`VoiceMeeter vaio 1、 vaio 2`
5. 设置中通道默认播放设备选`VoiceMeeter AUX Input`，Windows输出设备也是
6. 默认录音设备选G PRO Microphone，Windows输出设备选`Monster Mic (01)`
7. VST添加自定义插件路径，选择Clear插件所在的路径
8. 音轨添加Clear，打开Clear插件窗口，然后将VOICE区域的S按钮打开，实现AI降噪
9. VoiceMeeter的输入处1选择`Monster Mic (01)`
10. OBS麦克风也选`Monster Mic (01)`

## 测试是否有效

- 打开录音机选Monster Mic进行录音，看是否能正常录音而不崩溃
- Oopz试音
- OBS录制
