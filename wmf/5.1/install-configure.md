---
title: "安装并配置 WMF 5.1（预览版）"
ms.date: 2016-05-16
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
contributor: kriscv
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 0a53817d6af625822d9183d2a0d5bc7bf4d2b264
ms.openlocfilehash: 058d18deeb3d4926970ea25a157f92ad14836e4b

---

# 安装并配置 WMF 5.1（预览版） #

## 安装 .Net 4.6
必须安装 .Net Framework 4.6，才可使用 WMF 5.1。 必须启动新的目录签名功能，这将影响 WMF 5.1 中模块和脚本加载的若干方面。 

[.Net Framework 4.6 作为 KB 3045560](https://support.microsoft.com/en-us/kb/3045560) 提供。 下载位置提供了安装说明。

> **注意：**存在一个已知问题 - WMF 5.1 预览版安装程序未检测到 .NET 4.6 要求，因此你将可在安装 .Net 4.6 前安装 WMF 5.1 预览版。 我们的测试表明，你可在安装 WMF 5.1 预览版后安装 .Net 4.6。 WMF 5.1 的最终版本将在安装前正确检查此先决条件要求。 

## 下载和安装 WMF 5.1 预览版

下载适用于要在其中进行安装的操作系统和体系结构的 WMF 5.1 包：

| 操作系统       | 必备条件 | 包链接             |
|------------------------|---------------|---------------------------|
| Windows Server 2012 R2 | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) | [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823586)|
| Windows Server 2012    | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) | [W2K12-KB3156423-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823587)|
| Windows Server 2008 R2 | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) </br> [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) </br> [SHA-2 代码签名](https://technet.microsoft.com/en-us/library/security/3033929)的安全更新 | [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823588) |
| Windows 8.1            | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) | **x64：**[Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823586) </br> **x86：**[Win8.1-KB3156422-x86.msu](http://go.microsoft.com/fwlink/?LinkID=823589) |
| Windows 7 SP1          | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) </br> [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) </br> [SHA-2 代码签名](https://technet.microsoft.com/en-us/library/security/3033929)的安全更新 | **x64：**[Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823588) </br> **x86：**[Win7-KB3156424-x86.msu](http://go.microsoft.com/fwlink/?LinkID=823590) |


## 从 Windows 资源管理器（或是 Windows Server 2012 R2 或 Windows 8.1 中的文件资源管理器）安装 WMF 5.1

1. 导航到在其中下载了 MSU 文件的文件夹。

2. 双击 MSU 以运行它。

## 从命令提示符安装 WMF 5.1##

1. 下载适用于计算机体系结构的正确程序包后，使用提升的用户权限（以管理员身份运行）打开“命令提示符”窗口。 在 Windows Server 2012 R2、Windows Server 2012 或 Windows Server 2008 R2 SP1 的服务器核心安装选项上，命令提示符默认使用提升的用户权限打开。

2. 将目录更改为向其中下载或复制 WMF 5.1 安装包的文件夹。

3. 运行下列命令之一：
    - 在运行 Windows Server 2012 R2 或 Windows 8.1 x64 的计算机上，运行 `Win8.1AndW2K12R2-KB3156422-x64.msu /quiet`。
    - 在运行 Windows Server 2012 的计算机上，运行 `W2K12-KB3156423-x64.msu /quiet`。
    - 在运行 Windows Server 2008 R2 SP1 或 Windows 7 SP1 x64 的计算机上，运行 `Win7AndW2K8R2-KB3156424-x64.msu /quiet`。
    - 在运行 Windows 8.1 x86 的计算机上，运行 `Win8.1-KB3156422-x86.msu /quiet`。
    - 在运行 Windows 7 SP1 x86 的计算机上，运行 `Win7-KB3156424-x86.msu /quiet`。

## Windows Server 2008 SP1 和 Windows 7 SP1 的其他安装说明##
在 Windows Server 2008 SP1 或 Windows 7 SP1 上安装 WMF 5.1 需要安装以下各项：
- 最新 Service Pack。
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855)
- WMF 5.1 需要 [Microsoft .NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560)。 可按照下载位置的说明安装 Microsoft .NET Framework 4.6。
- [SHA-2 代码签名](https://technet.microsoft.com/en-us/library/security/3033929)的安全更新。 Windows 目录文件需要使用新的 PowerShell cmdlet。 

> **WinRM 依赖关系** - Windows PowerShell Desired State Configuration (DSC) 依赖 WinRM。 在 Windows Server 2008 R2 和 Windows 7 上默认不启用 WinRM。 若要启用 WinRM，请在 Windows PowerShell 提升的会话中运行 `Set-WSManQuickConfig`。




<!--HONumber=Jul16_HO5-->


