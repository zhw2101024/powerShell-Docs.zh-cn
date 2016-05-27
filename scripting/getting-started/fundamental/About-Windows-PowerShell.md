---
title:  关于 Windows PowerShell
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  979654ae-7994-47f8-be43-d79e7a140143
---

# 关于 Windows PowerShell
Windows PowerShell 旨在通过消除长期存在的问题和添加新功能改进命令行和脚本环境。

## 可发现性
Windows PowerShell 使它的功能更易发现。 例如，若要查找用于查看和更改 Windows 服务的 cmdlet 列表，请键入：

```
Get-Command *-Service
```

找到完成任务的 cmdlet 后，可通过使用 Get-Help cmdlet 了解有关该 cmdlet 的详细信息。 例如，若要显示有关 Get-Service cmdlet 的帮助，请键入：

```
Get-Help Get-Service
```
大多数 cmdlet 会发出对象，这些对象可获得操作，然后再呈现为显示文本。 若要全面了解该 cmdlet 的输出，请将其输出通过管道传递给 Get-Member cmdlet。 例如，下面的命令显示了有关 Get-Service cmdlet 所输出对象的成员的信息。

```
Get-Service | Get-Member
```

## 一致性
管理系统是一项复杂的任务，具有一致的接口的工具有助于控制固有的复杂性。 遗憾的是，命令行工具和可脚本化 COM 对象的一致性均未知。

Windows PowerShell 的一致性是其主要资产之一。 例如，如果了解如何使用 Sort-Object cmdlet，你可以利用这一知识对任何 cmdlet 的输出进行排序。 不需要了解每个 cmdlet 的不同排序例程。

此外，cmdlet 开发人员无需为其 cmdlet 设计排序功能。 Windows PowerShell 将给它们一个提供基本功能的框架，并强制它们在接口的多个方面保持一致。 该框架消除了通常留给开发人员的某些选择，但它也因而使得开发可靠的和易于使用的 cmdlet 变得简单得多。

## 交互式脚本编写环境
Windows PowerShell 是一个组合的交互式脚本编写环境，它允许你访问命令行工具和 COM 对象，还让你能够使用 .NET Framework 类库 (FCL) 的强大功能。

此环境改进了 Windows 命令提示，它将提供具有多个命令行工具的交互式环境。 它还改进了 Windows 脚本宿主 (WSH) 脚本，让你可以使用多个命令行工具和 COM 自动化对象，但不提供交互式环境。

通过组合使用以上所有功能，Windows PowerShell 将扩展交互用户和脚本编写者的能力，并使系统管理更可控。

## 面向对象
尽管通过在文本框中键入命令可以与 Windows PowerShell 交互，但 Windows PowerShell 仍以对象（而不是文本）为基础。 命令的输出是一个对象。 可以将输出对象发送给另一个命令以作为其输入。 因此，Windows PowerShell 将为曾使用其他 shell 的用户提供熟悉的界面，同时引入新的强大命令行范例。 它让你能够发送对象而不是文本，从而扩展了在命令之间发送数据的概念。

## 轻松转换到脚本
Windows PowerShell 让你能够从以交互方式键入命令转换到创建和运行脚本。 可以在 Windows PowerShell 命令提示符处键入命令，从而发现执行某项任务的命令。 然后，你可以在将这些命令保存到副本或历史记录中，然后将其复制到文件以用作脚本。



<!--HONumber=May16_HO2-->


