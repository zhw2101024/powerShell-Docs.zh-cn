---
title: GetProc Tutorial | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068090"
---
# <a name="getproc-tutorial"></a>GetProc 教程

本部分提供的教程，创建一个 Get-proc cmdlet 是非常类似于[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process)提供的 Windows PowerShell cmdlet。 本教程提供的演示了如何实现 cmdlet 的代码片段和代码的说明。

## <a name="topics-in-this-tutorial"></a>在本教程中的主题

在本教程中的主题旨在使用在上一主题中讨论的内容构建每个主题按顺序读取。

[创建不带参数的 Cmdlet](./creating-a-cmdlet-without-parameters.md)本部分介绍如何创建从本地计算机而不使用参数，检索的信息，然后将信息写入管道的 cmdlet。

[将该进程命令行输入参数添加](./adding-parameters-that-process-command-line-input.md)本部分介绍如何将参数添加到 Get-proc cmdlet，以便该 cmdlet 可以处理基于显式对象传递给 cmdlet 的输入。 中介绍的实现此处检索的过程基于其名称，，然后将信息写入管道。

[添加参数该进程管道输入](./adding-parameters-that-process-pipeline-input.md)本部分介绍如何将参数添加到 Get-proc cmdlet，以便该 cmdlet 可以处理通过管道传递给它的对象。 所述实现 cmdlet 此处检索进程基于对象传递给 cmdlet，然后将信息写入到管道。

[将非终止错误报告添加到你的 Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)本部分介绍如何添加非终止错误报告给 cmdlet。 此处所述的实现会检测发生时处理输入，并将错误记录写入错误流的非终止错误。

## <a name="see-also"></a>另请参阅

[创建不带参数的 Cmdlet](./creating-a-cmdlet-without-parameters.md)

[添加处理命令行输入的参数](./adding-parameters-that-process-command-line-input.md)

[添加进程管道输入的参数](./adding-parameters-that-process-pipeline-input.md)

[添加非终止错误报告到 Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
