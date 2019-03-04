---
title: 调用 Cmdlet 和 Cmdlet 中的脚本 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: e5dc525a6c80ce135d6d68e12968613056d447e8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855183"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a>调用 Cmdlet 中的 Cmdlet 和脚本

Cmdlet 可以调用其他 cmdlet 和脚本中的输入处理方法的 cmdlet。 这可以将现有的 cmdlet 和脚本的功能添加到 cmdlet，而无需重写代码。

## <a name="the-invoke-method"></a>调用方法

所有 cmdlet 可以通过调用都调用现有 cmdlet [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)方法的输入处理方法，如[System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)，即该 cmdlet 通过重写。 但是，可以调用仅直接派生这些 cmdlet [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)类。 不能调用派生的 cmdlet [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)类。

[System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)方法具有以下变体。

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)此变体调用 cmdlet 对象并返回"T"类型对象的集合。

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)此变体调用 cmdlet 对象并返回强类型化的 emumerator。 此变体允许用户使用集合中的对象来执行自定义操作。

## <a name="examples"></a>示例

|示例|描述|
|-------------|-----------------|
|[调用某个 Cmdlet 中的 Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|此示例演示如何调用在另一个 cmdlet 中的 cmdlet。|
|[调用某个 Cmdlet 中的脚本](./how-to-invoke-scripts-within-a-cmdlet.md)|此示例演示如何调用脚本提供给在另一个 cmdlet 从 cmdlet。|

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
