---
title: 'b站番剧评论区时间轴跳转功能竟然无效？害我白花时间写脚本'
date: 2022-01-30T6:00:00+08:00
keywords:
  - '文章'
---
本想写个pc web端tampermoneky脚本，一键在番剧中自动快进88秒进度条来实现快速跳过op的小功能，没想到一通代码操作下来，笑死 根本没用

<!--more-->

明明在正常bv号下是点击评论区里的时间轴跳转是正常的 但是番剧下的点击是不会跳转的 

我翻半天评论区总算找到一个发了时间轴评论的 点了之后才发现根本不跳转

那我只能说白花了时间 吐了

> 但是不能白写 先水一个帖子

源代码：
```
// ==UserScript==
// @name         BilibiliBangumiSkipOP
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  try to take over the world!
// @author       Himesamanoyume
// @match        https://www.bilibili.com/bangumi/play/*
// @require     https://cdn.bootcdn.net/ajax/libs/jquery/2.2.4/jquery.min.js
// @icon         https://www.google.com/s2/favicons?domain=bilibili.com
// @grant        none
// ==/UserScript==
jQuery(function ($) {
    'use strict';

    $(document).ready(function(){
        $(document).keydown(function(event){
            //按下“/”键触发
            if(event.keyCode == 191){
                var time_span = $('.squirtle-video-time-now')[0];
                var time = time_span.textContent;

                var time_to_sec = timeFunc(time);
                if (window.commentAgent && typeof window.commentAgent.seek === 'function') {
                    window.commentAgent.seek(time_to_sec+88);
                    window.scrollTo(0, 0);
                };
            };
        });
    })
    function timeFunc(time) {
        var s = '';
        var hour = 0;
        var min = 0;
        var sec =0;
        var arr = time.split(':');
        if(arr.length>=3){
            hour = time.split(':')[0];
            min = time.split(':')[1];
            sec = time.split(':')[2];
        }else{
            min = time.split(':')[0];
            sec = time.split(':')[1];
        }
        s = Number(hour*3600) + Number(min*60) + Number(sec); return s; };
});
```

只能试试看看直接用输入时间轴回车跳转的方式能不能成功了。

---

好耶 Tampermonkey有一脚本 <a href="https://github.com/the1812/Bilibili-Evolved" target="_blank">Bilibili-Evolved</a> 

安装脚本后再单独安装“快捷键扩展”功能 里面自带跳转功能 别人造好了轮子 我就没必要再自己弄了 舒服啊！