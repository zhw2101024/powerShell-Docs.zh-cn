---
title: 向 Cmdlet 添加参数集 |Microsoft Docs
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
ms.openlocfilehash: c9c0b9a7a587e856efc82b4d277cee373e3f8b38
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416324"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a>向 Cmdlet 添加参数集

## <a name="things-to-know-about-parameter-sets"></a>有关参数集的信息

Windows PowerShell 将参数集定义为一组一起操作的参数。 通过对 cmdlet 的参数进行分组，可以创建单个 cmdlet，该 cmdlet 可以根据用户指定的参数组来更改其功能。

使用两个参数集来定义不同功能的 cmdlet 示例是 Windows PowerShell 提供的 `Get-EventLog` cmdlet。 当用户指定 `List` 或 `LogName` 参数时，此 cmdlet 将返回不同的信息。 如果指定了 `LogName` 参数，则该 cmdlet 将返回有关给定事件日志中的事件的信息。 如果指定了 `List` 参数，则该 cmdlet 将返回有关日志文件本身的信息（而不是它们所包含的事件信息）。 在这种情况下，`List` 和 `LogName` 参数标识两个单独的参数集。

有关参数集的两个重要事项是： Windows PowerShell 运行时仅对特定输入使用一个参数集，并且每个参数集必须至少有一个参数集唯一的参数。

为了说明最后一点，此 Stop 过程 cmdlet 使用三个参数集： `ProcessName`、`ProcessId`和 `InputObject`。 其中每个参数集都具有一个不在其他参数集中的参数。 参数集可以共享其他参数，但 cmdlet 使用唯一参数 `ProcessName`、`ProcessId`和 `InputObject` 来确定 Windows PowerShell 运行时应使用的参数集。

## <a name="declaring-the-cmdlet-class"></a>声明 Cmdlet 类

创建 cmdlet 的第一步是始终命名 cmdlet 并声明实现 cmdlet 的 .NET 类。 对于此 cmdlet，将使用生命周期谓词 "Stop"，因为该 cmdlet 将停止系统进程。 之所以使用名词名称 "Proc"，是因为该 cmdlet 适用于进程。 请注意，在下面的声明中，cmdlet 谓词和名词名称反映在 cmdlet 类的名称中。

> [!NOTE]
> 有关已批准的 cmdlet 谓词名称的详细信息，请参阅[Cmdlet 谓词名称](./approved-verbs-for-windows-powershell-commands.md)。

下面的代码是此 Stop Proc cmdlet 的类定义。

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

此 cmdlet 将定义所需的三个参数作为 cmdlet 的输入（这些参数也定义参数集），并定义一个 `Force` 参数，该参数用于管理 cmdlet 的作用，以及一个确定 cmdlet 是否通过管道发送输出对象的 `PassThru` 参数。 默认情况下，此 cmdlet 不通过管道传递对象。 有关最后两个参数的详细信息，请参阅[创建修改系统的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。

### <a name="declaring-the-name-parameter"></a>声明 Name 参数

此输入参数允许用户指定要停止的进程的名称。 请注意， [Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)属性的 `ParameterSetName` attribute 关键字指定为此参数设置的 `ProcessName` 参数。

[!code-csharp[StopProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

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

另请注意，将别名 "ProcessName" 提供给此参数。

### <a name="declaring-the-id-parameter"></a>声明 Id 参数

此输入参数允许用户指定要停止的进程的标识符。 请注意， [Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)属性的 `ParameterSetName` attribute 关键字指定 `ProcessId` 参数集。

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

另请注意，将别名 "ProcessId" 提供给此参数。

### <a name="declaring-the-inputobject-parameter"></a>声明 InputObject 参数

此输入参数允许用户指定输入对象，该对象包含要停止的进程的相关信息。 请注意， [Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)属性的 `ParameterSetName` attribute 关键字指定为此参数设置的 `InputObject` 参数。

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

另请注意，此参数没有别名。

### <a name="declaring-parameters-in-multiple-parameter-sets"></a>在多个参数集中声明参数

尽管每个参数集必须有一个唯一参数，但参数可以属于多个参数集。 在这些情况下，为共享参数提供参数所属的每个集合的[Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)特性声明。 如果参数在所有参数集中，只需声明参数属性一次，且无需指定参数集名称。

## <a name="overriding-an-input-processing-method"></a>重写输入处理方法

每个 cmdlet 都必须重写输入处理方法，这通常是[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。 在此 cmdlet 中，将重写[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，以使 cmdlet 能够处理任意数量的进程。 它包含一个 Select 语句，该语句基于用户指定的参数来调用其他方法。

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

此处未介绍 Select 语句调用的帮助器方法，但您可以在下一节的完整代码示例中看到它们的实现。

## <a name="code-sample"></a>代码示例

有关完整C#的示例代码，请参阅[StopProcessSample04 示例](./stopprocesssample04-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定义对象类型和格式设置

Windows PowerShell 使用 .NET 对象在 cmdlet 之间传递信息。 因此，cmdlet 可能需要定义自己的类型，或者该 cmdlet 可能需要扩展另一个 cmdlet 提供的现有类型。 有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式](/previous-versions//ms714665(v=vs.85))。

## <a name="building-the-cmdlet"></a>构建 Cmdlet

实现 cmdlet 后，必须通过 Windows PowerShell 管理单元将其注册到 Windows PowerShell。 有关注册 cmdlet 的详细信息，请参阅[如何注册 cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))。

## <a name="testing-the-cmdlet"></a>测试 Cmdlet

向 Windows PowerShell 注册 cmdlet 后，通过在命令行上运行它来对其进行测试。 下面是一些测试，演示如何使用 `ProcessId` 和 `InputObject` 参数来测试它们的参数集以停止进程。

- 启动 Windows PowerShell 后，运行带有 `ProcessId` 参数设置的停止过程 cmdlet，以根据其标识符停止进程。 在这种情况下，该 cmdlet 使用 `ProcessId` 参数集来停止该进程。

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- 启动 Windows PowerShell 后，运行带有 `InputObject` 参数设置的停止过程 cmdlet，以停止 `Get-Process` 命令检索到的 Notepad 对象上的进程。

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>另请参阅

[创建修改系统的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)

[如何创建 Windows PowerShell Cmdlet](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[扩展对象类型和格式](/previous-versions//ms714665(v=vs.85))

[如何注册 Cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
