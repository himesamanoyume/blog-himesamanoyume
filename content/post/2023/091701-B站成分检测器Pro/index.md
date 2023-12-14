---
title: 'B站成分检测器Pro'
date: 2023-09-17T6:00:00+08:00
keywords:
  - '项目'
---

**B站评论区自动标注成分的油猴脚本,请勿滥用**

> 免责声明:本脚本原作者为xulaupuz,trychen,现该脚本为**姫様の夢**用作学习用途制作,且仅在极小范围内发布供个别人员学习,任何未经本人允许而大范围散播该脚本所造成的后果皆与本人**姫様の夢**无关,本人不承担相关法律责任

<!--more-->

很久之前当时b站很流行查成分

比如什么三相之力之类的玩意

而该脚本就是其中一个脚本被本人修改后得到的

##### 如想使用请直接在代码块右上角点击复制,然后在油猴脚本新建一个脚本粘贴进去就行了

```javascript
// ==UserScript==
// @name         B站成分检测器Pro
// @version      2.841
// @author       xulaupuz,trychen,姫様の夢
// @namespace    blog.himesamanoyume.top
// @license      GPLv3
// @description  B站评论区自动标注成分,请勿滥用  /免责声明:本脚本原作者为xulaupuz,trychen,现该脚本为姫様の夢用作学习用途制作,且仅在极小范围内发布供个别人员学习,任何未经本人允许而大范围散播该脚本所造成的后果皆与本人姫様の夢无关,本人不承担相关法律责任
// @match        https://www.bilibili.com/video/*
// @match        https://www.bilibili.com/read/*
// @match        https://t.bilibili.com/*
// @match        https://www.bilibili.com/bangumi/play/*
// @match        https://www.bilibili.com/v/topic/detail?topic_id=*
// @match        https://space.bilibili.com/*
// @match        https://www.bilibili.com/read/*
// @match        https://live.bilibili.com/*
// @icon         https://blog.himesamanoyume.top/favicon.ico
// @connect      bilibili.com
// @grant        GM_xmlhttpRequest
// @require      https://cdn.jsdelivr.net/npm/jquery@3.6.1/dist/jquery.min.js
// ==/UserScript==
/*
  2.841:fix something
  2.84:新增动态检测专用关键词,稍微减少成分检测的错误率
  2.833:修复导航栏动态也显示检查按钮的问题
  2.832:文本改动
  2.831:加点提示信息
  2.83:修复一些bug
  2.82:使所有tag都可悬浮查看而不被遮挡(完善)
  2.81:使所有tag都可悬浮查看而不被遮挡,去除了一些在不必要的位置添加的按钮
*/
$(function () {

    //功能开关

    //动态检查
    const dynamicSwitch = true
    //关注检查
    const followingSwitch = true
    //投稿检查
    const videoSwitch = true

    // 在这里配置要检查的成分
    const checkers = [
        {
            displayName: "米系",
            // displayIcon: "https://i2.hdslb.com/bfs/face/d2a95376140fb1e5efbcbed70ef62891a3e5284f.jpg@240w_240h_1c_1s.jpg",
            keywords: ["原神","崩坏3","崩坏","崩坏星穹铁道","星穹铁道","绝区零","米哈游","崩坏学园2"],
            dynamicKeywords: ["#原神#","#miHoYo#","#崩坏3#","#崩坏星穹铁道#","#绝区零#","#米哈游#","#崩坏学园2#"],
            followings: [
                401742377,// 原神官方号的 UID
                27534330, // 崩坏3第一偶像爱酱
                256667467, // 崩坏3官方号
                1340190821, // 崩坏星穹铁道
                1636034895, // 绝区零
                133934, // 崩坏学园2-灵依娘desu
            ],
            found: []
        },
        {
            displayName: "职业",
            displayIcon: "",
            keywords: ["KPM","速通","KD","捞薯","单刷","最强","狗斗","AIM","百杀","秒杀","aim","Acc","acc","ACC","kd","kpm"],
            dynamicKeywords: ["KPM","速通","KD","捞薯","单刷","最强","狗斗","AIM","百杀","秒杀","aim","Acc","acc","ACC","kd","kpm"],
            followings: [],
            found: []
        },
        {
            displayName: "任天堂",
            displayIcon: "",
            keywords: ["任天堂","Nintendo","塞尔达","旷野之息","switch","王国之泪","猎天使魔女","nintendo","Switch"],
            dynamicKeywords: [],
            followings: [],
            found: []
        },
        {
            displayName: "主机",
            displayIcon: "",
            keywords: ["Playstation","PS4","PS5","XSX","XSS","playstation","ps4","ps5","xsx","xss"],
            dynamicKeywords: [],
            followings: [],
            found: []
        },
        {
            displayName: "宵宵人?",
            displayIcon: "",
            keywords: ["宵宫","yoimiya","Yoimiya"],
            dynamicKeywords: [],
            followings: [],
            found: []
            //私货
        },
        {
            displayName: "农药",
            displayIcon: "",
            keywords: ["王者荣耀"],
            dynamicKeywords: ["王者荣耀"],
            followings: [
                57863910, // 王者荣耀
                392836434, // 哔哩哔哩王者荣耀赛事
            ],
            found: []
        },
        {
            displayName: "土孝子",
            displayIcon: "",
            keywords: ["土豆猫"],
            dynamicKeywords: ["土豆猫"],
            followings: [
                1638082715, // 土豆历险记哟
                2013897740, // 有点小可爱儿
                435643527, // 喔喔喔06
            ],
            found: []
        },
        {
            displayName: "小战",
            displayIcon: "",
            keywords: ["战舰世界","战雷","战争雷霆"],
            dynamicKeywords: [],
            followings: [],
            found: []
        },
        {
            displayName: "PCR",
            displayIcon: "",
            keywords: ["公主连结","Re:Dive","PCR","BCR","公主连接","公主链接","ReDive","pcr","bcr"],
            dynamicKeywords: ["公主连结","公主连接","公主链接"],
            followings: [353840826], //公主连结ReDive
            found: []
        },
        {
            displayName: "APEX",
            displayIcon: "",
            keywords: ["APEX","apex"],
            dynamicKeywords: ["APEX","apex"],
            followings: [],
            found: []
        },
        {
            displayName: "LOL",
            displayIcon: "",
            keywords: ["英雄联盟","lol","LOL"],
            dynamicKeywords: ["英雄联盟","lol","LOL"],
            followings: [
                50329118, // 哔哩哔哩英雄联盟赛事
                178778949, // 英雄联盟
            ],
            found: []
        },
        {
            displayName: "COD",
            displayIcon: "",
            keywords: ["COD","CallOfDuty","使命召唤","cod"],
            dynamicKeywords: ["COD","CallOfDuty","使命召唤","cod"],
            followings: [],
            found: []
        },
        {
            displayName: "粥粥人",
            displayIcon: "",
            keywords: ["明日方舟"],
            dynamicKeywords: ["明日方舟"],
            followings: [161775300], // 明日方舟
            found:[]
        },
        {
            displayName: "我去初音未来",
            displayIcon: "",
            keywords: ["初音未来","miku","葱厨","MIKU"],
            dynamicKeywords: ["初音未来","miku"],
            followings: [399918500], // 初音未来_Crypton
            found:[]
        },
        {
            displayName: "哈哈VTB天狗",
            displayIcon: "",
            keywords: ["東雪蓮","东雪莲","七海Nana7mi","七海辣辣米","塔菲","永雏塔菲","猫雷","天气阿准"],
            dynamicKeywords: ["東雪蓮","东雪莲","七海Nana7mi","七海辣辣米","塔菲","永雏塔菲","猫雷","天气阿准"],
            followings: [
                434334701, // 七海Nana7mi
                1437582453, // 東雪蓮Official
                1265680561, // 永雏塔菲
                697091119, // 猫雷NyaRu_Official
                490981706, // 天气阿准official
            ],
            found: []
        },
        {
            displayName: "战批",
            displayIcon: "",
            keywords: ["战地1","BF2042","bf2042","BF1","BF4","BF3","BF5","BFV","战地5","战地风云","Battlefield","战地3","战地4","战地1942","战地硬仗","战地2042","BFH","西奈沙漠","钉钉机","阿尔贡森林","bf1","bf4","bf5","bfv","bfh","battlefield"],
            dynamicKeywords: ["战地1","BF2042","bf2042","BF1","BF4","BF3","BF5","BFV","战地5","战地风云","Battlefield","战地3","战地4","战地1942","战地硬仗","战地2042","BFH","西奈沙漠","钉钉机","阿尔贡森林","bf1","bf4","bf5","bfv","bfh","battlefield"],
            followings: [
                381399962, // 战地风云2042
                2860983, //咖喱FPS
            ],
            found: []
        },
        {
            displayName: "幻塔",
            displayIcon: "",
            keywords: ["幻塔"],
            dynamicKeywords: ["幻塔手游","《幻塔》"],
            followings: [
                586631367 // 幻塔手游
            ],
            found: [],
            uid: []
        },
        {
            displayName: "A手",
            // displayIcon: "https://i2.hdslb.com/bfs/face/43b21998da8e7e210340333f46d4e2ae7ec046eb.jpg@240w_240h_1c_1s.jpg",
            keywords: ["A-SOUL_Official", "A_SOUL#","asoul","ASOUL","嘉然","乃琳","珈乐","向晚","贝拉"],
            dynamicKeywords: ["嘉然","乃琳","珈乐","向晚","贝拉"],
            followings: [
                672328094, // 嘉然今天吃什么
                703007996, // Asoul
                547510303, // Asoul二创计画
                672342685, // 乃琳Queen
                351609538, // 珈乐Carol
                672346917, // 向晚大魔王
                672353429 // 贝拉kira
            ],
            found: []
        }
    ]

    // 空间动态api
    const spaceApiUrl = 'https://api.bilibili.com/x/polymer/web-dynamic/v1/feed/space?&host_mid='
    const followingApiUrl = 'https://api.bilibili.com/x/relation/followings?vmid='
    const arcApiUrl = 'https://api.bilibili.com/x/space/arc/search?mid='
    //&pn=页码

    const checked = {}
    const checking = {}
    var printed = true

    // 监听用户ID元素出现
    waitForKeyElements(".user-info .user-name", installCheckButton);
    waitForKeyElements(".sub-user-name", installCheckButton);
    waitForKeyElements(".con  .user .name", installCheckButton);
    waitForKeyElements("#h-name", installCheckButton);

    // console.log("开启B站用户成分检查器Pro...")

    // 添加检查按钮
    function installCheckButton(element) {
        let node = $(`<div style="display: inline;" class="composition-checkable"><div class="composition-badge">
  <a class="composition-name">查</a>
</div></div>`)

        node.on('click', function () {
            node.find(".composition-name").text(checkingText)
            checkComposition(element, node.find(".composition-name"))
        })

        element.after(node)
    }

    const checkingText = "检查中,鼠标悬浮可显示具体信息,且建议同时只检查一个用户,否则悬停信息将出现bug"

    // 添加标签
    function installComposition(id, element, setting) {
        let node = $(`
        <div style="display: inline;">
          <div class="composition-badge">
            <a class="composition-name" title="${setting.found}">${setting.displayName}</a>
          </div>
        </div>`)

//         let node = $(`<div style="display: inline;"><div class="composition-badge">
//   <a class="composition-name">${setting.displayName}</a>
//   <img src="${setting.displayIcon}" class="composition-icon">
// </div></div>`)
        element.after(node)
    }

    function installErrorComposition(id, element, text) {
        let node = $(`
        <div style="display: inline;">
          <div class="composition-badge-error">
            <a class="composition-name">${text}</a>
          </div>
        </div>`)
        element.after(node)
    }

    // 检查标签
    function checkComposition(element, loadingElement) {
        // 用户ID
        let userID = element.attr("data-user-id") || element.attr("data-usercard-mid") || $('.n-btn').filter(".n-dynamic").attr('href').split('/')[1]
        // 用户名
        let name = element.text().charAt(0) == "@" ? element.text().substring(1) : element.text()

        if (checked[userID] != undefined) {
            // 已经缓存过了
            let found = checked[userID]
            if (found.length > 0) {
                for (let setting of found) {
                    installComposition(userID, element, setting)
                }
                loadingElement.parent().remove()
            } else {
                loadingElement.text('无')
            }
        } else if (checking[userID] != undefined) {
            // 检查中
            if (checking[userID].indexOf(element) < 0)
                checking[userID].push(element)
        } else {
            checking[userID] = [element]
            console.log("正在检查用户 " + name + " 的成分...");

            new Promise(async (resolve, reject) => {
                try {
                    // 找到的匹配内容
                    let found = []

                    let spaceRequest = request({
                        data: "",
                        url: spaceApiUrl + userID,
                    })

                    let followingRequest = request({
                        data: "",
                        url: followingApiUrl + userID,
                    })

                    let videoRequest = request({
                        data: "",
                        url: arcApiUrl + userID,
                    })


//-----------------------------------------------
                    if(dynamicSwitch){
                        try {
                            let spaceContent = await spaceRequest

                            if (!printed) {
                                console.log(spaceContent)
                                printed = true
                            }

                            // 动态内容检查
                            if (spaceContent.code == 0) {
                                // 解析并拼接动态数据
                                // let st = JSON.stringify(spaceContent.data.items)
                                // let st = JSON.stringify(spaceContent.data.items.map(it => it.modules.module_dynamic.desc))
                                let st = JSON.stringify(spaceContent.data.items.map(it => it.orig))

                                for (let setting of checkers) {
                                    // 检查动态内容
                                    if (setting.keywords) {
                                        loadingElement.text("动态"+checkingText)
                                        if (setting.dynamicKeywords.find(keyword => st.includes(keyword))) {
                                            // setting.found.push("【动态】"+setting.keywords.find(keyword => st.includes(keyword)))
                                            if (found.indexOf(setting) < 0){
                                                setting.found.push("【动态】"+setting.dynamicKeywords.find(keyword => st.includes(keyword)))
                                                found.push(setting)
                                                // setting.found = []
                                            }else{
                                                found[found.indexOf(setting)].found.push("【动态】"+setting.dynamicKeywords.find(keyword => st.includes(keyword)))
                                            }
                                        }
                                    }

                                }
                            }
                        }catch(error) {
                            installErrorComposition(userID, element, "动态读取失败")
                            // console.error(`获取 ${name} ${userID} 的动态失败`, error)
                        }
                    }
                    if(videoSwitch){
                        try {
                            let videoContent = await videoRequest

                            if (!printed) {
                                console.log(videoContent)
                                printed = true
                            }

                            // 投稿内容检查
                            if (videoContent.code == 0) {
                                // 解析并拼接投稿数据
                                // let st = JSON.stringify(videoContent.data.list)
                                let st = JSON.stringify(videoContent.data.list.vlist.map(it => it.title))
                                // console.log(st)
                                let count = JSON.stringify(videoContent.data.page.count)

                                let tempFound = []
                                for (let setting of checkers) {
                                    loadingElement.text("投稿第1页"+checkingText)
                                    // 检查投稿内容
                                    if (setting.keywords) {
                                        if (setting.keywords.find(keyword => st.includes(keyword))) {
                                            // setting.found.push("【投稿】"+setting.keywords.find(keyword => st.includes(keyword)))
                                            if (found.indexOf(setting) < 0){
                                                setting.found.push("【投稿】"+setting.keywords.find(keyword => st.includes(keyword)))
                                                found.push(setting)
                                                // setting.found = []
                                            }else{
                                                found[found.indexOf(setting)].found.push("【投稿】"+setting.keywords.find(keyword => st.includes(keyword)))
                                            }
                                        }
                                    }
                                }

                                let videoPageTotal = Math.ceil(count/30)
                                for(let i=2; i <= videoPageTotal; i++){

                                    let videoRequestTemp = request({
                                        data: "",
                                        url: arcApiUrl + userID + "&pn=" + i,
                                    })

                                    let videoContent = await videoRequestTemp

                                    if (!printed) {
                                        console.log(videoContent)
                                        printed = true
                                    }

                                    // 投稿标题检查
                                    if (videoContent.code == 0) {
                                        // 解析并拼接投稿数据
                                        let stt = JSON.stringify(videoContent.data.list.vlist.map(it => it.title))
                                        // console.log(stt)

                                        for (let setting of checkers) {
                                            loadingElement.text("投稿第"+i+"页"+checkingText)
                                            // 检查投稿内容
                                            if (setting.keywords) {

                                                if (setting.keywords.find(keyword => stt.includes(keyword))) {
                                                    // setting.found.push("【投稿】"+setting.keywords.find(keyword => stt.includes(keyword)))
                                                    if (found.indexOf(setting) < 0){
                                                        setting.found.push("【投稿】"+setting.keywords.find(keyword => stt.includes(keyword)))
                                                        found.push(setting)
                                                        // setting.found = []
                                                    }else{
                                                        found[found.indexOf(setting)].found.push("【投稿】"+setting.keywords.find(keyword => stt.includes(keyword)))
                                                    }
                                                }
                                            }
                                        }
                                    }
                                }
                            }
                        }catch(error) {
                            installErrorComposition(userID, element, "投稿读取失败")
                            // console.error(`获取 ${name} ${userID} 的投稿失败`, error)
                        }
                    }
                    if(followingSwitch){
                        try {
                            for(let pn=1; pn<=5; pn++){

                                let followingRequestTemp = request({
                                    data: "",
                                    url: followingApiUrl + userID + "&pn=" + pn,
                                })

                                let followingContent = await followingRequestTemp

                                // 可能无权限
                                // let following = followingContent.code == 0 ? followingContent.data.list.map(it => it.mid) : []

                                let followingUID = []
                                let followingName = []

                                if(followingContent.code == 0){
                                    followingUID = followingContent.data.list.map(it => it.mid)
                                    followingName = followingContent.data.list.map(it => it.uname)
                                }
                                else{
                                    followingUID = []
                                    followingName = []
                                }

                                let list = JSON.stringify(followingContent.data.list)
                                if(list=='[]') break

                                if (followingUID) {
                                    for (let setting of checkers) {
                                        loadingElement.text("关注第"+pn+"页"+checkingText)
                                        // 检查关注列表
                                        if (setting.followings){
                                            for (let mid of setting.followings) {

                                                if (followingUID.indexOf(mid) >= 0) {
                                                    // setting.found.push("【关注】"+ followingName[followingUID.indexOf(mid)])
                                                    if (found.indexOf(setting) < 0){
                                                        setting.found.push("【关注】"+ followingName[followingUID.indexOf(mid)])
                                                        found.push(setting)
                                                    }else{
                                                        found[found.indexOf(setting)].found.push("【关注】"+ followingName[followingUID.indexOf(mid)])
                                                    }

                                                    // continue;
                                                }
                                            }

                                        }
                                    }
                                }else{
                                    break
                                }
                            }
                        }catch(error) {
                            installErrorComposition(userID, element, "关注读取失败,可能其设置了隐私")
                            // console.error(`获取 ${name} ${userID} 的关注列表失败`, error)
                        }
                    }

                    // 添加标签
                    if (found.length > 0) {
                        // 输出日志
                        // console.log(`检测到 ${name} ${userID} 的成分为 `, found.map(it => it.displayName))

                        checked[userID] = found


                        // 给所有用到的地方添加标签
                        for (let element of checking[userID]) {
                            for (let settingOfFound of found) {
                                installComposition(userID, element, settingOfFound)
                                settingOfFound.found = []
                            }
                        }
                        loadingElement.parent().remove()
                    } else {
                        loadingElement.text('无')
                    }

                    checked[userID] = found
                    delete checking[userID]

                    resolve(found)
                }
                catch (error){
                    console.error(`检测 ${name} ${userID} 的成分失败`, error)
                    loadingElement.text('失败')
                    delete checking[userID]
                    // reject(error)
                }
            })
        }
    }

    // 添加标签样式
    addGlobalStyle(`
.composition-badge {
  display: inline-flex;
  justify-content: center;
  align-items: center;
  width: fit-content;
  background: #00AEEC26;
  border-radius: 10px;
  margin: -6px 0;
  margin: 0 5px;
  font-family: PingFang SC, HarmonyOS_Regular, Helvetica Neue, Microsoft YaHei, sans-serif;
}
.composition-badge-error {
  display: inline-flex;
  justify-content: center;
  align-items: center;
  width: fit-content;
  background: #FF222222;
  border-radius: 10px;
  margin: -6px 0;
  margin: 0 5px;
  font-family: PingFang SC, HarmonyOS_Regular, Helvetica Neue, Microsoft YaHei, sans-serif;
}
.composition-name {
  line-height: 13px;
  font-size: 13px;
  color: #00AEEC;
  padding: 2px 8px;
}
.composition-icon {
  width: 25px;
  height: 25px;
  border-radius: 50%;
  border: 2px solid white;
  margin: -6px;
  margin-right: 5px;
}
.composition-name:hover {
  color: #f25d8e;
  cursor:pointer;
}
.bb-comment .sailing, .comment-bilibili-fold .sailing {
  pointer-events: none;
}
.reply-item .root-reply-container .content-warp .reply-decorate {
  pointer-events: none;
}
    `)

    function addGlobalStyle(css) {
        var head, style;
        head = document.getElementsByTagName('head')[0];
        if (!head) { return; }
        style = document.createElement('style');
        style.type = 'text/css';
        style.innerHTML = css;
        head.appendChild(style);
    }

    function request(option) {
        return new Promise((resolve, reject) => {
            let requestFunction = GM_xmlhttpRequest ? GM_xmlhttpRequest : GM.xmlHttpRequest

            requestFunction({
                method: "get",
                headers: {
                    'user-agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/104.0.0.0 Safari/537.36'
                },
                ...option,
                onload: (response) => {
                    let res = JSON.parse(response.responseText)
                    resolve(res)
                },
                onerror: (error) => {
                    reject(error);
                }
            });
        })
    }

    /*--- waitForKeyElements():  A utility function, for Greasemonkey scripts,
    that detects and handles AJAXed content.
    Usage example:
        waitForKeyElements (
            "div.comments"
            , commentCallbackFunction
        );
        //--- Page-specific function to do what we want when the node is found.
        function commentCallbackFunction (jNode) {
            jNode.text ("This comment changed by waitForKeyElements().");
        }
    IMPORTANT: This function requires your script to have loaded jQuery.
    */
    function waitForKeyElements(selectorTxt, actionFunction, bWaitOnce, iframeSelector) {
        var targetNodes, btargetsFound;

        if (typeof iframeSelector == "undefined")
            targetNodes = $(selectorTxt);
        else
            targetNodes = $(iframeSelector).contents()
                .find(selectorTxt);

        if (targetNodes && targetNodes.length > 0) {
            btargetsFound = true;
            targetNodes.each(function () {
                var jThis = $(this);
                var alreadyFound = jThis.data('alreadyFound') || false;

                if (!alreadyFound) {
                    //--- Call the payload function.
                    var cancelFound = actionFunction(jThis);
                    if (cancelFound) btargetsFound = false;
                    else jThis.data('alreadyFound', true);
                }
            });
        } else {
            btargetsFound = false;
        }

        //--- Get the timer-control variable for this selector.
        var controlObj = waitForKeyElements.controlObj || {};
        var controlKey = selectorTxt.replace(/[^\w]/g, "_");
        var timeControl = controlObj[controlKey];

        //--- Now set or clear the timer as appropriate.
        if (btargetsFound && bWaitOnce && timeControl) {
            //--- The only condition where we need to clear the timer.
            clearInterval(timeControl);
            delete controlObj[controlKey]
        } else {
            //--- Set a timer, if needed.
            if (!timeControl) {
                timeControl = setInterval(function () {
                    waitForKeyElements(selectorTxt, actionFunction, bWaitOnce, iframeSelector);
                }, 300);
                controlObj[controlKey] = timeControl;
            }
        }
        waitForKeyElements.controlObj = controlObj;
    }
})

```