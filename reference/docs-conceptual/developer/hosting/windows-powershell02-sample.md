---
title: Windows PowerShell02 示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: db7ff3a2dbd92f562379d206db494ab92ef08736
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367296"
---
# <a name="windows-powershell02-sample"></a>Windows PowerShell02 示例

此示例演示如何使用运行空间池的运行空间以异步方式运行命令。 此示例生成命令列表，然后运行这些命令，而 Windows PowerShell 引擎在需要时从池中打开运行空间。

## <a name="requirements"></a>要求

- 此示例需要 Windows PowerShell 2.0。

## <a name="demonstrates"></a>示例

此示例演示了以下内容：

- 创建一个 RunspacePool 对象，该对象具有允许同时打开的最小和最大运行空间。

- 创建命令列表。

- 以异步方式运行命令。

- 调用[Runspacepool. Getavailablerunspaces *](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces)方法以查看有多少个空闲空间。

- 正在捕获带有[Endinvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法的命令输出。

## <a name="example"></a>示例

此示例演示如何打开运行空间池的运行空间，以及如何在这些运行空间中以异步方式运行命令。

[!code-csharp[PowerShell02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 主机应用程序](./writing-a-windows-powershell-host-application.md)
