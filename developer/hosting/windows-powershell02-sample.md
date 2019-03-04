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
ms.openlocfilehash: 89ad17257ebac56105a93672317a149515e80d32
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861063"
---
# <a name="windows-powershell02-sample"></a>Windows PowerShell02 示例

此示例演示如何使用运行空间的运行空间池以异步方式运行命令。 此示例将生成一系列命令，然后运行这些命令，而 Windows PowerShell 引擎将在需要时从池中打开运行空间。

## <a name="requirements"></a>要求

- 此示例要求 Windows PowerShell 2.0。

## <a name="demonstrates"></a>说明

此示例将演示如下：

- 创建具有最小和最大的可在同一时间打开运行空间数 RunspacePool 对象。

- 创建命令的列表。

- 以异步方式运行命令。

- 调用[System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces)方法，以便查看多少运行空间是免费的。

- 捕获命令输出中的与[System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke)方法。

## <a name="example"></a>示例

此示例演示如何打开运行空间的运行空间池，以及如何以异步方式在这些运行空间中运行命令。

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell 主机应用程序](./writing-a-windows-powershell-host-application.md)