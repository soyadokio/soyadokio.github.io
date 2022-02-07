---
title: 合并B站下载的单独视频和单独音频
toc: false
comments: true
date: 2022-02-07 22:44:58
updated: 2022-02-07 22:44:58
categories:
  - 记录
tags:
  - ffmpeg
  - Bilibili
description:
---

好像从2020年开始，用IDM从B站下载视频时会出现只能分别下载独立视频和独立音频的问题，那么就需要下载后手动合并了。

<!-- more -->

## 使用ffmpeg合并音视频

### 合并一个视频

命令：
```
ffmpeg -i input_video.m4s -i input_audio.m4s -codec copy output.mp4
```

其中 `-i` 表示输入文件选项，这里因为视频和音频是相互独立的，所以用两个输入文件分别表示，没有特定顺序。`-codec` 表示输出文件编码选项，这里 `-codec copy` 表示流复制，它只是对输入文件解封装和再封装，而省略了中间的解码和编码步骤，因此速度很快且无损。

### 批量合并视频

批处理命令：
```batch
@echo off
for /l %%i in (0,1,11) do (ffmpeg -i video%%i.m4s -i audio%%i.m4s -codec copy output%%i.mp4)
pause
```

这里假设我们在同一文件夹下有12个视频需要合并，且单独视频的文件名为 `video0.m4s`、`video1.m4s`、... 单独音频的文件名为 `audio0.m4s`、`audio1.m4s`、...

其中 `for /l` 表示`计数循环`，`(0,1,11)` 表示起始值为0，步长为1，中止值为11。


## 使用插件直接下载带音轨的视频

这里推荐油猴插件上的脚本[Bilibili-Evolved](https://github.com/the1812/Bilibili-Evolved)，其中就有下载视频各个清晰度的功能，甚至还有下载整个系列的功能。

我已经使用了一年多的时间，各个设置选项也都详细地看了一遍。作者的定义是「 强大的哔哩哔哩增强脚本 」，个人觉得名副其实，很值得推荐。
