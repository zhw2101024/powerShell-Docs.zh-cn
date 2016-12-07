---
title: "WMF 5.1 发行说明（预览版）"
ms.date: 2016-07-27
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: jkeithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: 60350cdc816e3a480a033adb3721ad4dabddfff9
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="windows-management-framework-wmf-51-preview-release-notes"></a>Windows Management Framework (WMF) 5.1 预览版发行说明 #

WMF 5.1 预览版包括将与 Windows Server 2016 一起发行的 PowerShell、WMI、WinRM 以及软件清单和许可 (SIL) 组件。 WMF 5.1 可安装在 Windows 7、Windows 8.1、Windows Server 2008 R2、2012 和 2012 R2 上，并提供了对 WMF 5.0 RTM 的大量改进，其中包括：

- 新 cmdlet：本地用户和组；Get-ComputerInfo
- PowerShellGet 改进包括强制签名模块和安装 JEA 模块
- PackageManagement 增加了对容器、CBS 安装程序、基于 EXE 的安装程序、CAB 包的支持
- DSC 和 PowerShell 类的调试改进
- 安全增强包括强制执行来自请求服务器和使用 PowerShellGet cmdlet 时的目录签名模块
- 响应大量的用户请求和问题

**重要说明：**

- **WMF 5.1 预览版需要 .NET Framework 4.6**。 安装将成功，但如果未安装 .NET 4.6，主要功能将失败。 相关说明请参见[安装和配置 WMF 5.1（预览版）](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure)主题。 
- **生产部署目前不支持 WMF 5.1 预览版**。 其目的是提供有关发行内容的提前告知信息，让你有机会向 PowerShell 团队提供反馈。
- 可在 WMF 5.0 上直接安装 WMF 5.1 预览版。
- 存在一个已知问题 - 现在 Windows 7 和 Windows Server 2008 R2 上安装 WMF 5.1 预览版必须具有 WMF 4.0。 此要求有望在最终发行前消除。
- 如果安装 WMF 5.1 的未来版本（包括 RTM 版本），将需要卸载 WMF 5.1 预览版。

