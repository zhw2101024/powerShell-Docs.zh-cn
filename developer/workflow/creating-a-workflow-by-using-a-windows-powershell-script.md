---
title: 使用 Windows PowerShell 脚本创建一个工作流 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853043"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>使用 Windows PowerShell 脚本创建工作流

可以通过编写一个 Windows PowerShell 脚本来创建工作流。 若要创建工作流，使用工作流关键字后跟工作流之前对该脚本的主体的名称。 例如：

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

在将任何其他 Windows PowerShell 命令的相同方式中找到工作流。

## <a name="implementing-parallel-and-sequence"></a>实现并行和序列

[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx)支持并行活动的执行。 若要在 Windows PowerShell 脚本中实现此功能，使用`parallel`关键字的脚本块的前面。 此外可以使用`foreach -parallel`构造循环访问一系列并行中的对象。 若要并行块内按顺序执行的一组活动，将在脚本块中，该组的活动，并且位于序列关键字的块。

## <a name="joining-computers-to-a-domain"></a>将计算机加入到域

以下脚本创建的工作流检查一组用户指定计算机的域状态，将它们加入到域中，如果它们已未联接，然后再次检查状态。 这是 XAML 工作流中所述的脚本版本[使用 Windows PowerShell 活动创建工作流](./creating-a-workflow-with-windows-powershell-activities.md)。

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