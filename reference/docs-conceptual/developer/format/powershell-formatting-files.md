---
title: Windows PowerShell 格式设置文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d4c8f84-ebd2-4405-bb10-cfc5400d4ad6
caps.latest.revision: 6
ms.openlocfilehash: 3ec127d5ff60754de5d7f1ac73f2965524228b9c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365006"
---
# <a name="windows-powershell-formatting-files"></a>Windows PowerShell 格式设置文件

Windows PowerShell 提供了几个位于安装目录（`$pshome`）中的格式化文件（. types.ps1xml）。 其中每个文件定义一组特定 .NET 对象的默认显示。 永远不应更改这些文件。 但是，可以将它们用作创建自己的自定义格式设置文件的参考。

`Certificate.Format.ps1xml` 定义证书存储中对象的显示，例如 x.509 证书和证书存储。

`DotNetTypes.Format.ps1xml` 定义杂项 .NET 对象的显示，例如 CultureInfo、FileVersionInfo 和 EventLogEntry 对象。

`FileSystem.Format.ps1xml` 定义文件系统对象（如文件和目录对象）的显示。

`Help.Format.ps1xml` 定义[get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet 使用的不同视图，例如详细、完整、参数和示例视图。

`PowerShellCore.Format.ps1xml` 定义 Windows PowerShell 核心 cmdlet 生成的对象的显示方式，如[获取成员](/powershell/module/Microsoft.PowerShell.Utility/Get-Member)和[获取历史](/powershell/module/Microsoft.PowerShell.Core/Get-History)cmdlet 返回的对象。

`PowerShellTrace.Format.ps1xml` 定义跟踪对象的显示，如[trace-Command](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) cmdlet 生成的跟踪对象。

`Registry.Format.ps1xml` 定义注册表对象的显示，如 key 和 entry 对象。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)
