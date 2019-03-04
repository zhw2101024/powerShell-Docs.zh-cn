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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859693"
---
# <a name="how-to-declare-parameter-sets"></a>如何声明参数集

此示例演示如何声明一个 cmdlet 的参数时定义两个参数集。 每个参数集具有唯一的参数和两个参数集使用了共享的参数。 有关参数集，包括如何指定默认参数集，请参阅[Cmdlet 参数可设置](./cmdlet-parameter-sets.md)。

> [!IMPORTANT]
> 只要有可能，定义一个参数为必需的参数集的唯一参数。 但是，如果你想在 cmdlet 运行而无需指定任何参数，唯一的参数可以是一个可选参数。 例如，唯一的参数`Get-Command`cmdlet 是可选的。

## <a name="how-to-define-two-parameter-sets"></a>如何定义两个参数集

1. 添加`ParameterSet`到第一个参数集的唯一参数的参数属性的关键字。

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

2. 添加`ParameterSet`到第二个参数集的唯一参数的参数属性的关键字。

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

3. 对于属于这两个参数集参数，添加每个参数集的参数属性，然后添加`ParameterSet`到每个集的关键字。 在每个参数属性，可以指定该参数的定义方式。 参数可以是中一组可选的在另一个强制性。

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
