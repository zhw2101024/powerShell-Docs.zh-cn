---
title: Cmdlet 参数可设置 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068502"
---
# <a name="cmdlet-parameter-sets"></a>Cmdlet 参数集

Windows PowerShell 使用参数集，您可以编写的单个 cmdlet，可以执行不同的操作为不同的方案。 参数集使您能够公开给用户的不同参数，并返回基于用户指定的参数的不同信息。

## <a name="examples-of-parameter-sets"></a>参数集的示例

例如， `Get-EventLog` cmdlet （由 Windows PowerShell 提供） 将返回不同的信息，具体取决于用户是否指定`List`或`LogName`参数。 如果`List`指定参数，则该 cmdlet 返回有关日志文件的信息本身，但不是包含事件信息。 如果`LogName`指定参数，则该 cmdlet 返回特定的事件日志中有关事件的信息。 `List`和`LogName`参数标识两个单独的参数集。

## <a name="unique-parameter"></a>唯一的参数

每个参数集必须具有一个唯一的参数，可以使用 Windows PowerShell 运行时公开相应的参数集。 如果可能，唯一的参数应为必需参数。 当一个参数是必需的时强制用户来指定参数，和 Windows PowerShell 运行时可以使用该参数将设置为使用该参数标识。 唯一的参数不能为必需，如果你的 cmdlet 专为运行而无需指定任何参数。

## <a name="multiple-parameter-sets"></a>多个参数集

下图中，在左侧的列显示三个有效的参数集。 一个参数是唯一的第一个参数集，参数 B 是唯一的第二个参数集，参数 C 是唯一的第三个参数集。 但是，在右列中，参数集不具有唯一的参数。

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>参数设置要求

以下要求适用于所有参数集。

- 每个参数集必须具有至少一个唯一的参数。 如果可能，请此参数强制参数。

- 包含多个位置参数的参数集必须定义为每个参数的唯一位置。 两个位置参数可以指定相同的位置。

- 一组中的只有一个参数可以声明`ValueFromPipeline`关键字，值为`true`。 可以定义多个参数`ValueFromPipelineByPropertyName`关键字，值为`true`。

- 如果为参数不指定任何参数集，则该参数属于所有参数集。

## <a name="default-parameter-sets"></a>默认参数集

如果定义多个参数集，可以使用`DefaultParameterSetName`Cmdlet 属性来指定默认参数集的关键字。 Windows PowerShell 使用的默认参数集如果它不能确定参数设置为使用基于命令提供的信息。 Cmdlet 属性有关的详细信息，请参阅[Cmdlet 特性声明](./cmdlet-attribute-declaration.md)。

## <a name="declaring-parameter-sets"></a>声明参数集

若要创建的参数集，必须指定`ParameterSetName`关键字声明中的参数集的每个参数的参数属性时。 对于属于多个参数集的参数，将添加每个参数集的参数属性。 这使您可以定义不同的方式针对每个参数集的参数。 例如，您可以为在一组必需的和可选中另一个定义参数。 但是，每个参数集必须包含一个唯一的参数。

在以下示例中，`UserName`参数是唯一的 Test01 参数集，参数和`ComputerName`参数是 Test02 参数集的唯一参数。 `SharedParam`参数属于这两个集，它是必需的 Test01 参数，但对于 Test02 参数集是可选的设置。

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```