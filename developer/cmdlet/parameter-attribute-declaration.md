---
title: 参数特性声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, Parameter
- Parameter attribute, described
- Parameter attribute
ms.assetid: 08433d0b-169b-42c8-9335-2881d9034698
caps.latest.revision: 13
ms.openlocfilehash: a3488d5fb3f7eb3df28d0242d6c39d07145a3c8d
ms.sourcegitcommit: 10c347a8c3dcbf8962295601834f5ba85342a87b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/07/2019
ms.locfileid: "56863613"
---
# <a name="parameter-attribute-declaration"></a>参数属性声明

参数特性标识为 cmdlet 参数在 cmdlet 类的公共属性。

## <a name="syntax"></a>语法

```csharp
[Parameter()]
[Parameter(Named Parameters...)]
```

#### <a name="parameters"></a>参数

`Mandatory` ([System.Boolean](/dotnet/api/System.Boolean)) 可选的命名参数。 `True` 指示 cmdlet 参数是必需的。 如果未提供一个必需的参数，则调用该 cmdlet 时，Windows PowerShell 会提示用户输入参数值。 默认值为 `false`。

`ParameterSetName` ([System.String](/dotnet/api/System.String)) 可选的命名参数。 指定该参数设置，此 cmdlet 参数属于。 如果不指定任何参数集，则该参数属于所有参数集。

`Position` ([System.Integer](/dotnet/api/System.Integer)) 可选的命名参数。 指定的 Windows PowerShell 命令中的参数的位置。

`ValueFromPipeline` ([System.Boolean](/dotnet/api/System.Boolean)) 可选的命名参数。 `True` 指示此 cmdlet 参数采用其值从管道对象。 指定此关键字，如果该 cmdlet 将访问的完整对象，而不仅仅是对象的属性。 默认值为 `false`。

`ValueFromPipelineByPropertyName` ([System.Boolean](/dotnet/api/System.Boolean)) 可选的命名参数。 `True` 指示此 cmdlet 参数采用其值从具有相同的名称或此参数的别名相同的管道对象的属性。 例如，如果该 cmdlet 具有`Name`参数，而管道对象还具有`Name`属性、 的值`Name`属性分配给`Name`cmdlet 参数。 默认值为 `false`。

`ValueFromRemainingArguments` ([System.Boolean](/dotnet/api/System.Boolean)) 可选的命名参数。 `True` 指示 cmdlet 参数接受所有剩余的自变量传递给该 cmdlet。 默认值为 `false`。

`HelpMessage` 可选的命名参数。 指定参数的简短说明。 Windows PowerShell cmdlet 运行和未指定必需的参数时显示此消息。

`HelpMessageBaseName` 可选的命名参数。指定资源标识符所在的位置。 例如，此参数可以指定包含要本地化的帮助消息的资源程序集。

`HelpMessageResourceId` 可选的命名参数。指定的帮助消息的资源标识符。

## <a name="remarks"></a>备注

- 有关如何声明此属性的详细信息，请参阅[如何声明 Cmdlet 参数](./how-to-declare-cmdlet-parameters.md)。

- 一个 cmdlet 可以具有任意数量的参数。 但是，为了更好的用户体验，限制参数的数目。

- 参数必须声明上公共非静态字段或属性。 应在属性上声明参数。 该属性必须具有公共的 set 访问器，并且如果`ValueFromPipeline`或`ValueFromPipelineByPropertyName`指定关键字，该属性必须具有公共 get 访问器。

- 当您指定位置参数时，限制中将参数设置为小于五的位置参数的数目。 和位置参数不需要是连续的。 位置 5、 100 和 250 工作方式为 0、 1 和 2 的位置相同。

- 当`Position`关键字未指定，则必须通过其名称引用的 cmdlet 参数。

- 使用参数集，请注意以下事项：

    - 每个参数集必须具有至少一个唯一的参数。 好 cmdlet 设计指示该唯一参数还应该强制在可能的情况。 如果你的 cmdlet 专为运行不带参数，唯一的参数不能为必需。

    - 没有参数集应包含多个具有相同的位置的位置参数。

    - 中的参数集只有一个参数应声明`ValueFromPipeline = true`。 可以定义多个参数`ValueFromPipelineByPropertyName = true`。

    - 可以定义多个参数`ValueFromPipelineByPropertyName = true`。

- 有关参数名称的准则的详细信息，请参阅[Cmdlet 参数名称](standard-cmdlet-parameter-names-and-types.md)。

- 参数属性定义由[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)类。

## <a name="see-also"></a>另请参阅

[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)

[Cmdlet 参数名称](standard-cmdlet-parameter-names-and-types.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
