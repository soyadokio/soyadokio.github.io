---
title: VBA-数据类型
toc: true
comments: true
date: 2023-02-08 14:34:53
updated: 2023-02-08 14:34:53
categories:
  - 编程
tags:
  - VBA
  - 语法
description: 对 VBA 语言数据类型的归纳整理。
---

## 基本数据类型

1. 字符串（String）
必须用半角双引号。

1. 布尔型（Boolean）
赋值范围：True和False

1. 整数型

  1. 字节型（Byte）
  可理解为Integer的简配版，用来表示0~255之间的整数。声明符号为`$`

  1. 整形（Integer）
  用来表示-32768~32768之间的整数。声明符号为`%`

  1. 长整型（Long）
  用来表示-2147483648~2147483647之间的整数。声明符号为`&`

1. 浮点型
  1. 单精度浮点数（Single）
  一般的小数单精度够用了。声明符号为`!`

  1. 双精度浮点数（Double）
  双精度一般用于科学计算等对小数精确值很敏感的领域。声明符号为`#`

1. 货币型（Currency）
（没有了解）声明符号为`@`

1. 日期型（Date）
含有年月日时分秒。

1. 小数型（Decimal）
（没有了解）小数型数据类型只能在变体型中使用，不能声明一个变量为小数型。

1. 对象型（Object）
利用Set语句声明为对象型的变量可以赋值为任何对象的引用。
示例
```vba
Dim MyObj As Object
Set MyObj = xxx
```

1. 变体型（Variant）
无类型声明字符，变体型除定长字符串数据及用户定义类型外，可以包含任何类型数据，包括Empty、Error、Nothing、Null等特殊值，可以用`VarType(变量名)`函数和`TypeName(变量名)`函数来决定如何处理变体型中的数据。
```vba
Dim MyName
```

**VarType()函数返回常量值**

|常量|值|说明|
|:-|-:|:-|
|vbEmpty            |   0|空（未初始化）|
|vbNull             |   1|Null（不是有效数据）|
|vbInteger          |   2|整数|
|vbLong             |   3|长整数|
|vbSingle           |   4|单精度浮点数|
|vbDouble           |   5|双精度浮点数|
|vbCurrency         |   6|货币值|
|vbDate             |   7|日期值|
|vbString           |   8|字符串|
|vbObject           |   9|Object|
|vbError            |  10|错误值|
|vbBoolean          |  11|布尔值|
|vbVariant          |  12|Variant（仅与变量的数组一起使用）|
|vbDataObject       |  13|数据访问对象|
|vbDecimal          |  14|小数值|
|vbByte             |  17|字节值|
|vbLongLong         |  20|LongLong 整数 (仅在 64 位平台上有效)|
|vbUserDefinedType  |  36|包含用户定义类型的变量|
|vbArray            |8192|此函数返回数组 (始终添加到另一个常量)|

注意：
1. 如果传递对象并具有默认属性， 则 VarType (对象) 返回该对象的默认属性的类型。
1. VarType 函数本身绝不返回 vbArray 的值。 它始终添加到其他某个值，以指示特定类型的数组。 例如，为整数数组返回的值的计算方式为 vbInteger + vbArray ，或 8194。
1. 常量 vbVariant 仅与 vbArray 一起使用以指示 VarType 函数的参数是类型 Variant 的数组。

**TypeName()函数返回字符串**

|返回字符串|变量|
|:-|:-|
|objecttype   |对象类型             |
|Byte         |位值                |
|Integer      |整数                |
|Long         |长整数               |
|Single       |单精度浮点数         |
|Double       |双精度浮点数         |
|Currency     |货币                |
|Decimal      |十进制值             |
|Nothing      |不再引用对象的对象变量|
|Date         |日期                |
|String       |字符串               |
|Error        |错误值               |
|Boolean      |逻辑值               |
|Empty        |未初始化             |
|Null         |无效对象             |
|object       |对象                |
|Unknown      |类型未知的对象       |

## 枚举类型

当一个变量只有几种可能的值时，可以将其定义为枚举类型。枚举类型的定义需要放在模块和窗体的声明部分

语法

```vba
[Public | Private] Enum 类型名称
  成员 [=常量表达式]
  成员 [=常量表达式]
  ......
End Enum
```

示例

```vba
'定义
Public Enum Weekdays
  Monday
  Tuesday
  Wednesday
  Thursday
  Friday
  Saturday
  Sunday
End Enum

'使用
Sub Test()
  Dim day As Weekdays
  day = Monday
End Sub
```

## 用户定义类型

在VBA中还可以使用Type语句来定义自己的数据类型，其格式如下：

语法
```vba
Type 类型名
元素名1  AS  数据类型1
元素名2  AS  数据类型2
...
End Type
```

自定义的数据类型的定义必须放在模块的声明部分中。

## 参考文献
[1]L罗乐.VBA的数据类型[EB/OL].[http://www.360doc.com/content/18/0603/19/30583536_759387607.shtml](http://www.360doc.com/content/18/0603/19/30583536_759387607.shtml),2018-06-03.
[2]凌霄百科.VBA学习-语法基础[EB/OL].[https://www.bilibili.com/read/cv2467437/](https://www.bilibili.com/read/cv2467437/),2019-04-16.
