---
title: Cmdlet 代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 936728d64f30a08fb9e2fa9ccef103683594aa3e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364496"
---
# <a name="examples-of-cmdlet-code"></a>Cmdlet 代码示例

本部分包含可用于开始编写自己的 cmdlet 的 cmdlet 代码示例。

> [!IMPORTANT]
> 如需编写 cmdlet 的分步说明，请参阅[编写 Cmdlet 教程](./tutorials-for-writing-cmdlets.md)。

## <a name="in-this-section"></a>本部分内容

[如何编写简单的 Cmdlet](./how-to-write-a-simple-cmdlet.md)此示例显示了 cmdlet 代码的基本结构。

[如何声明 Cmdlet 参数](./how-to-declare-cmdlet-parameters.md)此示例演示如何声明不同类型的参数。

[如何声明参数集](./how-to-declare-parameter-sets.md)此示例演示如何声明一组参数，这些参数可以更改 cmdlet 执行的操作。

[如何验证参数输入](./how-to-validate-parameter-input.md)这些示例演示如何验证参数输入。

[如何声明动态参数](./how-to-declare-dynamic-parameters.md)此示例演示如何声明在运行时添加的参数。

[如何在 Cmdlet 中调用脚本](./how-to-invoke-scripts-within-a-cmdlet.md)此示例演示如何调用提供给 cmdlet 的脚本。

[如何替代输入处理方法](./how-to-override-input-processing-methods.md)这些示例演示用于重写 BeginProcessing、ProcessRecord 和 EndProcessing 方法的基本结构。

[如何支持 ShouldProcess 调用](./how-to-request-confirmations.md)此示例显示了应如何从 Cmdlet 内调用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法的方法的操作方式，如。

[如何支持事务](./how-to-support-transactions.md)此示例显示了如何指示该 cmdlet 支持事务，以及如何实现在事务中使用 cmdlet 时采取的操作。

[如何支持作业](./how-to-support-jobs.md)此示例演示如何在编写 cmdlet 时支持作业。

[如何从 Cmdlet 内调用 cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)此示例演示如何从另一个 cmdlet 中调用 cmdlet，这允许你将调用的 cmdlet 的功能添加到正在开发的 cmdlet。

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
