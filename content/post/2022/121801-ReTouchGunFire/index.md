---
title: 'Re-TouchGunFire'
date: 2022-12-18T6:00:00+08:00
description: ''
keywords:
  - '项目'
---

该项目是一个最多支持4人联机的在线游戏,玩家通过击杀敌人获取经验值与金币,并逐步提升枪械与装备的属性使自己更加强大

<!--more-->

# Re-TouchGunFire

完全自写的服务端与客户端,网络协议使用了 Protobuf ,实现了基本的数据同步和玩家信息存
储 

项目的服务端和客户端可拓展性较强,99%的资源使用 AB 包加载,具备热更新能力改造的基础,
项目结构满足了小型游戏的后续更新需求,能够方便地进行后续新内容的添加与更新

游戏玩法实现了好友系统,组队系统,商店系统,单人出战/组队出战,且重要数据皆以服务器为
准 

项目代码耦合性低,简洁美观,注释较少但可读性极高,且开发过程运用了中介者模式,事件模式,
状态模式,直到项目末期开发仍然十分轻松

#### 玩法

战斗场景是玩家通过旋转角度 尽可能让敌人的身形重叠

就可以让子弹穿透敌人并根据枪械的属性和副词条 

造成不同的直击伤害(爆头/暴击)和穿透伤害,如狙击步枪的爆头率更高,穿透伤害更高,轻机枪对敌人的护甲造成的伤害更高,微型冲锋枪的暴击率更高

视频中敌人尚不会对玩家发动攻击,否则将根据玩家的防御属性先对护甲造成伤害,再对本体造成伤害,玩家的血量和护甲亮都会自动回复

想要获得更强的属性就必须不停刷怪获取金币,购买解锁新武器新装备,并刷新武器装备上的主词条和副词条,不同的装备还带有特定的天赋,将能够进一步增强玩家的实力

如主玩自动步枪的玩家目标就是尽可能地把所有装备的副词条都刷到高数值的自动步枪相关的词条

<iframe id="spkj" src="https://www.acfun.cn/player/ac40190066" width="100%" frameborder="no" scrolling="no" allowfullscreen="allowfullscreen"><span data-mce-type="bookmark" style="display: inline-block; width: 0px; overflow: hidden; line-height: 0;" class="mce_SELRES_start"></span> <span data-mce-type="bookmark" style="display: inline-block; width: 0px; overflow: hidden; line-height: 0;" class="mce_SELRES_start"></span> </iframe> <script type="text/javascript"> document.getElementById("spkj").style.height=document.getElementById("spkj").scrollWidth*0.76+"px"; </script>