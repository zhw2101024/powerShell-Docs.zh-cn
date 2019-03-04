---
title: 声明属性作为参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f71ea35d-cff5-4e44-a5c6-3a747ed4c4d9
caps.latest.revision: 9
ms.openlocfilehash: 6f6640afb15b3608669538f9b5f53d7a8a5c380d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861373"
---
# <a name="declaring-properties-as-parameters"></a>将属性声明为参数

本主题提供了声明的参数的 cmdlet 之前，您必须了解的基本信息。

若要声明 cmdlet 类中的 cmdlet 的参数，请定义公共属性表示每个参数，并将一个或多个参数属性添加到每个属性。 Windows PowerShell 运行时使用的参数属性来标识作为 cmdlet 参数的属性。 声明参数属性的基本语法是`[Parameter()]`。

下面是属性的定义为必需的参数的示例。

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

以下是要记住有关参数的一些事项。

- 参数必须显式标记为公共。 未标记为公共的默认为内部和 Windows PowerShell 运行时将不会找到的参数。

- 参数应定义为 Microsoft.NET Framework 类型，以提供更好的参数验证。 例如，限制为一个值超出的一组值的参数应定义为枚举类型。 获取统一资源标识符 (URI) 值的参数应为类型[System.Uri](/dotnet/api/System.Uri)。

- 避免以外的所有的自由格式文本属性的基本字符串参数。

- 可以将参数添加到任意数量的参数集。 有关参数集的详细信息，请参阅[Cmdlet 参数可设置](./cmdlet-parameter-sets.md)。

Windows PowerShell 还提供了一组会自动提供给每个 cmdlet 的常见参数。 有关这些参数及其各自的别名的详细信息，请参阅[Cmdlet 流通用参数](./common-parameter-names.md)。

## <a name="see-also"></a>另请参阅

[Cmdlet 常见参数](./common-parameter-names.md)

[类型的 Cmdlet 参数](./types-of-cmdlet-parameters.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
