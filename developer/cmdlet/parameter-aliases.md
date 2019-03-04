---
title: 参数别名 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853313"
---
# <a name="parameter-aliases"></a>参数别名

Cmdlet 参数也可以有别名。 键入或在命令中指定参数时，可以使用别名而不是参数名称。

## <a name="benefits-of-using-aliases"></a>使用别名的好处

将别名添加到参数提供以下优势。

- 可以提供一种快捷方式，以便用户无需调用 cmdlet 时，使用完整的参数名称。 例如，您可以使用"CN"别名而不是参数名称"ComputerName"。

- 如果您想要提供不同的名称相同的参数，可以定义多个别名。 您可能想要定义多个别名，如果您需要使用不同的方式引用的相同数据的多个用户组。

- 您可以向后兼容性为提供现有脚本的参数的名称更改。

- 通过使用别名属性以及 ValueFromPipelineByName 属性，可以定义一个参数，它允许您 cmdlet 将绑定到不同的对象类型。 例如，假设您有两个不同类型的对象的第一个对象具有编写器属性和第二个对象具有一个编辑器属性。 如果你的 cmdlet 有一个参数，必须接受管道输入属性名称中基于编写器和编辑器别名和 cmdlet，cmdlet 可以将绑定到这两个对象使用两个参数的别名。

有关可以用于特定参数的别名的详细信息，请参阅[通用参数名称](./common-parameter-names.md)。

## <a name="defining-parameter-aliases"></a>定义参数的别名

若要定义参数的别名，声明别名属性，如下面的参数声明中所示。 在此示例中，相同的参数定义多个别名。 (有关详细信息，请参阅[如何声明 Cmdlet 参数](./how-to-declare-cmdlet-parameters.md)。)

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a>另请参阅

[常见的参数名称](./common-parameter-names.md)

[如何声明 Cmdlet 参数](./how-to-declare-cmdlet-parameters.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
