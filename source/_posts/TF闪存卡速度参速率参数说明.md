---
title: TF闪存卡速度参速率参数说明
toc: true
comments: true
date: 2021-01-27 14:00:06
updated: 2021-01-27 14:00:06
categories:
tags:
description:
---

关于TF卡最低写入速率的4种规范/标准的说明。

<!-- more -->

## SD卡和TF卡
Secure Digital全名为Secure Digital Memory Card，中文直译为`安全数码卡`，官方一般将之缩写为SD。SD卡的技术是建基于MultiMediaCard格式上。由SD Association（SDA，SD协会）推出。SD卡分为SD、miniSD、microSD三种规范。
![▲ 由上至下分别为SD、miniSD、microSD](sd_cards.png)

### SD|SDHC|SDXC
SD协会官方定义的3种等级的速率标准，由于分别应用于3种尺寸不同的SD卡，故3种卡分别以此命名。
SDHC=SD High Capacity，SDXC=SD Extended Capacity

### 历史
microSD卡原本称为TF卡（T-Flash卡或TransFlash），由摩托罗拉和闪迪共同研发，在2004年推出。不过闪迪无法自行将它推广普及化，前期仅有摩托罗拉的手机支持TransFlash。为了能将销路完全拓展，于是闪迪将TransFlash规格并入SD协会，成为SD家族产品之一，造就了目前使用最广泛的手机存储卡。TF卡重命名为microSD是并入SD协会的妥协。
![▲ 常见的TF卡](tf_card.png)
近几年TF卡这种历史称呼逐渐盖过microSD卡成为主流，可能是其名字更简短，也可能是厂商在背后发力，谁又知道呢。

## 性能标示规范
常见的TF卡最低写入速率规范/标准共有3种，这里做个统一说明。
![▲ 常见TF卡的各种标记](card_host_marks.jpg)

### Speed Class
SD卡提供不同的速率，它是按CD-ROM的150KB/s为1倍速（记作“1x”）的速率计算方法来计算的。
SD2.0的规范中对于SD卡的性能上分为如下若干等级：
* Class 0
包括低于Class 2和未标注Speed Class的情况；
* Class 2
能满足观看普通MPEG4 MPEG2的电影、SDTV、数码摄像机拍摄；
* Class 4
可以流畅播放高清电视（HDTV），数码相机连拍等需求；
* Class 6
满足单反相机连拍和专业设备的使用要求；
* Class 10
满足更高速率要求的存储需求。

注：Class等级是按8KB/s换算的，Class 4最低写入速率为4MB/s，Class 10表示最低写入速率为10MB/s

### UHS Speed Class
UHS-1 表示支持 UHS (Ultra High Speed, 超高速)接口，其带宽达到 104MB/s。但是这个速度只代表总线规格，并不代表闪存内部速率。

### Video Speed Class
Video Speed Class定义了录制高解析度和高画质(4K/8K)视频的需求，同时也具备支持下一代闪存（如3D NAND）的重要功能。此外，Video Speed Class也把录制HD (2K)的视频速度整合在其中。

## 不同速率TF卡的具体应用
![▲ SD卡速度分类](video_speed_class_01.jpg)
![▲ 视频格式](video_speed_class_02.jpg)

## 参考文献
[1]维基百科成员.SD卡[EB/OL].[https://zh.wikipedia.org/wiki/SD卡](https://zh.wikipedia.org/wiki/SD%E5%8D%A1),2020-09-26.
[2]KevinTan9.SD卡分类与速度等级[EB/OL].[https://www.cnblogs.com/KevinTan9/p/12205668.html](https://www.cnblogs.com/KevinTan9/p/12205668.html),2020-01-17.
[3]Huatai Huang.SD/TF卡速度等级[EB/OL].[https://cloud-atlas.readthedocs.io/zh_CN/latest/arm/hardware/sd_tf_card_speed_class.html](https://cloud-atlas.readthedocs.io/zh_CN/latest/arm/hardware/sd_tf_card_speed_class.html),2019.
