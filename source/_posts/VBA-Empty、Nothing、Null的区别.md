---
title: VBA中Empty、Null、Nothing的区别
toc: true
comments: true
date: 2023-02-08 16:19:59
updated: 2023-02-08 16:19:59
categories:
  - 编程
tags:
  - VBA
  - 语法
description: 对 VBA 中常见的几种“空”类型理解的归纳整理。
---

## 适用对象

`Empty`、`Null`、`Nothing`是3种特殊值。
它们不可赋值给强类型对象，如：`Integer`，`Long`，`Single`，`Double`，`String`或`Date`等。
它们可以赋值给弱类型对象——变体型`Variant`。它们只对`Variant`变量有意义。

补充：
变体型`Variant`是一种能包含所有类型的变量，它是一种特殊的数据类型，可以赋值数值、字符串或日期数据，还赋值用户定义类型、对象（Object）和特殊类型`Empty`、`Null`和`Nothing`。对所有变量，如果没有明确声明它们是其它数据类型，则它们都变成`Variant`数据类型。

## Empty

示例
```vba
Dim MyVnt As Variant
```
MyVnt只声明未赋值，那么其值就是Empty（由系统自动赋予），表示MyVnt声明后尚未初始化（即尚未赋值）。因为`Variant`可以赋任意类型的值，但由于在初始化前无法确定实际的类型，因而不能给出具体的数据类型。

对于赋值为`Empty`的`Variant`变量，`Empty`是个有效数据（可以称为**万能值**），因为如果你认为这是数值型则值是0，认为是字符串型则值是""（空串）。所以下列的比较判断均为真：
```vba
If MyVnt = 0 Then
  Pass
End If

If MyVnt = "" Then
  Pass
End If

If IsEmpty(MyVnt) Then
  Pass
End If
```

## Null

示例
```vba
MyVnt = null
```
如果将`Null`赋予MyVnt，则表示MyVnt是**无效数据**。对于值为`Null`的变量可以通过`IsNull(变量名)`函数来判断。比如填写性别就是个应用场景，对于性别，有效数据只能是男或女，但没填时就是无效数据，就应该使用`Null`来赋值。

## Nothing

声明为`Variant`的诸多变量中有一种叫对象变量。`Nothing`就是为对象变量赋值的，示例：
```vba
Dim MyVnt As Variant
Set MyVnt = Nothing
```
对象变量使用时会指向/引用一个对象，对象需要占用较大的内存资源，用完应尽快释放。将对象变量设为`Nothing`就是通知系统对象变量不再指向/引用该对象，当该对象没有被任何对象变量引用时，系统便会释放该对象所占的内存资源。

## 总结

`Empty`、`Null`和`Nothing`都可赋值给`Variant`变量，声明时系统会设`Variant`变量为`Empty`；如果要将`Variant`变量设为无效数据可用`Null`；如果不再使用对象变量就应尽快将之设成`Nothing`以便系统尽快释放内存资源。

## 参考文献
[1]烛光.辨析VBA中的Empty，Null和Nothing[EB/OL].[http://www.360doc.com/content/22/0329/17/37559519_1023901524.shtml](http://www.360doc.com/content/22/0329/17/37559519_1023901524.shtml),2022-03-29.
