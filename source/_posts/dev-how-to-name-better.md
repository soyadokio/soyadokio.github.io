---
title: 怎样给文件、变量和函数命名？
toc: true
comments: true
date: 2023-07-04 15:27:35
updated: 2023-07-04 15:27:35
categories:
  - 编程
tags:
  - 编程
  - 命名
description: 给文件、函数、变量命名是一件很难的事，本文是一个归纳总结。
---

> 本文转载自[怎样给文件、变量和函数命名？](https://www.voidking.com/dev-how-to-name-better/)

## 前言

使用 user_tool.py 还是 user_utils.py？使用 name 还是 username？使用 user_add 还是 add_user？使用 get_user_by_name 还是 get_users_by_name？等等等等，在编程活动中，我们经常会产生各种关于命名的纠结。

给文件、函数、变量命名是一件很难的事，但是也是有方法的。本文中，我们就来学习一下文件、变量和函数命名的方法。

参考文档：

- [工程实践：给函数取一个”好”的名字](https://www.cnblogs.com/dolphin0520/p/10567879.html)
- [Google 开源项目风格指南 (中文版)](https://github.com/zh-google-styleguide/zh-google-styleguide)
- [命名规范](https://leohxj.gitbooks.io/a-programmer-prepares/content/programmer-basic/naming.html)

## 命名方法

要领：一看就懂，保持一致。

## 文件

由于 Windows, OSX 下文件名不区分大小写(linux 是区分的)，所以命名建议还是以全部小写为主。
连字符可以使用中划线、下划线或者省略，关键是要统一。

目录建议连字符使用中划线，比如: my-project-name。
有复数的情况使用复数命名法，比如: scripts, styles, images 和 data-modules。
文件建议连字符使用下划线，比如：user_test.py。

## 变量

变量命名常用的有两种方式:
下划线命名法，比如: my_variable
驼峰式命名法，比如: myVariale

python 语言建议使用下划线命名法。

## 函数

函数命名常用的有两种方式:
下划线命名法，比如: get_user_by_name
驼峰式命名法，比如: getUserByName

python 语言建议使用下划线命名法。不同于变量命名的是，函数名称要使用动词开头，并且尽可能准确。

## 常用动词表

动词选取要精准。通常来说，动词决定了一个函数要采取什么”动作”。动词取的好，一个函数名字已经成功了 80%。

常用动词表：
| 类别 | 单词 |
| :--- | :--- |
| 添加/插入/创建/初始化/加载 | add、append、insert、create、initialize、load |
| 删除/销毁 | delete、remove、destroy、drop |
| 打开/开始/启动 | open、start |
| 关闭/停止 | close、stop |
| 获取/读取/查找/查询 | get、fetch、acquire、read、search、find、query |
| 设置/重置/放入/写入/释放/刷新 | set、reset、put、write、release、refresh |
| 发送/推送 | send、push |
| 接收/拉取 | receive、pull |
| 提交/撤销/取消 | submit、cancel |
| 收集/采集/选取/选择 | collect、pick、select |
| 提取/解析 | sub、extract、parse |
| 编码/解码 | encode、decode |
| 填充/打包/压缩 | fill、pack、compress |
| 清空/拆包/解压 | flush、clear、unpack、decompress |
| 增加/减少 | increase、decrease、reduce |
| 分隔/拼接 | split、join、concat |
| 过滤/校验/检测 | filter、valid、check |

## 常用领域词

名词使用领域词汇。举个例子：集合的容量通常用 capacity、集合实际元素个数用 size、字符串长度用 length，这种就遵循大家的使用习惯，不要用 size 去形如字符串的长度。

再比如，假如使用到建造者模式，那么通常会用 build 作为函数名字，这个时候就不要另辟蹊径，用 create 来作为函数名字，使用大家约定俗成的命名习惯更容易让你的代码被别人读懂。

常用名词表：
| 类别 | 单词 |
| :--- | :--- |
| 容量/大小/长度 | capacity、size、length |
| 实例/上下文 | instance、context |
| 配置 | config、settings |
| 头部/前面/前一个/第一个 | header、front、previous、first |
| 尾部/后面/后一个/最后一个 | tail、back、next、last |
| 区间/区域/某一部分/范围/规模 | range、interval、region、area、section、scope、scale |
| 缓存/缓冲/会话 | cache、buffer、session |
| 本地/局部/全局 | local、global |
| 成员/元素 | member、element |
| 菜单/列表 | menu、list |
| 源/目标 | source、destination、target |

## 常用缩写表

1. 本缩写表是《编码命名规范》的附录。
1. 本缩写表中列出的都是通用性缩写，不提供标准缩写，如：Win9x、COM 等。
1. 使用本缩写表里的缩写时，请对其进行必要的注释说明。
1. 除少数情况以外，大部分缩写与大小写无关。

| 缩写       | 全称                              |
| :--------- | :-------------------------------- |
| addr       | Address                           |
| adm        | Administrator                     |
| app        | Application                       |
| arg        | Argument                          |
| asm        | assemble                          |
| asyn       | asynchronization                  |
| avg        | average                           |
| DB         | Database                          |
| bk         | back                              |
| bmp        | Bitmap                            |
| btn        | Button                            |
| buf        | Buffer                            |
| calc       | Calculate                         |
| char       | Character                         |
| chg        | Change                            |
| clk        | Click                             |
| clr        | color                             |
| cmd        | Command                           |
| cmp        | Compare                           |
| col        | Column                            |
| coord      | coordinates                       |
| cpy        | copy                              |
| ctl/ctrl   | Control                           |
| cur        | Current                           |
| cyl        | Cylinder                          |
| dbg        | Debug                             |
| dbl        | Double                            |
| dec        | Decrease                          |
| def        | default                           |
| del        | Delete                            |
| dest/dst   | Destination                       |
| dev        | Device                            |
| dict       | dictionary                        |
| diff       | different                         |
| dir        | directory                         |
| disp       | Display                           |
| div        | Divide                            |
| dlg        | Dialog                            |
| doc        | Document                          |
| drv        | Driver                            |
| dyna       | Dynamic                           |
| env        | Environment                       |
| err        | error                             |
| ex/ext     | Extend                            |
| exec       | execute                           |
| flg        | flag                              |
| frm        | Frame                             |
| func/fn    | Function                          |
| grp        | group                             |
| horz       | Horizontal                        |
| idx/ndx    | Index                             |
| img        | Image                             |
| impl       | Implement                         |
| inc        | Increase                          |
| info       | Information                       |
| init       | Initial/Initialize/Initialization |
| ins        | Insert                            |
| inst       | Instance                          |
| INT/intr   | Interrupt                         |
| len        | Length                            |
| lib        | Library                           |
| lnk        | Link                              |
| log        | logical                           |
| lst        | List                              |
| max        | maximum                           |
| mem        | Memory                            |
| mgr/man    | Manage/Manager                    |
| mid        | middle                            |
| min        | minimum                           |
| msg        | Message                           |
| mul        | Multiply                          |
| num        | Number                            |
| obj        | Object                            |
| ofs        | Offset                            |
| org        | Origin                            |
| param      | Parameter                         |
| pic        | picture                           |
| pkg        | package                           |
| pnt/pt     | Point                             |
| pos        | Position                          |
| pre/prev   | previous                          |
| prg        | program                           |
| prn        | Print                             |
| proc       | Process                           |
| prop       | Properties                        |
| psw        | Password                          |
| ptr        | Pointer                           |
| pub        | Public                            |
| rc         | rect                              |
| ref        | Reference                         |
| reg        | Register                          |
| req        | request                           |
| res        | Resource                          |
| ret        | return                            |
| rgn        | region                            |
| scr        | screen                            |
| sec        | Second                            |
| seg        | Segment                           |
| sel        | Select                            |
| src        | Source                            |
| std        | Standard                          |
| stg        | Storage                           |
| stm        | Stream                            |
| str        | String                            |
| sub        | Subtract                          |
| sum        | summation                         |
| svr        | Server                            |
| sync       | Synchronization                   |
| sys        | System                            |
| tbl        | Table                             |
| temp/tmp   | Temporary                         |
| tran/trans | translate/transation/transparent  |
| tst        | Test                              |
| txt        | text                              |
| unk        | Unknown                           |
| upd        | Update                            |
| upg        | Upgrade                           |
| util       | Utility                           |
| var        | Variable                          |
| ver        | Version                           |
| vert       | Vertical                          |
| vir        | Virus                             |
| wnd        | Window                            |
