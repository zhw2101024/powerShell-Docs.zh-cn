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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369306"
---
# <a name="types-of-cmdlet-parameters"></a>Cmdlet 参数的类型

本主题介绍可在 cmdlet 中声明的不同类型的参数。 Cmdlet 参数可以是位置、命名、必需、可选或切换参数。

## <a name="positional-and-named-parameters"></a>位置和命名参数

所有 cmdlet 参数都是命名参数或位置参数。 命名参数要求在调用 cmdlet 时键入参数名称和参数。 位置参数只要求按相对顺序键入参数。 然后，系统将第一个未命名的参数映射到第一个位置参数。 系统会将第二个未命名的参数映射到第二个未命名的参数，依此类推。 默认情况下，所有 cmdlet 参数均为命名参数。

若要定义命名参数，请在**参数**属性声明中省略 @no__t 的关键字，如下面的参数声明中所示。

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

若要定义位置参数，请在参数属性声明中添加 `Position` 关键字，然后指定位置。 在下面的示例中，@no__t 的参数声明为位置为0的位置参数。 这意味着调用的第一个参数将自动绑定到此参数。

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
> 良好的 cmdlet 设计建议将最常使用的参数声明为位置参数，使用户无需在运行 cmdlet 时输入参数名称。

位置和命名参数接受单个参数或用逗号分隔的多个参数。 仅当参数接受集合（如字符串数组）时，才允许使用多个参数。 可以在同一个 cmdlet 中混合位置和命名参数。 在这种情况下，系统首先检索命名参数，然后尝试将其余未命名参数映射到位置参数。

以下命令显示了不同的方法，你可以在其中指定 @no__t cmdlet 的参数的单个参数和多个参数。 请注意，在最后两个示例中， **-name**不需要指定，因为 `Name` 参数定义为位置参数。

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>必需参数和可选参数

你还可以将 cmdlet 参数定义为必需或可选参数。 （必须在 Windows PowerShell 运行时调用 cmdlet 之前指定必需参数。） 默认情况下，将参数定义为可选。

若要定义强制参数，请在参数属性声明中添加 `Mandatory` 关键字，并将其设置为 `true`，如以下参数声明中所示。

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

若要定义可选参数，请在**参数**属性声明中省略 `Mandatory` 关键字，如下面的参数声明中所示。

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

Windows PowerShell 提供[SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)类型，该类型允许您定义一个参数，该参数的值自动设置为 @no__t 如果在调用 cmdlet 时未指定参数，则为-1。 请尽可能使用开关参数代替布尔参数。

请考虑以下示例。 默认情况下，多个 Windows PowerShell cmdlet 不会将输出对象沿管道向下传递。 但是，这些 cmdlet 具有一个 `PassThru` 开关参数，该参数将覆盖默认行为。 如果在调用这些 cmdlet 时指定了 `PassThru` 参数，则 cmdlet 会将输出对象返回到管道。

如果在调用中未指定参数时，需要参数的默认值为 `true`，请考虑反转参数的意义。 对于示例，请将属性声明为[SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)类型，而不是将参数特性设置为的布尔 @no__t 值，然后将该参数的默认值设置为 `false`。

若要定义开关参数，请将属性声明为[SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)类型，如下面的示例中所示。

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

若要使 cmdlet 在指定时对参数执行操作，请在其中一个输入处理方法中使用以下结构。

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
