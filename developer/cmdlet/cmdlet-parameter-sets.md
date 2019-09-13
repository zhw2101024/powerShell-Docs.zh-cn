---
title: Cmdlet 参数集 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: d8c00c7ffd369a32af151836785a2c5f47b05a68
ms.sourcegitcommit: 889b93d170aeb3d444288e7ccf67e62ce822cb7c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70936204"
---
# <a name="cmdlet-parameter-sets"></a>Cmdlet 参数集

PowerShell 使用参数集来编写单个 cmdlet，该 cmdlet 可以针对不同的方案执行不同的操作。 参数集使你可以向用户公开不同参数。 和，根据用户指定的参数返回不同的信息。

## <a name="examples-of-parameter-sets"></a>参数集的示例

例如，PowerShell `Get-EventLog` cmdlet 返回不同的信息，具体取决于用户是否指定了**List**或**LogName**参数。 如果指定了**List**参数，则 cmdlet 将返回有关日志文件本身的信息，而不返回这些日志文件所包含的事件信息。 如果指定了**LogName**参数，则 cmdlet 将返回有关特定事件日志中的事件的信息。 **List**和**LogName**参数标识两个单独的参数集。

## <a name="unique-parameter"></a>唯一参数

每个参数集都必须具有一个唯一参数，该参数由 PowerShell 运行时用来公开相应的参数集。 如果可能，唯一参数应该是必需参数。 如果参数是必需的，则用户必须指定参数，并且 PowerShell 运行时使用该参数来标识参数集。 如果 cmdlet 设计为在不指定任何参数的情况下运行，则 unique 参数不是必需的。

## <a name="multiple-parameter-sets"></a>多个参数集

在下图中，左栏显示了三个有效的参数集。 **参数 A**对于第一个参数集是唯一的，**参数 B**对于第二个参数集是唯一的，而**参数 C**对第三个参数集是唯一的。 在右列中，参数集没有唯一参数。

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>参数集要求

以下要求适用于所有参数集。

- 每个参数集必须至少具有一个唯一参数。 如果可能，请将此参数设置为必需参数。

- 包含多个位置参数的参数集必须为每个参数定义唯一的位置。 无两个位置参数可以指定同一位置。

- 集内只有一个参数可以用`ValueFromPipeline` `true`值声明关键字。
  多个参数可以使用`ValueFromPipelineByPropertyName` `true`值定义关键字。

- 如果未指定参数的参数集，则参数属于所有参数集。

> [!NOTE]
> 对于 cmdlet 或函数，有32个参数集的限制。

## <a name="default-parameter-sets"></a>默认参数集

如果定义了多个参数集，则可以使用`DefaultParameterSetName` **Cmdlet**特性的关键字来指定默认参数集。 如果 PowerShell 无法根据命令提供的信息确定要使用的参数集，则它将使用默认参数集。 有关**cmdlet**特性的详细信息，请参阅[cmdlet 特性声明](./cmdlet-attribute-declaration.md)。

## <a name="declaring-parameter-sets"></a>声明参数集

若要创建参数集，您必须在为`ParameterSetName`参数集中的每个参数声明**参数**属性时指定关键字。 对于属于多个参数集的参数，请为每个参数集添加一个**参数**特性。 此特性使你能够以不同的方式为每个参数集定义参数。 例如，可以在一组中将参数定义为强制参数，并在另一个集中定义为可选参数。 但是，每个参数集必须包含一个唯一参数。 有关详细信息，请参阅[参数属性声明](parameter-attribute-declaration.md)。

在下面的示例中， **UserName**参数是`Test01`参数集的唯一参数， **ComputerName**参数`Test02`是参数集的唯一参数。 **SharedParam**参数属于这两个集并且对于`Test01`参数集是必需的， `Test02`但对于参数集是可选的。

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
private string sharedParam;
```
