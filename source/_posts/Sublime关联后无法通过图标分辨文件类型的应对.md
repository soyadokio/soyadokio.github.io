---
title: Sublime关联常见文本格式后难以通过图标分辨文件类型的应对
date: 2022-04-12 11:13:18
updated: 2022-04-12 11:13:18
toc: true
comments: true
tags:
  - Sublime
  - 文件格式
  - 文件类型
categories:
  - 记录
description:
---

Windows平台，Sublime关联常见文本格式后，所有被关联格式的文件图标都变成了Sublime的Logo，导致难以通过图标分辨文件类型，这背离了文件图标分辨文件的初衷。那么如何使文件既可以用Sublime打开，又有清晰明了易于分辨的图标呢？今天终于决定腾出时间来应对这个问题。

<!-- more -->

## 操作

### 借助程序FileTypesMan的实现

#### 原理

**<font color="#d00">2022/4/19更新：在Win10上实测无效，即目前没有以知的好的方法解决这一问题</font>**

~~「关联程序」和「打开命令」是两个不一样操作。关联到一个「关联程序」的话就会共享图标；而设置「打开命令」并不影响关联程序。所以先把所有要改的格式的sublime关联去掉，然后通过关联到喜欢的程序改其图标，最后把open命令改成 `sublime.exe %1` 就可以了。~~

#### 步骤

1. ~~下载程序 [FileTypesMan](https://www.nirsoft.net/utils/filetypesman.zip) | [FileTypesMan for x64](https://www.nirsoft.net/utils/filetypesman-x64.zip) 后运行~~

2. ~~在左侧第一列「Extension」找到对应的文件类型，或者直接输入即可快速定位，如这里找 `.html` 就输入 `.html` 即可~~

3. ~~右键点击该行，在弹出的菜单中选择「Edit Selected File Type」或按快捷键F2，或双击该行，打开文件类型编辑窗口~~

![▲ 文件类型编辑窗口](FileTypesMan-1.png)

4. ~~清空「User Choice」输入框中的内容后点击「OK」关闭文件类型编辑窗口~~

5. ~~在下侧找到「open」命令的行右键单击，在弹出的菜单中选择「Edit Selected Action」或按快捷键F3，或双击该行，打开动作编辑窗口~~

![▲ 动作编辑窗口](FileTypesMan-2.png)

6. ~~在「Command-Line」输入框中输入`"C:\Program Files\Sublime Text 3\sublime_text.exe" "%1"`后点击「OK」关闭动作编辑窗口~~

![▲ 修改Command-Line](FileTypesMan-3.png)


### 借助程序Default Programs Editor的实现

1. 下载程序 [Default Programs Editor](https://defaultprogramseditor.com/files/DefaultProgramsEditor.zip) 后运行

1. 点击「File Type Settings」

![▲ 点击「File Type Settings」](DefaultProgramsEditor-1.png)

1. 点击「Icon」

![▲ 点击「Icon」](DefaultProgramsEditor-2.png)

1. 借助右上角的检索框在下方的文件类型清单中找到对应的文件类型，单击选中

![▲ 找到目标文件类型](DefaultProgramsEditor-3.png)

1. 点击「Next」按钮

1. 单击「Browse...」按钮，然后选中喜欢的图标，点击确定

![▲ 单击「Browse...」按钮](DefaultProgramsEditor-4.png)

![▲ 选择喜欢的图标](DefaultProgramsEditor-5.png)

1. 点击右下角按钮「Save Icon」即可应用

1. [可选]或者也可点击'Save Icon'按钮旁的下拉三角形图标，选中「Save to .reg file...」按钮，再选择保存目录，即可得到后缀为.reg的文件，方便传给别的电脑使用，使用时只许双击运行再点确定即可。
我看了下保存的.reg文件是这样的：
```
Windows Registry Editor Version 5.00

; Created with Default Programs Editor
; http://defaultprogramseditor.com/

; Edit File Type Icon
[HKEY_CURRENT_USER\Software\Classes\Applications\sublime_text.exe\DefaultIcon]
@="C:\\WINDOWS\\system32\\imageres.dll,97"
```
目测这个只是改了Sublime的图标，而不是我最开始希望的不同类型文件有各自不同的图标。


### 其它说明
通过修改注册表项 `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\ Explorer\FileExts\.txt\UserChoice` 的项 `ProgId` 的值为想要关联程序的方式不好操作。

首先这个值的设定不是设定为完整文件名就可以的，比如notepad设的是 `txtfile`，我估计这是个引用值，实际值指的是`\HKEY_CLASSES_ROOT\txtfile`？纯猜测。

其次，单改了项 `ProgId` 的值还不行，它还有个校验值保存在同路径下的项 `Hash` 中，而这个Hash的值据说可以通过软件 [SetUserFTA.zip](https://kolbi.cz/SetUserFTA.zip)取得，我试了下发现并不好使。比如作者给出的将PDF的默认程序设为 Acrobat Reader 的命令 `SetUserFTA.exe .pdf AcroExch.Document.DC` 中，使用 `AcroExch.Document.DC` 指代 Acrobat Reader，这个映射关系我没找到，好比我拿到国民党通讯兵的电台却没有密码本，也是没法使用的。

## 参考文献
[1]erikaIT.windows注册表文件关联机制[EB/OL].[https://blog.csdn.net/erikaIT/article/details/71637167](https://blog.csdn.net/erikaIT/article/details/71637167),2017-05-11.
[2]woshub.com.Changing Default File Associations in Windows 10 via GPO[EB/OL].[http://woshub.com/managing-default-file-associations-in-windows-10/](http://woshub.com/managing-default-file-associations-in-windows-10/),2020-01-21.
[3]Christoph Kolbicz.SetUserFTA: UserChoice Hash defeated – Set File Type Associations per User or Group on Windows 8/10 and 2012/2016/2019[EB/OL].[https://kolbi.cz/blog/2017/10/25/setuserfta-userchoice-hash-defeated-set-file-type-associations-per-user/](https://kolbi.cz/blog/2017/10/25/setuserfta-userchoice-hash-defeated-set-file-type-associations-per-user/),2017-10-25.
[4]Rimo.Sublime Text 3修改配色方案和关联文件类型的图标[EB/OL].[https://segmentfault.com/q/1010000000589849](https://segmentfault.com/q/1010000000589849),2017-12-23.
