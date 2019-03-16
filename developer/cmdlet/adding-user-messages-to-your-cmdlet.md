---
title: 将用户消息添加到你的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WriteWarning
- notifications, writing
- progress notification
- WriteVerbose
- Stop-Proc
- WriteProgress
- WriteDebug
- notifications, debug
- ProgressRecord
- samples, Stop-Proc cmdlet
- notifications, progress
- notifications, warning
- WriteObject
- WriteError
- verbose notification
- ProcessRecord
- notifications, verbose
- debug notification
- cmdlet, writing notifications
- warning
- code sample, user notifications
- user notifications
ms.assetid: 14c13acb-f0b7-4613-bc7d-c361d14da1a2
caps.latest.revision: 8
ms.openlocfilehash: 5b3a5f5d5d02c7d5a3c1d622ec1a3740739c694f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055030"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>向 Cmdlet 添加用户消息

Cmdlet 可以编写多种类型的可由 Windows PowerShell 运行时向用户显示的消息。 这些消息包括以下类型：

- 包含常规用户信息的详细信息。

- 调试包含故障排除信息的消息。

- 警告消息包含一条通知，该 cmdlet 即将执行的操作可以具有意外的结果。

- 包含数量相关信息的消息处理该 cmdlet 的进度报告已完成时执行时间较长的操作。

没有针对你的 cmdlet 可以写入的消息数或的 cmdlet 将写入的消息类型的限制。 中的输入处理方法的 cmdlet 从特定的调用，从而写入每条消息。

## <a name="the-stopproc-cmdlet"></a>StopProc Cmdlet

在本部分中的主题包括：

- [定义 Cmdlet](#Defining-the-Cmdlet)

- [系统修改为定义参数](#Defining-Parameters-for-System-Modification)

- [重写方法的处理的输入](#Overriding-an-Input-Processing-Method)

- [写入详细消息](#Writing-a-Verbose-Message)

- [写入调试消息](#Writing-a-Debug-Message)

- [编写一条警告消息](#Writing-a-Warning-Message)

- [写入进度消息](#Writing-a-Progress-Message)

- [代码示例](#Code-Sample)

- [定义对象类型和格式设置](#Define-Object-Types-and-Formatting)

- [生成该 Cmdlet](#Building-the-Cmdlet)

- [测试 Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>定义 Cmdlet

Cmdlet 创建的第一步是始终命名 cmdlet 和实现该 cmdlet 的.NET 类声明。 任何类型的 cmdlet 可以从其输入处理方法; 这些方法中编写用户通知因此，一般情况下，您可以命名使用任何谓词，指示该 cmdlet 将执行哪些系统修改此 cmdlet。 有关已批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 的动词名称](./approved-verbs-for-windows-powershell-commands.md)。

停止进程 cmdlet 专门用于修改系统;因此， [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .NET 类的声明必须包括`SupportsShouldProcess`属性关键字，并设置为`true`。

以下代码是此停止进程 cmdlet 类的定义。 有关此定义的详细信息，请参阅[创建一个 Cmdlet 来修改系统](./creating-a-cmdlet-that-modifies-the-system.md)。

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>系统修改为定义参数

停止进程 cmdlet 定义了三个参数： `Name`， `Force`，和`PassThru`。 有关定义这些参数的详细信息，请参阅[创建一个 Cmdlet 来修改系统](./creating-a-cmdlet-that-modifies-the-system.md)。

下面是停止进程 cmdlet 的参数声明。

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a>重写方法的处理的输入

你的 cmdlet 必须重写方法的处理的输入，则将其最常[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。 此停止进程 cmdlet 覆盖[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)输入处理方法。 在停止进程 cmdlet 的此实现中，调用都要写入详细消息、 调试消息和警告消息。

> [!NOTE]
> 有关如何调用此方法的详细信息[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)并[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，请参阅[创建一个 Cmdlet 来修改系统](./creating-a-cmdlet-that-modifies-the-system.md)。

## <a name="writing-a-verbose-message"></a>写入详细消息

[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法用于编写与特定的错误情况无关的常规用户级别信息。 然后，系统管理员可以使用该信息以继续处理其他命令。 此外，根据需要使用此方法编写的任何信息应该被本地化。

此停止进程 cmdlet 中的以下代码显示了两次调用[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法的重写从[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a>写入调试消息

[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法用于编写可用于排除该 cmdlet 的操作的问题的调试消息。 从输入处理方法进行调用。

> [!NOTE]
> Windows PowerShell 还定义`Debug`参数显示两者详细和调试信息。 如果你的 cmdlet 支持此参数，它不需要调用[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)中调用的相同代码[System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).

以下两个部分的示例停止进程 cmdlet 中的代码显示调用[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法的重写从[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。

此调试消息写入之前[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用。

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

此调试消息写入之前[System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)调用。

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows PowerShell 会自动将任何路由[System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)对跟踪基础结构和 cmdlet 的调用。 这样，方法调用，而无需执行任何额外的开发工作中该 cmdlet 追溯到宿主应用程序、 文件或调试器。 以下命令行条目实现跟踪操作。

**PS > 跟踪表达式停止的进程的文件 proc.log-命令停止进程记事本**

## <a name="writing-a-warning-message"></a>编写一条警告消息

[System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法用于该 cmdlet 时要执行的操作可能具有意外的结果，例如，覆盖只读文件写入一条警告。

示例停止进程 cmdlet 从下面的代码演示在调用[System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法的重写从[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a>写入进度消息

[System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)用于 cmdlet 操作需要较长的时间才能完成时写入进度消息。 调用[System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)将传递[System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord)发送到主机应用程序向用户呈现的对象。

> [!NOTE]
> 此停止进程 cmdlet 不包括调用[System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)方法。

以下代码是编写尝试将项复制一个 cmdlet 的进度消息的示例。

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a>代码示例

有关完整C#示例代码，请参阅[StopProcessSample02 示例](./stopprocesssample02-sample.md)。

## <a name="define-object-types-and-formatting"></a>定义对象类型和格式设置

Windows PowerShell cmdlet 使用.NET 对象之间传递信息。 因此，一个 cmdlet 可能需要定义其自己的类型，或者该 cmdlet 可能需要扩展现有类型提供的另一个 cmdlet。 有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。

## <a name="building-the-cmdlet"></a>生成该 Cmdlet

执行后一个 cmdlet，它必须向注册 Windows PowerShell 通过 Windows PowerShell 管理单元。 有关注册 cmdlet 的详细信息，请参阅[如何注册 Cmdlet、 提供商和主机应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-cmdlet"></a>测试 Cmdlet

当已使用 Windows PowerShell 注册你的 cmdlet 时，可以通过运行命令行上测试它。 让我们测试示例停止进程 cmdlet。 有关使用命令行中的 cmdlet 的详细信息，请参阅[Windows PowerShell 入门学习](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

- 以下命令行条目使用停止的进程停止名为"NOTEPAD"的进程、 提供详细的通知，并打印调试信息。

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

将显示以下输出。

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a>另请参阅

[创建用于修改系统的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)

[如何创建 Windows PowerShell Cmdlet](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[如何注册 Cmdlet、 提供程序，和托管应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)
