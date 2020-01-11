---
title: 使用 Windows PowerShell 脚本创建工作流 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5720200ce32f114cd4965d961b9e2804bd154b2e
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870840"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>使用 Windows PowerShell 脚本创建工作流

可以通过编写 Windows PowerShell 脚本来创建工作流。 若要创建工作流，请在脚本正文前使用工作流关键字，后跟工作流的名称。 例如：

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

查找工作流的方式与处理任何其他 Windows PowerShell 命令的方式相同。

## <a name="implementing-parallel-and-sequence"></a>实现并行和序列

[Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms735967(v=vs.90))支持并行执行活动。 若要在 Windows PowerShell 脚本中实现此功能，请在脚本块前面使用 `parallel` 关键字。 你还可以使用 `foreach -parallel` 构造以并行方式循环访问对象的集合。 若要按顺序在并行块中按顺序执行一组活动，请将该活动组括在脚本块中，并在块前面加上 sequence 关键字。

## <a name="joining-computers-to-a-domain"></a>将计算机加入域

下面的脚本创建一个工作流，该工作流检查一组用户指定的计算机的域状态，将它们加入域（如果尚未加入域），然后再次检查状态。
这是在[使用 Windows PowerShell 活动创建工作流](./creating-a-workflow-with-windows-powershell-activities.md)中说明的 XAML 工作流的脚本版本。

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
}
```