---
title: "了解 Windows PowerShell 管道"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 233ec6fafbf1e770190601750be3bdcef2337b7f

---

# 了解 Windows PowerShell 管道
在 Windows PowerShell 中，管道的作用几乎随处可见。 尽管你会在屏幕上看到文本，但 Windows PowerShell 不通过管道在命令之间传递文本。 而是通过管道传递对象。

管道使用的表示法与其他 Shell 中使用的类似，因此乍看之下，似乎 Windows PowerShell 并未引入什么新的内容。 例如，如果你使用 **Out\-Host** cmdlet 来强制逐页显示来自于另一个命令的输出，则这一输出看起来就像分页显示在屏幕上的普通文本：

```
PS> Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\system32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2005-10-22  11:04 PM        315 $winnt$.inf
-a---        2004-08-04   8:00 AM      68608 access.cpl
-a---        2004-08-04   8:00 AM      64512 acctres.dll
-a---        2004-08-04   8:00 AM     183808 accwiz.exe
-a---        2004-08-04   8:00 AM      61952 acelpdec.ax
-a---        2004-08-04   8:00 AM     129536 acledit.dll
-a---        2004-08-04   8:00 AM     114688 aclui.dll
-a---        2004-08-04   8:00 AM     194048 activeds.dll
-a---        2004-08-04   8:00 AM     111104 activeds.tlb
-a---        2004-08-04   8:00 AM       4096 actmovie.exe
-a---        2004-08-04   8:00 AM     101888 actxprxy.dll
-a---        2003-02-21   6:50 PM     143150 admgmt.msc
-a---        2006-01-25   3:35 PM      53760 admparse.dll
<SPACE> next page; <CR> next line; Q quit
...
```

如果你想要缓慢显示冗长输出，Out\-Host\-Paging 命令会是一个有用的管道元素。 尤其是在操作会大量占用 CPU 的情况下，会十分有用。 因为当有可以立即显示的完整页面时，处理进程会转移到 Out\-Host cmdlet，而管道中在其之前的 cmdlet 会停止操作，直到输出了下一页为止。 如果使用 Windows 任务管理器监视 Windows PowerShell 的 CPU 和内存使用情况，便会见到这种情况。

运行命令：**Get\-ChildItem C:\\Windows\-Recurse**。 将 CPU 和内存的使用情况与此命令相比较：**Get\-ChildItem C:\\Windows\-Recurse | Out\-Host\-Paging**。 你在屏幕上会看到文本，但那是因为在控制台窗口中以文本形式表示对象是必需的。 这只是 Windows PowerShell 中实际运行内容的表示形式。 例如，考虑 Get\-Location cmdlet。 如果你键入 **Get\-Location**，而你当前的位置是 C 驱动器的根路径时，你将看到以下输出：

```
PS> Get-Location

Path
----
C:\
```

如果 Windows PowerShell 通过管道传递文本，并发出诸如 **Get\-Location | Out\-Host** 的命令，则会将一组字符按其在屏幕上的显示顺序从 **Get\-Location** 传递到 **Out\-Host**。 换言之，如你打算忽略标题信息，**Out\-Host** 会首先收到字符“**C”**，接着是字符“**:”**，然后是字符“**\\”**。 **Out\-Host** cmdlet 无法确定要与 **Get\-Location** cmdlet 输出的字符关联的含义。

Windows PowerShell 在管道通信中不使用文本运行命令，而是使用对象。 从用户角度来看，对象将相关信息打包成一种可使信息作为单元进行操作变得更容易以及提取所需的特定项变得更容易的形式。

**Get\-Location** 命令不返回包含当前路径的文本。 它返回称为 **PathInfo** 对象的一个信息包，其中包含了当前路径以及一些其他信息。 然后 **Out\-Host** cmdlet 将此 **PathInfo** 对象发送到屏幕，Windows PowerShell 会根据其格式设置规则决定要显示的信息以及显示的方式。

实际上，只会在此进程结束时添加 **Get\-Location** cmdlet 输出的标题信息，作为屏幕上所显示数据的格式设置过程的一部分。 你在屏幕上看到的只是信息摘要，而非输出对象的完整表示形式。

假设从 Windows PowerShell 命令输出的信息比我们在控制台窗口中看到的多，该如何检索不可见的元素呢？ 如何查看额外的数据？ 并且如果你想以不同于 Windows PowerShell 通常使用的格式来查看数据，应该怎么做？

本章的其余部分将讨论如何发现特定 Windows PowerShell 对象的结构，同时选择特定项并将其设置为更易显示的格式，以及如何将此信息发送至备用输出位置，比如文件和打印机。




<!--HONumber=Jun16_HO4-->


