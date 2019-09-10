---
title: RunSpace03 （C#）代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 9afdb97b8ae2919f091ca5bacccedbe37c2e1584
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848028"
---
# <a name="runspace03-c-code-sample"></a>RunSpace03 (C#) 代码示例

下面是 " C#创建运行指定脚本的控制台应用程序" 中所述的控制台应用程序的源代码。 此示例使用[Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke)类来执行一个脚本，该脚本通过使用传递到脚本的进程名称列表来检索进程信息。 它演示如何将输入对象传递给脚本，以及如何检索错误对象以及输出对象。

> [!NOTE]
> 你可以使用适用C#于 Windows Vista 的 Microsoft Windows 软件开发工具包和 Microsoft .NET Framework 3.0 运行时组件下载此示例的源文件（runspace03.cs）。 有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
> 已下载的源文件中有 **\<PowerShell 示例 >** 目录。

## <a name="code-sample"></a>代码示例

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a>另请参阅

[Windows PowerShell 程序员指南](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)