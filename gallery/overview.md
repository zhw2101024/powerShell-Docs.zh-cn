---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery,psget
title: PowerShell 库
ms.openlocfilehash: d3e3b9d8bb3d6cefd3a3bfe79b012bb1dc1d8a2d
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225612"
---
# <a name="the-powershell-gallery"></a>PowerShell 库

PowerShell 库是 PowerShell 内容的中心存储库。 在 PowerShell 库中，可找到包含 PowerShell 命令和 Desired State Configuration (DSC) 资源的实用 PowerShell 模块。
还可找到 PowerShell 脚本，其中一些脚本可能包含 PowerShell 工作流、概述任务组和提供这些任务的序列。 其中一些包由 Microsoft 编写，另一些包由 PowerShell 社区编写。

## <a name="powershellget-overview"></a>PowerShellGet 概述

PowerShellGet 模块包含用于发现、安装、更新和发布包含来自 [PowerShell 库](https://www.PowerShellGallery.com)和其他专用存储库的模块、DSC 资源、角色功能和脚本等项目的 PowerShell 包的 cmdlet。

## <a name="getting-started-with-the-gallery"></a>库入门

从库安装包需要 PowerShellGet 模块的最新版本。
请参阅[安装 PowerShellGet](installing-psget.md)，获取完整说明。

有关如何在库中使用 PowerShellGet 命令的详细信息，请参阅[入门](getting-started.md)页面。 你也可运行 *Update-Help -Module PowerShellGet* 安装这些命令的本地帮助。

## <a name="supported-operating-systems"></a>受支持的操作系统

PowerShellGet 模块需要 Windows PowerShell 3.0 或更高版本或 PowerShell Core 6.0 或更高版本。

针对以下操作系统提供对应的 Windows PowerShell 版本：

- Windows 10
- Windows 8.1 专业版
- Windows 8.1 企业版
- Windows 7 SP1
- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

PowerShellGet 需要 .NET Framework 4.5 或更高版本。 你可从[此处](https://msdn.microsoft.com/library/5a4x27ek.aspx)安装 .NET Framework 4.5 或更高版本。

由于 PowerShell Core 是跨平台的，这意味着它可以在 Windows、Linux 和 MacOS 上工作，这也使得 PowerShellGet 在这些系统上均可用。 有关 PowerShell Core 支持的完整系统列表，请参阅[安装 PowerShell](/powershell/scripting/setup/installing-powershell)。

许多托管在库中的模块都支持不同的操作系统并具有附加要求。 有关详细信息，请参阅模块文档。

## <a name="got-a-question-have-feedback"></a>遇到问题？ 有反馈？

可在[入门](getting-started.md)页面找到有关 PowerShell 库和 PowerShellGet 的详细信息。 请使用 [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell) 提供反馈和报告问题。
