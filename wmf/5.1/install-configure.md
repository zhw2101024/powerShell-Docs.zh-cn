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
ms.sourcegitcommit: 26da6c80568327faadc6746099ac9869f2018fcf
ms.openlocfilehash: 8a10903c421f62311a28c9f32e352bba75f21052

---

# 安装并配置 WMF 5.1（预览版） #

***请注意：*** 
*该内容为占位符。下面的链接指向 WMF 5.0 版本，并且将在版本发布后更新。*

下载适用于要在其中进行安装的操作系统和体系结构的 WMF 5.1 包：

| 操作系统       | 体系结构 | 包名称              |
|------------------------|--------------|---------------------------|
| Windows Server 2012 R2 | x64      | [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows Server 2012    | x64      | [W2K12-KB3156423-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) |
| Windows Server 2008 R2 | x64      | [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 8.1            | x64          | [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows 8.1            | x86          | [Win8.1-KB3156422-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963) |
| Windows 7 SP1          | x64          | [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 7 SP1          | x86          | [Win7-KB3156424-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962) |


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

> **WinRM 依赖关系** - Windows PowerShell Desired State Configuration (DSC) 依赖 WinRM。 在 Windows Server 2008 R2 和 Windows 7 上默认不启用 WinRM。 若要启用 WinRM，请在 Windows PowerShell 提升的会话中运行 `Set-WSManQuickConfig`。




<!--HONumber=Jul16_HO2-->


