---
title: 自定义SSH登录前提示信息
date: 2020-06-12 09:47:00
updated: 2020-06-12 09:47:00
toc: false
comments: true
categories:
  - Linux
tags:
  - 强迫症
description: 看游戏HackTheGame的SSH登录提示信息好帅
---

![▲ SSH登录前提示信息](1.png)

修改 `/etc/ssh/sshd_config` ，找到 `# Banner` ，新增一行或解开注释，内容为：

```
Banner /etc/ssh/banner
```

随后创建文件 `/etc/ssh/banner` ，自定义所需内容即可，也可参考当前目录下 `banner` 。

最后执行以下命令即可生效：

``` bash
service sshd restart
```

或

``` bash
systemctl restart sshd
```

附上自己的 [banner](banner) 作为例子：
```
#####################################################################
#                     Welcome to SDokio.cn                          #
#                                                                   #
#           All connections are monitored and recorded              #
#     Disconnect IMMEDIATELY if you are not an authorized user!     #
#####################################################################
```
