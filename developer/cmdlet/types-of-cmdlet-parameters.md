---
title: Cmdlet 参数的类型 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059569"
---
# <a name="types-of-cmdlet-parameters"></a>Cmdlet 参数的类型

本主题介绍不同类型的参数可以声明在 cmdlet 中。 Cmdlet 参数可以是位置、 命名、 必需、 可选的或开关参数。

## <a name="positional-and-named-parameters"></a>定位和命名参数

所有 cmdlet 参数都是已命名或位置参数。 一个命名的参数需要调用 cmdlet 时键入参数名称和参数。 位置参数仅要求您键入的参数中的相对顺序。 然后，系统将第一个未命名的参数映射到第一个位置参数。 系统将第二个未命名的参数映射到第二个未命名的参数，依此类推。 默认情况下，所有 cmdlet 参数被都命名参数。

若要定义一个命名的参数，则忽略`Position`中的关键字**参数**特性声明，如下面的参数声明中所示。

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

若要定义的位置参数，添加`Position`参数中的关键字属性声明中，，然后指定位置。 在以下示例中，`UserName`参数声明为具有位置 0 位置参数。 这意味着调用的第一个参数将自动绑定到此参数。

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> 好 cmdlet 设计推荐的最常用的参数声明为位置参数，以便用户无需运行该 cmdlet 时输入的参数名称。

位置和名称参数接受单个参数或逗号分隔的多个自变量。 仅当该参数接受字符串的一个数组，如集合允许多个参数。 您可能混合在同一个 cmdlet 中的位置和名称参数。 在这种情况下，系统首先，检索命名的参数，然后尝试映射剩余未命名位置参数的参数。

以下命令演示了可以在其中指定单个和多个自变量的参数的不同方式`Get-Command`cmdlet。 请注意，在最后两个示例中，**的名称**不需要指定，因为`Name`参数定义为位置参数。

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>必需和可选参数

您还可以定义 cmdlet 参数为必需或可选参数。 （Windows PowerShell 运行时调用该 cmdlet 之前，必须指定必需参数。）默认情况下，定义为可选参数。

若要定义必需参数，请添加`Mandatory`参数中的关键字属性声明中，并将其设置为`true`，如下面的参数声明中所示。

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

若要定义可选参数，请省略`Mandatory`中的关键字**参数**特性声明，如下面的参数声明中所示。

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a>开关参数

Windows PowerShell 提供了[System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)允许你定义一个参数的值的类型自动设置为`false`如果 cmdlet 时未指定此参数调用。 只要可能，使用代替布尔参数的开关参数。

请考虑下面的示例。 默认情况下，多个 Windows PowerShell cmdlet 不将传递管道向下的输出对象。 但是，这些 cmdlet 具有`PassThru`开关重写默认行为的参数。 如果`PassThru`调用这些 cmdlet 时指定参数，该 cmdlet 将返回到管道输出对象。

如果需要该参数具有默认值为`true`时在调用中未指定参数，请考虑反转参数的意义上说。 有关示例，而不是将参数属性设置为布尔值`true`，将属性声明为[System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)类型，然后设置的参数的默认值`false`.

若要定义一个开关参数，将属性声明为[System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)类型，如下面的示例中所示。

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

若要使作用于该参数指定私钥时，该 cmdlet，使用以下结构中的输入处理方法之一。

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
