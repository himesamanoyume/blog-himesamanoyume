---
title: 'Miyako Tarkov'
date: 2024-12-05T00:00:00+08:00
description: '私服v1.3'
keywords:
  - '文章'
---

<!--more-->

> SPT3.10.X 塔科夫0.15.5.1.33420 筹备中

将改为公网部署

# MOD添加清单

## Client Mods

- [ ] ~~**[SAIN](https://hub.sp-tarkov.com/files/file/1062-sain-solarint-s-ai-modifications-full-ai-combat-system-replacement/?highlight=sain#versions)[未适配3.10]**~~
- - 弃用

- [ ] ~~**[NoBushESP](https://hub.sp-tarkov.com/files/file/903-no-bush-esp/?highlight=no#versions)[未适配3.10]**~~
- - 弃用

- [x] [Waypoints](https://hub.sp-tarkov.com/files/file/1119-waypoints-expanded-navmesh/?highlight=waypo#versions)

- [x] [DynamicMaps](https://hub.sp-tarkov.com/files/file/1981-dynamic-maps/?highlight=dy#versions)
- - [汉化补丁](https://sns.oddba.cn/136048.html)

- [ ] **[friendlyPMC](https://hub.sp-tarkov.com/files/file/989-friendly-pmc/#versions)[未适配3.10]**
- - [原作者源码](https://bitbucket.org/pitvenin/friendlypmc/src/main/)
- - [我的源码](https://bitbucket.org/himesamanoyume/friendlypmc/src/main/)
- - [尝试实现适配联机时别人也无法掠夺跟随者物品1](https://bitbucket.org/pitvenin/friendlypmc/commits/d70e27b81e2a96ffbd018638583d19dece25df2f),[2](https://bitbucket.org/pitvenin/friendlypmc/commits/1b6385a100aa157077a59f1e8ea43396194d4c2b)
- - - 已知跟随者装备锁定只对主机有效,但是当联机时,会每人各生成一个小队,此时是否别的小队的装备是否可以掠夺,别的小队长的可掠夺情况又是如何

- [x] [ModSync](https://github.com/himesamanoyume/ModSync)
- - **需要重新克隆,进行汉化后编译**

- [x] [MoreCheckmarks](https://hub.sp-tarkov.com/files/file/1159-morecheckmarks/?highlight=MoreCheckmarks#versions)
- - [汉化补丁](https://sns.oddba.cn/136078.html)

- [x] [QuickSell](https://hub.sp-tarkov.com/files/file/2318-quicksell/?highlight=QuickSell#versions)
- - [汉化补丁](https://sns.oddba.cn/143051.html)

- [x] [BigBrain](https://hub.sp-tarkov.com/files/file/1219-bigbrain/?highlight=BigBrain#versions)

- [x] [QuickMoveToContainer](https://hub.sp-tarkov.com/files/file/1859-quick-move-to-containers/?highlight=Quick%20Move#versions)

- [x] [Fika](https://github.com/himesamanoyume/Fika-Plugin)
- - **已汉化并个性化处理,需要重新克隆编译**

- [x] [ItemSellPrice](https://hub.sp-tarkov.com/files/file/1230-item-sell-price/?highlight=Item%20Sell%20Price#versions)
- - [需要自行编译,去除Knight商人](https://dev.sp-tarkov.com/IcyClawz/ClientMods)

- [ ] [LootingBots](https://hub.sp-tarkov.com/files/file/1096-looting-bots/?highlight=looting#versions)

- [x] [Skipper](https://hub.sp-tarkov.com/files/file/1861-skipper/?highlight=Skipper#versions)
- - **想自己编译一下进行汉化:https://github.com/TerkoizLT/SPT-Skipper**

- [x] [UIFixes](https://hub.sp-tarkov.com/files/file/1860-ui-fixes/?highlight=UI%20Fix)
- - [汉化](https://sns.oddba.cn/139386.html)

- [x] [UnityToolKit](https://hub.sp-tarkov.com/files/file/1976-unitytoolkit/?highlight=UnityToolKit#versions)

## Server Mods

- [x] [ExpandedTaskText](https://hub.sp-tarkov.com/files/file/1415-expanded-task-text-ett/?highlight=Expanded%20Task%20Text#versions)
- - [汉化补丁](https://sns.oddba.cn/142846.html)

- [x] [autoprofilebackup](https://hub.sp-tarkov.com/files/file/1143-lua-s-auto-profile-backup-updated/#versions)
- - ~~暂时没有新版本,但应该直接通用~~没有什么是改不了
- - 如果在docker下使用,则需要将mod.ts中的`this.profilePath`这部分改为容器目录且不是本机目录的profile路径,如`/opt/server/user/profile`

- [ ] **[betterkeysupdated](https://hub.sp-tarkov.com/files/file/1963-better-keys-updated/#versions)[未适配3.10]**

- [ ] [LootingBots](https://hub.sp-tarkov.com/files/file/1096-looting-bots/?highlight=looting#versions)

- [x] [DynamicMaps](https://hub.sp-tarkov.com/files/file/1981-dynamic-maps/?highlight=dy#versions)
- - [汉化补丁](https://sns.oddba.cn/136048.html)

- [ ] **[LiveFleaPrices](https://hub.sp-tarkov.com/files/file/1561-live-flea-prices/#versions)[未适配3.10]**
- - 修改镜像(国内环境则无需修改):https://raw.gitmirror.com/DrakiaXYZ/SPT-LiveFleaPriceDB/main/prices-${gameMode}.json

## 整合包特色 v1.3

主打还原线上多人游戏体验的同时，尽可能发挥多人联机的乐趣，保持原汁原味地降低上手门槛。

AI敌人尽可能模拟真人行为。

没有朋友联机也有AI队友陪你。

萌新不懂做任务不懂战利品该不该留着，也有地图和标记告诉你。

## MOD列表

**Fika**

- 知名离线版联机mod
- 本人汉化+民间汉化

**friendlyPMC**

- 能让战局开始时自动生成AI队友全图跟随，单人塔科夫也完全不会孤独，满满的安全感，你只管舔包，周围交给他们来警戒吧！
- 本人针对Fika进行优化，拥有<span class="important">原作者版本所没有的功能</span>，专为联机而生
- 本人汉化

**SAIN**

- 知名改造AI逻辑mod，让AI的行为无限接近于人，视线也会被草丛等障碍物遮蔽，不再透视。但会探头歪头Peek射击，听见声音会静步走路，会当老6，会Pro哥突脸。你最好别再当他只是个AI！
- 民间汉化

**LootingBots**

- 能让AI对周边战利品进行搜刮，更换自身的装备。起全装被杀，AI能把你全身都毛喽！
- 民间汉化

**ItemSellPrice**

- 在物品详细界面能显示卖给商人的价格
- 民间+本人汉化

**MoreCheckmarks**

- 类似于愿望单。能够显示该物品在藏身处、任务的各种类目中的需求，方便萌新决定是否保留战利品。
- 民间汉化

**DynamicMaps**

- 动态地图。萌新福音，任务地点、撤离点、尸体位置、队友位置，无所遁形。
- 本人汉化

**LiveFleaPrices**

- 同步在线模式的跳蚤市场价格

**ExpandedTaskText**

- 会在任务说明处写明该任务所需的钥匙,改枪所需的配件,是否为灯塔商人，3x4的前置任务等等
- 民间汉化

**Skipper**

- 在商人任务界面按住左Ctrl可对任务的特定达成条件进行跳过,免去完成阴间任务所浪费的时间
- 本人汉化

**betterkeysupdated**

- 修改钥匙背景颜色,更好的区分钥匙地区
- 本人汉化

**autoprofilebackup**

- 在特定时间(登录游戏时,战局开始时,战局结束时,退出游戏时)自动备份存档,免受坏档困扰

**UIFixes**

- 新增一系列UI优化操作,如多选物品
- 民间汉化

**QuickMoveToContainer**

- 当开启对应容器的窗口时,自动检测快速移动物品时的去向至合适的容器当中,而不会一味地在背包胸挂与仓库之间移动

**QuickSell**

- 按下对应按键即可快速出售给价格最高的商人,或快速以合适的价格上架至跳蚤市场
- 民间汉化

**ModSync**

- 能够自动同步MOD列表,免去客户端更新mod的烦恼
- 本人汉化

## 其他优化

- 对游戏本体的某些未汉化内容和界面做了进一步的汉化
- 服务器会对每个人存档自动备份，分别为游戏启动时，战局开始和结束时

---

<blockquote style="background-color:#5f4040;box-shadow:3px 0 0 0 #d85959 inset;margin:10px 0 0 0;">
  已弃用
</blockquote>

<details>
<summary>老版本v1.2说明</summary>

基于SPT3.9.7 塔科夫0.14.9.1.30626

## 整合包特色 v1.2

主打还原线上多人游戏体验的同时，尽可能发挥多人联机的乐趣，保持原汁原味地降低上手门槛。

AI敌人尽可能模拟真人行为。

没有朋友联机也有AI队友陪你。

萌新不懂做任务不懂战利品该不该留着，也有地图和标记告诉你。

## MOD列表

**Fika**

- 知名离线版联机mod
- 本人汉化+民间汉化

**friendlyPMC**

- 能让战局开始时自动生成AI队友全图跟随，单人塔科夫也完全不会孤独，满满的安全感，你只管舔包，周围交给他们来警戒吧！
- 本人针对Fika进行优化，拥有<span class="important">原作者版本所没有的功能</span>，专为联机而生
- 本人汉化

**QuestingBots**

- 能让AI在战局中获得任务，使AI模拟真人玩家在战局中为了完成任务会做出的行为
- 民间汉化

**SAIN**

- 知名改造AI逻辑mod，让AI的行为无限接近于人，视线也会被草丛等障碍物遮蔽，不再透视。但会探头歪头Peek射击，听见声音会静步走路，会当老6，会Pro哥突脸。你最好别再当他只是个AI！
- 民间汉化

**LootingBots**

- 能让AI对周边战利品进行搜刮，更换自身的装备。起全装被杀，AI能把你全身都毛喽！
- 民间汉化

**ItemSellPrice**

- 在物品详细界面能显示卖给商人的价格
- 民间+本人汉化

**MoreCheckmarks**

- 类似于愿望单。能够显示该物品在藏身处、任务的各种类目中的需求，方便萌新决定是否保留战利品。
- 民间汉化

**DynamicMaps**

- 动态地图。萌新福音，任务地点、撤离点、尸体位置、队友位置，无所遁形。
- 本人汉化

**LiveFleaPrices**

- 同步在线模式的跳蚤市场价格

## 其他优化

- 对游戏本体的某些未汉化内容和界面做了进一步的汉化
- 服务器会对每个人存档自动备份，分别为游戏启动时，战局开始和结束时

</details>

---

> **写给自己**：公网IP开服一定要记得给梯子加直连规则,使用代理会连不上服务器