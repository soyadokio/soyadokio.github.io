---
title: Hexo：搭建博客
toc: true
comments: true
date: 2020-09-02 13:48:20
updated: 2020-09-02 13:48:20
categories:
  - 博客
tags:
  - Hexo
description:
---

记录从在 Github 建立 repository 开始，到博客部署的博客建站过程。本文还包含博文版本控制、多端协作、自动部署等内容。

<!-- more -->

## 目标及思路
本文有如下几个目标：
- 建立本地博客
- 部署博客到 GitHub Pages
- 对博文源文件进行版本控制
- 持续集成/持续部署

前两条很容易理解，写博客当然是希望能发布在互联网上广而告之，选`GitHub Pages`是因为它有微软背书，可靠性上应该没啥问题。那一个小小博客又不是什么大项目，为何要版本控制呢？

早期的Hexo建博教程中，大多是使用`Hexo工作文件`在本地生成Web文件后将其上传到`GitHub Pages`进行部署。这里有个问题，万一本地电脑遗失，或遭遇磁盘损坏等不可抗力因素导致`Hexo工作文件`丢失，那想要继续更新博客就得重建之前的`Hexo工作文件`，光想想就是一件很麻烦的事。所以，发布的Web文件可以不用版本控制，但`Hexo工作文件`（含Hexo环境和博文源文件）就得版本控制以备万一之需了。

至于最后一条目标，接触过持续集成/持续部署的朋友可能很好理解，这又是一项偷懒罢了。每次通过Hexo将博文源文件生成Web文件后还得上传到GitHub Pages才算发布成功，这样究竟太过麻烦，而使用持续集成/持续部署后，我只负责上传保存博文源文件，剩下的编译、生成、打包、上传、发布，全部让`GitHub Actions`替我完成，它不香吗？

## 建立本地博客
Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）渲染文章，在几秒内，即可利用靓丽的主题生成静态网页。

<font color=#aaaaaa size=2>注：若要执行Hexo命令需先安装Git和Node.js环境，可参考 [Hexo官方文档](https://hexo.io/zh-cn/docs/#安装)</font>

### 安装Hexo
使用 npm 安装 Hexo。
```
$ npm install -g hexo-cli
```

# 未完待续...（可是不想写了，之后如果有这个闲情再说吧）

## 参考文献
[1]silaoA.hexo+github pages搭建博客站全过程记录[EB/OL].[https://silaoa.github.io/2019/2019-04-18-hexo-github-pages建博客站全过程记录.html](https://silaoa.github.io/2019/2019-04-18-hexo-github-pages建博客站全过程记录.html),2019-04-18.
[2]yifanzheng.使用 GitHub Actions 自动部署 Hexo 博客到 GitHub Pages[EB/OL].[https://juejin.im/post/6854573218779381773](https://juejin.im/post/6854573218779381773),2020-07-25.
[3]Hexo官方.Hexo官方文档[EB/OL].[https://hexo.io/zh-cn/docs/](https://hexo.io/zh-cn/docs/),2020-08-31.
