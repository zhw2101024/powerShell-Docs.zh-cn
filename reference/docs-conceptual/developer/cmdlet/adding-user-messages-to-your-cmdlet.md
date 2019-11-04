---
title: 将用户消息添加到 Cmdlet |Microsoft Docs
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
ms.openlocfilehash: 1e048f6ae94ac226218c18c8f8f7590a4db26226
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72370066"
---
# <a name="adding-user-messages-to-your-cmdlet"></a>向 Cmdlet 添加用户消息

Cmdlet 可以编写多种消息，Windows PowerShell 运行时可向用户显示这些消息。 这些消息包括以下类型：

- 包含常规用户信息的详细消息。

- 调试包含故障排除信息的消息。

- 警告消息，其中包含 cmdlet 要执行可能产生意外结果的操作的通知。

- 进度报告消息，其中包含有关在执行耗时很长的操作时 cmdlet 已完成的工作量的信息。

Cmdlet 可以写入的消息数或 cmdlet 写入的消息类型没有限制。 每条消息都是通过从 cmdlet 的输入处理方法中进行特定调用来编写的。

## <a name="defining-the-cmdlet"></a>定义 Cmdlet

创建 cmdlet 的第一步是始终命名 cmdlet 并声明实现 cmdlet 的 .NET 类。 任何类型的 cmdlet 都可以从其输入处理方法写入用户通知;因此，一般情况下，可以使用指示 cmdlet 执行的系统修改的任何谓词来命名此 cmdlet。 有关批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 谓词名称](./approved-verbs-for-windows-powershell-commands.md)。

停止过程 cmdlet 用于修改系统;因此，.NET 类的[CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)声明必须包含 `SupportsShouldProcess` attribute 关键字，并将设置为 `true`。

下面的代码是此 Stop Proc cmdlet 类的定义。 有关此定义的详细信息，请参阅[创建修改系统的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>定义系统修改的参数

停止过程 cmdlet 定义三个参数： `Name`、`Force` 和 `PassThru`。 有关定义这些参数的详细信息，请参阅[创建修改系统的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。

下面是用于停止过程 cmdlet 的参数声明。

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

## <a name="overriding-an-input-processing-method"></a>重写输入处理方法

Cmdlet 必须重写输入处理方法，最常见的方法是[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。 此 ProcessRecord cmdlet 将重写 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 输入处理方法。 在此过程中，将调用来编写详细消息、调试消息和警告消息。

> [!NOTE]
> 有关此方法如何调用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法的详细信息，请参阅[创建用于修改系统的 Cmdlet （& a）：创建用于修改系统的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。

## <a name="writing-a-verbose-message"></a>编写详细消息

[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法用于写入与特定错误条件不相关的常规用户级别信息的情况。 然后，系统管理员可以使用该信息继续处理其他命令。 此外，使用此方法编写的任何信息都应该根据需要进行本地化。

此 Stop Proc cmdlet 中的以下代码演示了对[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法的两次调用，从[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的重写中的重写。

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a>编写调试消息

[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法用于编写调试消息，这些消息可用于排查 Cmdlet 的操作问题的问题。 从输入处理方法进行调用。

> [!NOTE]
> Windows PowerShell 还定义了一个 `Debug` 参数，用于提供详细信息和调试信息。 如果你的 cmdlet 支持此参数，则它不需要在调用[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)的相同代码中调用[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) ，而不需要调用。

以下两个示例中的代码部分将从 [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 方法中调用，以从 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 方法的重写中，显示对方法的调用。

此调试消息将在调用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)之前立即写入。

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

此调试消息将在调用[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)之前立即写入。

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

Windows PowerShell 会自动将任何[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)调用路由到跟踪基础结构和 cmdlet。 这允许对宿主应用程序、文件或调试器跟踪方法调用，而无需在 cmdlet 中进行任何额外的开发工作。 以下命令行项实现跟踪操作。

**PS > trace 表达式停止进程文件过程。日志命令停止-过程记事本**

## <a name="writing-a-warning-message"></a>写入警告消息

当 Cmdlet 要执行可能产生意外结果的操作时（例如，覆盖只读文件），将使用[WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法来编写一条警告，并使用该方法。

以下来自 [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) cmdlet 的代码演示了如何从 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 方法的重写调用中调用了对方法的调用的方法中。

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

当 Cmdlet 操作需要很长时间才能完成时，将使用[WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)来写入进度消息。 对[WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)的调用会传递发送到宿主应用程序的[Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord)对象，以便向用户呈现该对象的功能。

> [!NOTE]
> 此 Stop Proc cmdlet 不包括对[WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)方法的调用。 "。

下面的代码示例是由尝试复制项的 cmdlet 编写的进度消息。

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

有关完整C#的示例代码，请参阅[StopProcessSample02 示例](./stopprocesssample02-sample.md)。

## <a name="define-object-types-and-formatting"></a>定义对象类型和格式设置

Windows PowerShell 使用 .NET 对象在 cmdlet 之间传递信息。 因此，cmdlet 可能需要定义自己的类型，或者该 cmdlet 可能需要扩展另一个 cmdlet 提供的现有类型。 有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式](/previous-versions//ms714665(v=vs.85))。

## <a name="building-the-cmdlet"></a>构建 Cmdlet

实现 cmdlet 后，必须通过 Windows PowerShell 管理单元向 Windows PowerShell 注册它。 有关注册 cmdlet 的详细信息，请参阅[如何注册 cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))。

## <a name="testing-the-cmdlet"></a>测试 Cmdlet

向 Windows PowerShell 注册 cmdlet 后，可以通过在命令行上运行 cmdlet 来对其进行测试。 接下来，请测试示例的停止过程 cmdlet。 有关从命令行使用 cmdlet 的详细信息，请参阅[使用 Windows PowerShell 的入门](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

- 以下命令行条目使用 Stop 进程来停止名为 "NOTEPAD" 的进程，提供详细通知并打印调试信息。

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

此时将显示以下输出。

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

[如何创建 Windows PowerShell Cmdlet](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[扩展对象类型和格式](/previous-versions//ms714665(v=vs.85))

[如何注册 Cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
