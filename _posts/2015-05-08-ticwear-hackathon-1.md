---
layout: post
title: 记《步伐》手表版的诞生
description: "参加TicWear的Creatic Hackathon比赛，做了步伐的Android Wear版，说说它的产品设计"
headline: "参加TicWear的Creatic Hackathon比赛，做了步伐的Android Wear版，说说它的产品设计"
categories: design
tags:
  - 步伐
  - Ticwear
  - Hackathon
  - Android wear
  - Design
comments: true
mathjax: null
featured: true
published: true
---

这篇文章主要介绍《步伐》手表版的产品设计。

4月18~19日，我参加了TicWear的Creatic Hackathon比赛，做了个步伐的Android Wear版，[拿了个“大奖”](http://ask.ticwear.com/?/article/7)。
Hackathon 真的是一项非常不错的活动，在极短时间内，完成一项颇具挑战的事情。
如果不是这个马拉松，估计做这个手表版至少得一个星期。
就像评委柯老师说的那样，在有限的条件下，能心无杂念的去完成一件事情，可能激发出无限可能。

<!--break-->

这篇文章，只谈产品设计。
至于为何我时隔两个星期才开始总结，可以看看我的[这篇文章]({% post_url 2015-05-07-indie-or-teamwork %})。

在介绍比赛的详情前，我有必要先大致介绍下这次比赛作品的基础 —— [《步伐》](http://app.tankery.me/pace/cn/)。

《步伐》是一款专为跑友们设计的本地音乐播放器，它只播放与你跑步频率相匹配的音乐。
从技术上来说，步伐做的事情是识别你的步频、并扫描分析手机曲库中的歌曲，提取出歌曲频率，然后在曲库中寻找与步频相近甚至相等的歌曲。
其核心算法，在于步频识别以及歌曲频率分析这两块。
UI是下面这个样子：

![Pace plaing screenshot]({{ site.baseurl }}/images/post/ticwear-hackathon/playing.jpg "Pace plaing screenshot")

本次比赛采用的手表是Moto 360 搭载出门问问出品的Ticwear操作系统。
从UI上说，手表是圆形表盘，底部有个黑条，可以通过手势操作应用，但从左往又滑动的操作已经被系统定义为退出应用的手势，不可用；

下面，我将从产品设计的角度，简单说说手表端《步伐》的创作过程。

我对手表的理解，首先是一个可穿戴设备，它离人更近（不光是距离，还有交互的便捷性），但屏幕更小。
由于距离人近，手表上的传感器相比手机，能更准确的识别人的动作和身体状况；又因为抬手这一动作的便捷，使得消息通知能被更快的反应；而语音交互，使得我们可以解放双手。
但由于屏幕很小，我们的界面设计必须比手机更加精简、交互设计必须比手机更加粗放（少点击、多滑动）。

具体到《步伐》的手表版上来说，我需要做了下面几件事情：

 1. 充分利用手表的传感器，将步频识别模块移植到手表上，而理解手表的限制，保留手机的音乐分析模块；
 2. 理解手表的交互便捷性，将应用的音乐控制延伸到手表；
 3. 重新设计手表的UI，使其更精简、操作更粗放；
 4. 额外添加对语音控制的支持，增加无手操作的可能。

那么，从技术上来说，需要移植步频识别模块、通过数据通讯连接手表和手机、并增加语音的支持。
从设计上，需要设计一套圆形表盘的精简版UI，并定义合理的交互控制方式。

由于界面精简和交互粗放化的需要，我首先想到的是需要去除底部的三个按钮，改用手势的方式控制。
另外，将音乐时间、播放列表等不太重要的信息去除。
利用圆形表盘的特点，考虑到黑色条，将播放进度调整到屏幕边缘。
再精简步频的显示，将音乐名称和作者，放到手表中部显眼的位置，考虑到标题一般比名字长，将标题移动到更中间的位置。

于是就有了下面的手表设计图：

![Pace playing wear]({{ site.baseurl }}/images/post/ticwear-hackathon/playing-wear.png "Pace playing wear")

考虑到交互的粗放性，我采用上抛删除（有些抛弃的隐喻）、向左滑动切歌（内容跟随手指做阻尼运动）、向下滑动喜爱/不喜爱（爱心logo跟随手指做阻尼运动），这样的手势设计，而整个界面都可以点击播放/暂停。

可惜的是，最终由于比赛时间限制，我只简单的实现了上抛删除、左抛切歌、下抛喜爱这样的交互，也算差强人意吧。

