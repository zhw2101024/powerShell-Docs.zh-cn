---
title: "从管道中删除对象 (Where Object)"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 0c5e2b60d96a6c64aedfa9522cbdc0ce5d4aa6b0

---

# 从管道中删除对象 (Where-Object)
在 Windows PowerShell 中，你通常会生成和传递比预期更多的对象到管道中。 可以通过使用 **Format** cmdlet 指定特定对象的属性进行显示，但是这对从显示中删除整个对象的问题没有任何帮助。 你可能希望在管道结束之前筛选对象，以便你可以只对初始生成对象的子集执行操作。

Windows PowerShell 包括 **Where\-Object** cmdlet，它可让你在管道中测试每个对象，并且仅沿管道传递满足特定测试条件的对象。 将从管道中删除未通过测试的对象。 提供测试条件作为 **Where\-ObjectFilterScript** 参数的值。

### 使用 Where\-Object 执行简单测试
**FilterScript** 的值是一个*脚本块* \- 由大括号 {} \- 括起来的一个或多个 Windows PowerShell 命令，其计算结果为 True 或 False。 这些脚本块可能非常简单，但是创建它们需要了解有关 Windows PowerShell 的另一个概念，即比较运算符。 比较运算符比较其每一侧显示的项。 比较运算符以“\-”字符开头，后跟名称。 基本比较运算符适用于几乎任何类型的对象。 更高级的比较运算符可能仅适用于文本或数组。

> [!NOTE]
> 默认情况下，在处理文本时，Windows PowerShell 比较运算符不区分大小写。

出于分析考虑，<、> 和 \= 等符号不用作比较运算符。 相反，比较运算符由字母组成。 下表中列出了基本比较运算符。

|比较运算符|含义|示例（返回 True）|
|-----------------------|-----------|--------------------------|
|\-eq|等于|1 \-eq 1|
|\-ne|不等于|1 \-ne 2|
|\-lt|小于|1 \-lt 2|
|\-le|小于或等于|1 \-le 2|
|\-gt|大于|2 \-gt 1|
|\-ge|大于或等于|2 \-ge 1|
|\-like|相似（文本的通配符比较）|"file.doc" \-like "f\*.do?"|
|\-notlike|不相似（文本的通配符比较）|"file.doc" \-notlike "p\*.doc"|
|\-contains|包含|1,2,3 \-contains 1|
|\-notcontains|不包含|1,2,3 \-notcontains 4|

Where\-Object 脚本块使用特殊变量“$\_”来指代管道中的当前对象。 以下是其工作原理示例。 如果你有一个数字列表，且希望仅返回小于 3 的数字，则可使用 Where\-Object 通过键入以下内容来筛选数字：

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

### 基于对象属性进行筛选
既然 $\_ 指代当前管道对象，我们就可以访问其属性以进行测试。

例如，我们可以看看 WMI 中的 Win32\_SystemDriver 类。 一个特定的系统上可能有数百个系统驱动程序，但是你可能只对特定一些系统驱动程序感兴趣，例如那些当前正在运行的程序。 如果你使用 Get\-Member 查看 Win32\_SystemDriver 成员（**Get\-WmiObject \-Class Win32\_SystemDriver | Get\-Member \-MemberType 属性**），你将发现相关属性为 State，并且在驱动程序运行时，它的值为“Running”。 你可以筛选系统驱动程序，通过键入以下内容仅选择正在运行的驱动程序：

```
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"}
```

这仍会生成一个较长的列表。 你可能还希望进行筛选，以通过测试 StartMode 值仅选择自动启动的驱动程序集：

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Auto"}

DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
```

这为我们提供了大量不再需要的信息，因为我们知道驱动程序正在运行。 事实上，此时我们可能需要的唯一信息就是名称和显示名。 下面的命令仅包括这两种属性，从而使输出更简单：

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Manual"} | Format-Table -Property Name,DisplayName

Name                                    DisplayName
----                                    -----------
AsyncMac                                RAS Asynchronous Media Driver
Fdc                                     Floppy Disk Controller Driver
Flpydisk                                Floppy Disk Driver
Gpc                                     Generic Packet Classifier
IpNat                                   IP Network Address Translator
mouhid                                  Mouse HID Driver
MRxDAV                                  WebDav Client Redirector
mssmbios                                Microsoft System Management BIOS Driver
```

上面的命令包含两个 Where\-Object 元素，但是可以使用 \-and 逻辑运算符将其表示为一个 Where\-Object 元素，如下所示：

```
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq "Running") -and ($_.StartMode -eq "Manual") } | Format-Table -Property Name,DisplayName
```

下表中列出了标准逻辑运算符。

|逻辑运算符|含义|示例（返回 True）|
|--------------------|-----------|--------------------------|
|\-和|Logical and；如果两侧都为 True，则返回 True|(1 \-eq 1) \-and (2 \-eq 2)|
|\-或|Logical or；如果某一侧为 True，则返回 True|(1 \-eq 1) \-or (1 \-eq 2)|
|\-非|Logical not；反转 True 和 False|\-not (1 \-eq 2)|
|\!|Logical not；反转 True 和 False|\!(1 \-eq 2)|




<!--HONumber=Jun16_HO4-->


