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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369586"
---
# <a name="parameter-aliases"></a>参数别名

Cmdlet 参数还可以有别名。 在命令中键入或指定参数时，可以使用别名，而不是参数名称。

## <a name="benefits-of-using-aliases"></a>使用别名的好处

将别名添加到参数提供以下优点。

- 您可以提供一个快捷方式，以便用户在调用 cmdlet 时不必使用完整的参数名称。 例如，可以使用 "CN" 别名，而不是参数名称 "ComputerName"。

- 如果要为同一参数提供不同的名称，可以定义多个别名。 如果必须使用以不同方式引用相同数据的多个用户组，则可能需要定义多个别名。

- 如果参数名称发生更改，则可以为现有脚本提供向后兼容性。

- 通过使用 Alias 属性和 ValueFromPipelineByName 属性，可以定义一个参数，该参数允许 cmdlet 绑定到不同的对象类型。 例如，假设您有两个不同类型的对象，第一个对象有一个写入器属性，并且第二个对象有一个编辑器属性。 如果 cmdlet 有一个参数，该参数具有编写器和编辑器别名，并且 cmdlet 已根据属性名称接受管道输入，则 cmdlet 可以使用两个参数别名绑定到这两个对象。

有关可用于特定参数的别名的详细信息，请参阅[通用参数名称](./common-parameter-names.md)。

## <a name="defining-parameter-aliases"></a>定义参数别名

若要为参数定义别名，请声明 Alias 特性，如下面的参数声明中所示。 在此示例中，为同一参数定义了多个别名。 （有关详细信息，请参阅[如何声明 Cmdlet 参数](./how-to-declare-cmdlet-parameters.md)。）

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

[常见参数名称](./common-parameter-names.md)

[如何声明 Cmdlet 参数](./how-to-declare-cmdlet-parameters.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
