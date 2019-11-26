---
title: RunSpace05 代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: 979403376c5e694b686aaf77a2cb787d765cb883
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417928"
---
# <a name="runspace05-code-sample"></a>RunSpace05 代码示例

下面是[使用 RunspaceConfiguration 配置运行空间](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2)中所述的 Runspace05 示例的源代码。 此示例演示如何创建运行空间配置信息、创建运行空间、使用单个命令创建管道，然后执行管道。 执行的命令是 `Get-Process` cmdlet。

> [!NOTE]
> 你可以使用适用C#于 windows Vista 的 Microsoft Windows 软件开发工具包和 Microsoft .NET Framework 3.0 运行时组件下载源文件（runspace05.cs）。 有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
>
> 下载的源文件在 **\<PowerShell 示例 >** 目录中提供。

## <a name="code-sample"></a>代码示例

[!code-csharp[Runspace05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a>请参阅

[Windows PowerShell 程序员指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
