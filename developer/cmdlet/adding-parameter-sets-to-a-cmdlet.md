---
title: 将参数添加到 Cmdlet 设置 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameter sets [PowerShell Programmer's Guide]
ms.assetid: a6131db4-fd6e-45f1-bd47-17e7174afd56
caps.latest.revision: 8
ms.openlocfilehash: b02a2e0d4b0a27c261b0bc05febda7826ad5276e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859263"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a>向 Cmdlet 添加参数集

本部分介绍如何添加参数设置为 Stop Proc cmdlet (中所述[创建一个 Cmdlet 来修改系统](./creating-a-cmdlet-that-modifies-the-system.md))。 类似于此编程人员的指南中所述的其他进程停止外 cmdlet，此 cmdlet 会尝试停止使用 Get-proc cmdlet 检索的进程 (中所述[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md))。

在本部分中的主题包括：

- [关于参数集点提示](#Adding-Parameter-Sets-to-a-Cmdlet)

- [声明 Cmdlet 类](#Declaring-the-Cmdlet-Class)

- [声明 Cmdlet 的参数](#Declaring-the-Parameters-of-the-Cmdlet)

- [重写方法的处理的输入](#Overriding-an-Input-Processing-Method)

- [代码示例](#Declaring-the-Parameters-of-the-Cmdlet)

- [定义对象类型和格式设置](#Defining-Object-Types-and-Formatting)

- [生成该 Cmdlet](#Building-the-Cmdlet)

- [测试 Cmdlet](#Testing-the-Cmdlet)

## <a name="things-to-know-about-parameter-sets"></a>关于参数集点提示

Windows PowerShell 定义参数设置为一起运行的参数组。 通过对 cmdlet 的参数进行分组，可以创建的单个 cmdlet，可以更改基于参数哪组用户指定其功能。

使用两个参数集来定义不同功能的 cmdlet 的一个示例是`Get-EventLog`提供的 Windows PowerShell cmdlet。 此 cmdlet 将返回不同的信息时用户指定`List`或`LogName`参数。 如果`LogName`指定参数，则该 cmdlet 返回给定事件日志中有关事件的信息。 如果`List`指定参数，该 cmdlet 将返回有关日志的信息文件本身 （而非它们所包含事件信息）。 在这种情况下，`List`和`LogName`参数标识两个单独的参数集。

需要记住有关参数集的两个重要事项是，Windows PowerShell 运行时使用只有一个参数设置为某一特定的输入，以及每个参数集必须具有至少一个参数，是唯一的参数集。

为了说明该最后一个点，此停止进程 cmdlet 使用三个参数集： `ProcessName`， `ProcessId`，和`InputObject`。 每个这些参数集有一个参数，它不在其他参数集。 参数集可能共享其他参数，但此 cmdlet 将使用唯一的参数`ProcessName`， `ProcessId`，和`InputObject`来标识的组的 Windows PowerShell 运行时应使用的参数。

## <a name="declaring-the-cmdlet-class"></a>声明 Cmdlet 类

Cmdlet 创建的第一步是始终命名 cmdlet 和实现该 cmdlet 的.NET 类声明。 对于此 cmdlet，因为该 cmdlet 会停止系统进程使用生命周期谓词"Stop"。 由于 cmdlet 适用于进程，则使用名词名称"过程"。 在以下声明中，请注意 cmdlet 动词和名词名称将反映在 cmdlet 类的名称。

> [!NOTE]
> 已批准的 cmdlet 的动词名称有关的详细信息，请参阅[Cmdlet 的动词名称](./approved-verbs-for-windows-powershell-commands.md)。

以下代码是此停止进程 cmdlet 的类定义。

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        DefaultParameterSetName = "ProcessId",
        SupportsShouldProcess = true)]
public class StopProcCommand : PSCmdlet
```

```vb
<Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
SupportsShouldProcess:=True)> _
Public Class StopProcCommand
    Inherits PSCmdlet
```

## <a name="declaring-the-parameters-of-the-cmdlet"></a>声明 Cmdlet 的参数

此 cmdlet 定义作为到 cmdlet （这些参数定义的参数集），输入所需的三个参数以及`Force`管理 cmdlet 的用途的参数和一个`PassThru`确定是否将发送该 cmdlet 的参数通过管道的输出对象。 默认情况下，此 cmdlet 不将传递的对象通过管道。 有关这些最后两个参数的详细信息，请参阅[创建一个 Cmdlet 来修改系统](./creating-a-cmdlet-that-modifies-the-system.md)。

### <a name="declaring-the-name-parameter"></a>声明名称参数

此输入的参数允许用户以指定要停止的进程的名称。 请注意，`ParameterSetName`属性的关键字[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)特性指定`ProcessName`参数设置为此参数。

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

```vb
<Parameter(Position:=0, ParameterSetName:="ProcessName", _
Mandatory:=True, _
ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
HelpMessage:="The name of one or more processes to stop. " & _
    "Wildcards are permitted."), [Alias]("ProcessName")> _
Public Property Name() As String()
    Get
        Return processNames
    End Get
    Set(ByVal value As String())
        processNames = value
    End Set
End Property

Private processNames() As String
```

此外请注意，此参数为给定别名"ProcessName"。

### <a name="declaring-the-id-parameter"></a>声明的 Id 参数

此输入的参数允许用户指定要停止的进程的标识符。 请注意，`ParameterSetName`属性的关键字[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)特性指定`ProcessId`参数集。

```csharp
[Parameter(
           ParameterSetName = "ProcessId",
           Mandatory = true,
           ValueFromPipelineByPropertyName = true,
           ValueFromPipeline = true
)]
[Alias("ProcessId")]
public int[] Id
{
  get { return processIds; }
  set { processIds = value; }
}
private int[] processIds;
```

```vb
<Parameter(ParameterSetName:="ProcessId", _
Mandatory:=True, _
ValueFromPipelineByPropertyName:=True, _
ValueFromPipeline:=True), [Alias]("ProcessId")> _
Public Property Id() As Integer()
    Get
        Return processIds
    End Get
    Set(ByVal value As Integer())
        processIds = value
    End Set
End Property
Private processIds() As Integer
```

此外请注意，此参数为给定别名"ProcessId"。

### <a name="declaring-the-inputobject-parameter"></a>InputObject 参数声明

此输入的参数允许用户指定包含要停止的进程有关的信息的输入的对象。 请注意，`ParameterSetName`属性的关键字[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)特性指定`InputObject`参数设置为此参数。

```csharp
[Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
public Process[] InputObject
{
  get { return inputObject; }
  set { inputObject = value; }
}
private Process[] inputObject;
```

```vb
<Parameter(ParameterSetName:="InputObject", _
Mandatory:=True, ValueFromPipeline:=True)> _
Public Property InputObject() As Process()
    Get
        Return myInputObject
    End Get
    Set(ByVal value As Process())
        myInputObject = value
    End Set
End Property
Private myInputObject() As Process
```

另请注意，此参数有无别名。

### <a name="declaring-parameters-in-multiple-parameter-sets"></a>声明中多个参数集的参数

尽管必须为每个参数集的唯一参数，参数可以属于多个参数集。 在这些情况下，提供共享的参数[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)特性声明的每个设置该参数属于。 如果参数是在所有参数集，只有一次声明参数属性且不需要指定该参数设置名称。

## <a name="overriding-an-input-processing-method"></a>重写方法的处理的输入

每个 cmdlet 必须重写方法的处理的输入，这是最常[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。 此 cmdlet 中[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法被重写，以便该 cmdlet 可以处理任意数量的进程。 它包含用户对哪些参数集基于另一种方法的调用具有指定的 Select 语句。

```csharp
protected override void ProcessRecord()
{
  switch (ParameterSetName)
  {
    case "ProcessName":
         ProcessByName();
         break;

    case "ProcessId":
         ProcessById();
         break;

    case "InputObject":
         foreach (Process process in inputObject)
         {
           SafeStopProcess(process);
         }
         break;

    default:
         throw new ArgumentException("Bad ParameterSet Name");
  } // switch (ParameterSetName...
} // ProcessRecord
```

```vb
Protected Overrides Sub ProcessRecord()
    Select Case ParameterSetName
        Case "ProcessName"
            ProcessByName()

        Case "ProcessId"
            ProcessById()

        Case "InputObject"
            Dim process As Process
            For Each process In myInputObject
                SafeStopProcess(process)
            Next process

        Case Else
            Throw New ArgumentException("Bad ParameterSet Name")
    End Select

End Sub 'ProcessRecord ' ProcessRecord
```

不在这里，介绍 Select 语句调用的帮助器方法，但您可以看到其实现中下一节中的完整代码示例。

## <a name="code-sample"></a>代码示例

有关完整C#示例代码，请参阅[StopProcessSample04 示例](./stopprocesssample04-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定义对象类型和格式设置

Windows PowerShell cmdlet 使用.NET 对象之间传递信息。 因此，一个 cmdlet 可能需要定义其自己的类型，或者该 cmdlet 可能需要扩展现有类型提供的另一个 cmdlet。 有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。

## <a name="building-the-cmdlet"></a>生成该 Cmdlet

实现一个 cmdlet 之后, 您必须注册它使用 Windows PowerShell 通过 Windows PowerShell 管理单元。 有关注册 cmdlet 的详细信息，请参阅[如何注册 Cmdlet、 提供商和主机应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-cmdlet"></a>测试 Cmdlet

你的 cmdlet 具有已注册到 Windows PowerShell，通过命令行上运行测试。 以下是显示一些测试如何`ProcessId`和`InputObject`参数可用于测试及其参数集，若要停止的进程。

- 借助启动 Windows PowerShell，运行停止进程 cmdlet 与`ProcessId`参数设置为停止进程根据其标识符。 在这种情况下，使用该 cmdlet`ProcessId`参数设置为停止进程。

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- 借助启动 Windows PowerShell，运行停止进程 cmdlet 与`InputObject`参数设置为记事本对象来检索上停止进程`Get-Process`命令。

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>另请参阅

[创建一个 Cmdlet 来修改系统](./creating-a-cmdlet-that-modifies-the-system.md)

[如何创建 Windows PowerShell Cmdlet](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[如何注册 Cmdlet、 提供程序，和托管应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)
