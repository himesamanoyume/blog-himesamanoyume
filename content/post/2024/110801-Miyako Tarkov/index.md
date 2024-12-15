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
- - [ ] 可能使用:[Fika-Dedicated](https://github.com/project-fika/Fika-Dedicated)
- - - 由于Miyako专版Fika是以最新源码编译,似乎导致了版本较后的Fika-Dedicated与Fika-Core有功能偏差,因此无法使用

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

- [x] [autoprofilebackup](https://hub.sp-tarkov.com/files/file/1143-lua-s-auto-profile-backup-updated/#versions)[官方未适配3.10]
- - 没有新版本,但改一下版本依赖就可以直接用
- - 如果在docker下使用,则需要将mod.ts中的`this.profilePath`这部分改为容器目录且不是本机目录的profile路径,如`/opt/server/user/profile`

- [x] [betterkeysupdated](https://hub.sp-tarkov.com/files/file/1963-better-keys-updated/#versions)[官方未适配3.10]
- - 但是似乎没有新钥匙所以可以改一下版本依赖就直接用

- [ ] [LootingBots](https://hub.sp-tarkov.com/files/file/1096-looting-bots/?highlight=looting#versions)

- [x] [DynamicMaps](https://hub.sp-tarkov.com/files/file/1981-dynamic-maps/?highlight=dy#versions)
- - [汉化补丁](https://sns.oddba.cn/136048.html)

- [x] [LiveFleaPrices](https://hub.sp-tarkov.com/files/file/1561-live-flea-prices/#versions)[官方未适配3.10]
- - 没有新版本,但改一下版本依赖就可以直接用
- - 修改镜像(国内环境则无需修改):https://raw.gitmirror.com/DrakiaXYZ/SPT-LiveFleaPriceDB/main/prices-${gameMode}.json

## 整合包特色 v1.3

主打还原线上多人游戏体验的同时，尽可能发挥多人联机的乐趣，保持原汁原味地降低上手门槛。

AI敌人尽可能模拟真人行为。

没有朋友联机也有AI队友陪你。

萌新不懂做任务不懂战利品该不该留着，也有地图和标记告诉你。

## MOD列表

**Fika**

- 知名离线版联机mod
- 本人汉化

**friendlyPMC**(未完成)

- 能让战局开始时自动生成AI队友全图跟随，单人塔科夫也完全不会孤独，满满的安全感，你只管舔包，周围交给他们来警戒吧！
- 本人针对Fika进行优化，拥有<span class="important">原作者版本所没有的功能</span>，专为联机而生
- 本人汉化

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

**写给自己**：公网IP开服一定要记得给梯子加直连规则,使用代理会连不上服务器

# 记录docker开服+fika专用客户端

不知道究竟是因为linux dd了windows导致了性能损耗还是vCPU或者硬盘的性能不太够,GCP的第二代机器用来作为Fika的专用客户端一直很垃圾

我开个灯塔，要等足足14分钟，完美还原NJT匹配体验

直到我在新加坡开出了第四代机器，使用了Hyperdisk硬盘，Linux搭建1panel面板使用docker开服后，一切都有了转变

cpu性能和硬盘的大幅提升是加载速度变快的主要因素

甚至已经达到了跟我电脑同等的加载速度，开一局灯塔我加载完刚好专用客户端也加载完了，马上战局就倒计时开始，在我吃了之前那么多的史之后，直接把我惊到了

终于实现了离线版自己一个人玩还不用自己电脑出算力计算AI，简直不要太爽

因此在这记录开服的几个重要步骤，以后开服我必定继续仰赖GCP C4机器

## 选机器

亚太地区只有新加坡的配额能开出4核8vCPU,60G的机器

## 前期准备

1panel,防火墙,游戏本体整合包

## 安装

### Docker

### Docker服务器容器 fika-spt-server-docker

[fika-spt-server-docker](https://github.com/zhliau/fika-spt-server-docker)

因为我使用3.10.1所以这么写

```docker
docker run --name fika-server \
  -e LISTEN_ALL_NETWORKS=true \
  -v /path/to/server/files:/opt/server \
  -p 6969:6969 \
  --network host \
  ghcr.io/zhliau/fika-spt-server-docker:3.10.1
```

官方教程的为

```docker
docker run --name fika-server \
  -e INSTALL_FIKA=true \
  -e LISTEN_ALL_NETWORKS=true \
  -v /path/to/server/files:/opt/server \
  -p 6969:6969 \
  ghcr.io/zhliau/fika-spt-server-docker:3.10.2
```

我是不想让他自动安装fika的，而是先创建完容器之后，在本机电脑调试完成服务端后再把mod核设置等全部上传至容器路径中

#### Docker专用客户端容器 fika-headless-docker

[fika-headless-docker](https://github.com/zhliau/fika-headless-docker)

```docker
docker run --name fika_dedicated \
  -v {游戏本体路径}:/opt/tarkov \
  -e PROFILE_ID={填专用客户端存档的ID} \
  -e USE_MODSYNC=true \
  -e SERVER_URL={服务器公网ip/服务器域名} \
  -e AUTO_RESTART_ON_RAID_END=true \
  -e SERVER_PORT=6969 \
  -p {默认25565}:{默认25565}/udp \
  ghcr.io/zhliau/fika-headless-docker:latest
```

官方是这样的

```docker
docker run --name fika_dedicated \
  -v {游戏本体路径}:/opt/tarkov \
  -e PROFILE_ID={填专用客户端存档的ID} \
  -e SERVER_URL={服务器公网ip/服务器域名} \
  -e SERVER_PORT=6969 \
  -p 25565:25565/udp \
  ghcr.io/zhliau/fika-headless-docker:latest
```

如果在linux中使用`lua-autoprofilebackup`, 则到`mod.ts`
```ts
const dirArray = __dirname.split("\\");
this.profilePath = `${dirArray[dirArray.length - 4]}/profiles`;
```
修改为
```ts
const dirArray = "/opt/server/user";
this.profilePath = `${dirArray}/profiles`;
```

因为docker镜像的fika-server会每日备份一次`/user/profiles`，因此搭配`lua-autoprofilebackup`效果更好

##### 其中几个重点,其余细节不多说。并且第二第三点内容可作为连接不上专用客户端时的自查清单

1. 如何在linux上下载好游戏本体

我是通过Onedrive来存放整合包的,[点击这里查看linux下载Onedrive分享文件的方法](#onedrive)

2. 如何让专用客户端能正常连接上其他客户端

- SERVER_URL**一定要直接填公网IP**或**域名**，不要填`127.0.0.1`,`0.0.0.0`，哪怕是同一台机器

- `BepInEx/config`中`com.fika.core.cfg`的和`强制IP(Force IP)`**只能**填`公网IP`

如果使用临时公网IP的话，最好选择固定IP，因为`com.fika.core.cfg`内的IP不能填域名

注意有些时候里面的内容会出现仍未被我汉化过的配置名，改值的时候千万要记得全部改了，不要改了英文的配置，中文的配置没改，使用中文配置的客户端就可能无法连接

3. 单服务器多个开多个专用客户端的方式

- 将整合游戏本体复制一份，然后再用docker run命令对应生成一个新容器。经过测试，`EscapeFromTarkov_Data`不能用符号链接的，只能全部复制

- **容器网络要选择`bridge`**

- **udp端口要改掉，如`25566:25566`,那么`com.fika.core.cfg`中的udp端口也要对应改掉为`25566`**

- **同时其他配置要满足`2.`，并且别忘记开防火墙，限制20G内存**

- 记得到fika-server的`/user/mods/fika-server/assets/configs/fika.jsonc`中修改配置来生成专用客户端存档,forceIP可填域名/IP，无所谓，因为docker下是用不到他生成的bat脚本的，一定要点开profile中的对应存档查看ID来填入到docker中


## 其他可能会用到的

**符号链接**

`ln -s <被链接的路径> <将被链接的路径>`

可以用来链接文件或文件夹到另一个路径中，减少存储的浪费


<div id="onedrive"></div>

## Linux下载Onedrive文件

在网页onedrive目录上打开F12，切换到网络，筛选器填`aspx`

对想下载的文件点下载，然后马上关掉已经开始的下载

看F12找到对应了文件大小的那一项,右键`复制`->`复制为cURL命令(bash)`，会得到一大段东西

```
curl 'XXX/_layouts/15/download.aspx?UniqueId=XXX' \
  -H 'accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7' \
  -H 'accept-language: zh-CN,zh;q=0.9,en;q=0.8,ja;q=0.7' \
  ....
  ....
  ....
  -H 'sec-gpc: 1' \
  -H 'service-worker-navigation-preload: {"supportsFeatures":[1855,61313]}' \
  -H 'upgrade-insecure-requests: 1' \
  -H 'user-agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/131.0.0.0 Safari/537.36 Edg/131.0.0.0'
```

在最后加上` \`然后换行再机上`--output 文件名.后缀`

文件名不能带路径，没用，会全部当成文件名写上去

```
curl 'XXX/_layouts/15/download.aspx?UniqueId=XXX' \
  -H 'accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7' \
  -H 'accept-language: zh-CN,zh;q=0.9,en;q=0.8,ja;q=0.7' \
  ....
  ....
  ....
  -H 'sec-gpc: 1' \
  -H 'service-worker-navigation-preload: {"supportsFeatures":[1855,61313]}' \
  -H 'upgrade-insecure-requests: 1' \
  -H 'user-agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/131.0.0.0 Safari/537.36 Edg/131.0.0.0' \
  --output 文件名.后缀
```

到SSH终端输入即可下载，至于要怎么找到在哪就看你自己了，应该是在`root`下吧

还有一点这个方法不能多个下载，适合下载一个单独的大文件

## Linux解压超过4GB大小文件的方法

```bash
sudo apt update
sudo apt-get install p7zip-full
```

```bash
7z x xxx.zip
```