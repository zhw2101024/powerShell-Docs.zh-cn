---
title: 将属性声明为参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365746"
---
# <a name="declaring-properties-as-parameters"></a>将属性声明为参数

本主题提供在声明 cmdlet 参数之前必须了解的基本信息。

若要声明 cmdlet 类中 cmdlet 的参数，请定义表示每个参数的公共属性，然后将一个或多个参数特性添加到每个属性。 Windows PowerShell 运行时使用参数属性将属性标识为 cmdlet 参数。 用于声明参数特性的基本语法为 `[Parameter()]`。

下面是一个定义为所需参数的属性示例。

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

下面是一些关于参数的注意事项。

- 参数必须显式标记为公共。 未标记为 "公共" 的参数默认为内部参数，将不会被 Windows PowerShell 运行时发现。

- 应将参数定义为 Microsoft .NET 框架类型，以提供更好的参数验证。 例如，限制为一组值中的一个值的参数应定义为枚举类型。 采用统一资源标识符（URI）值的参数[的类型应为 system.string。](/dotnet/api/System.Uri)

- 避免为所有自由格式的文本属性提供基本的字符串参数。

- 可以将参数添加到任意数量的参数集。 有关参数集的详细信息，请参阅[Cmdlet 参数集](./cmdlet-parameter-sets.md)。

Windows PowerShell 还提供了一组自动可用于每个 cmdlet 的通用参数。 有关这些参数及其别名的详细信息，请参阅[Cmdlet 公用参数](./common-parameter-names.md)。

## <a name="see-also"></a>另请参阅

[Cmdlet 通用参数](./common-parameter-names.md)

[Cmdlet 参数的类型](./types-of-cmdlet-parameters.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
