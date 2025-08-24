---
title: '神医治好我的Github Desktop卡顿'
date: 2025-08-24T12:00:00+08:00
description: ''
keywords:
  - '文章'
---

不知从哪天起，用了很久的Github Desktop总是开始莫名奇妙的卡顿...

<!--more-->

看到这个Issue之后，我终于成功解决

[GitHub Gets Very Slow #20059](https://github.com/desktop/desktop/issues/20059)

> @LuxyCeremy: I just fixed it! It disturbs me for weeks! Just go to Service and disable "Microsoft PC Manager" related service and uninstall it, then github desktop is smooth as before! Microsoft PC Manager is a Mcafee like software, it blocks many processes when they tries to read files! I am adding everything to windows defender's white list, but it didn't work. I never thought that MSPC Manager is the culprit!

总之就是把Windows服务`Microsoft PC Manager`终止运行

至于要不要卸载，我选择先终止运行一段时间看是否会造成其他问题