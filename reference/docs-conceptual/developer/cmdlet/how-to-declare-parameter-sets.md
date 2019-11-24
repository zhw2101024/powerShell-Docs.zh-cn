---
title: 如何声明参数集 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365606"
---
# <a name="how-to-declare-parameter-sets"></a>如何声明参数集

此示例演示如何在声明 cmdlet 的参数时定义两个参数集。 每个参数集都具有唯一参数和两个参数集均使用的共享参数。 有关参数集的详细信息，包括如何指定默认参数集，请参阅[Cmdlet 参数集](./cmdlet-parameter-sets.md)。

> [!IMPORTANT]
> 尽可能将参数集的唯一参数定义为必需的参数。 但是，如果想要在不指定任何参数的情况下运行 cmdlet，则 unique 参数可以是可选参数。 例如，`Get-Command` cmdlet 的唯一参数是可选的。

## <a name="how-to-define-two-parameter-sets"></a>如何定义两个参数集

1. 将 `ParameterSet` 关键字添加到第一个参数集的 unique 参数的 Parameter 特性中。

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. 将 `ParameterSet` 关键字添加到第二个参数集的 unique 参数的 Parameter 特性中。

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. 对于属于这两个参数集的参数，请为每个参数集添加一个参数属性，然后将 `ParameterSet` 关键字添加到每个集合。 在每个参数特性中，可以指定如何定义该参数。 参数在一组中是可选的，另一种是强制参数。

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a>另请参阅

[Cmdlet 参数集](./cmdlet-parameter-sets.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
