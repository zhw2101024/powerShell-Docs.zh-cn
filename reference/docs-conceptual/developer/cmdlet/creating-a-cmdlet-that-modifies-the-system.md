---
title: 创建修改系统的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- should process [PowerShell Programmer's Guide]
- should continue [PowerShell Programmer's Guide]
- user feedback [PowerShell Programmer's Guide]
- confirm impact [PowerShell Programmer's Guide]
ms.assetid: 59be4120-1700-4d92-a308-ef4a32ccf11a
caps.latest.revision: 8
ms.openlocfilehash: 8a65915b88a04e36e773853b903528a65fe11e99
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365756"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a>创建用于修改系统的 Cmdlet

有时，cmdlet 必须修改系统的运行状态，而不只是 Windows PowerShell 运行时的状态。 在这些情况下，cmdlet 应该允许用户有机会确认是否要进行更改。

若要支持确认，cmdlet 必须执行两项操作。

- 声明通过将 SupportsShouldProcess 关键字设置为 `true` 来指定[CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)属性时，cmdlet 支持确认。

- 在执行 Cmdlet 的过程中，请调用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) （如以下示例中所示）。

通过支持确认，cmdlet 将公开 Windows PowerShell 提供的 `Confirm` 和 `WhatIf` 参数，同时满足 cmdlet 的开发准则（有关 cmdlet 开发指南的详细信息，请参阅[cmdlet开发指南](./cmdlet-development-guidelines.md)。）

## <a name="changing-the-system"></a>更改系统

"更改系统" 的作用是指任何可能更改 Windows PowerShell 外部系统状态的 cmdlet。 例如，停止进程、启用或禁用用户帐户，或者向数据库表添加行都是对系统进行的所有更改。 与此相反，读取数据或建立暂时性连接的操作不会更改系统，通常不需要确认。 对于其效果限制在 Windows PowerShell 运行时内的操作（如 `set-variable`），也不需要确认。 可能或可能不会进行永久更改的 cmdlet 应该仅在要进行持久更改时才声明 `SupportsShouldProcess` 和[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 。

> [!NOTE]
> ShouldProcess 确认仅适用于 cmdlet。 如果命令或脚本通过直接调用 .NET 方法或属性，或在 Windows PowerShell 外部调用应用程序来修改系统的运行状态，则这种形式的确认将不可用。

## <a name="the-stopproc-cmdlet"></a>StopProc Cmdlet

本主题介绍了一种停止过程 cmdlet，该 cmdlet 尝试使用 Get-help cmdlet （在[创建第一个 cmdlet](./creating-a-cmdlet-without-parameters.md)时介绍）来停止检索的进程。

## <a name="defining-the-cmdlet"></a>定义 Cmdlet

创建 cmdlet 的第一步是始终命名 cmdlet 并声明实现 cmdlet 的 .NET 类。 因为你要编写一个 cmdlet 来更改系统，所以应该相应地对其进行命名。 此 cmdlet 将停止系统进程，因此在此处选择的谓词名称为 "Stop"，由[Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)类定义，名词 "Proc" 指示该 cmdlet 停止进程。 有关批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 谓词名称](./approved-verbs-for-windows-powershell-commands.md)。

下面是此 Stop Proc cmdlet 的类定义。

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

请注意，在[CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)声明中，`SupportsShouldProcess` attribute 关键字设置为 "`true`，以使该 cmdlet 可以调用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ，并[将调用"ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)"。 如果未设置此关键字，则用户将无法使用 `Confirm` 和 `WhatIf` 参数。

### <a name="extremely-destructive-actions"></a>极其破坏性操作

有些操作非常有破坏性，如重新格式化活动硬盘分区。 在这些情况下，cmdlet 应在声明[CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)属性时设置 `ConfirmImpact`  =  `ConfirmImpact.High`。 此设置强制 cmdlet 即使在用户未指定 `Confirm` 参数时也请求用户确认。 但是，cmdlet 开发人员应避免过度使用 `ConfirmImpact` 的操作，这些操作可能具有破坏性，如删除用户帐户。 请记住，如果 `ConfirmImpact` 设置为[ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**。

同样，某些操作不太可能是破坏性的，尽管它们在理论上是在 Windows PowerShell 之外修改系统的运行状态。 此类 cmdlet 可将 `ConfirmImpact` 设置为[Confirmimpact](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0)。 这会绕过确认请求，用户只要求确认影响和影响最大的操作。

## <a name="defining-parameters-for-system-modification"></a>定义系统修改的参数

本部分介绍如何定义 cmdlet 参数，包括支持系统修改所需的参数。 如果需要有关定义参数的常规信息，请参阅[添加处理命令行输入的参数](./adding-parameters-that-process-command-line-input.md)。

停止过程 cmdlet 定义三个参数： `Name`、`Force` 和 `PassThru`。

@No__t_0 参数对应于进程输入对象的 `Name` 属性。 请注意，此示例中的 `Name` 参数是必需的，因为如果没有要停止的命名进程，cmdlet 将失败。

@No__t_0 参数允许用户重写对[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)的调用。） 事实上，调用 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 的任何 cmdlet 都应具有一个 `Force` 参数，以便在指定 `Force` 时，该 cmdlet 将跳过对 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 的调用。 继续执行该操作。 请注意，这不会影响对[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)的调用。

@No__t_0 参数允许用户指示 cmdlet 是否通过管道传递输出对象，在这种情况下，进程停止后。 请注意，此参数绑定到 cmdlet 本身，而不是绑定到输入对象的属性。

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

该 cmdlet 必须重写输入处理方法。 下面的代码演示了示例 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Cmdlet 中使用的重写。 对于每个请求的进程名称，此方法可确保该进程不是一个特殊的进程，尝试停止该进程，然后发送一个输出对象（如果指定了 `PassThru` 参数）。

```csharp
protected override void ProcessRecord()
{
  foreach (string name in processNames)
  {
    // For every process name passed to the cmdlet, get the associated
    // process(es). For failures, write a non-terminating error
    Process[] processes;

    try
    {
      processes = Process.GetProcessesByName(name);
    }
    catch (InvalidOperationException ioe)
    {
      WriteError(new ErrorRecord(ioe,"Unable to access the target process by name",
                 ErrorCategory.InvalidOperation, name));
      continue;
    }

    // Try to stop the process(es) that have been retrieved for a name
    foreach (Process process in processes)
    {
      string processName;

      try
      {
        processName = process.ProcessName;
      }

      catch (Win32Exception e)
        {
          WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                     ErrorCategory.ReadError, process));
          continue;
        }

        // Call Should Process to confirm the operation first.
        // This is always false if WhatIf is set.
        if (!ShouldProcess(string.Format("{0} ({1})", processName,
                           process.Id)))
        {
          continue;
        }
        // Call ShouldContinue to make sure the user really does want
        // to stop a critical process that could possibly stop the computer.
        bool criticalProcess =
             criticalProcessNames.Contains(processName.ToLower());

        if (criticalProcess &&!force)
        {
          string message = String.Format
                ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                processName);

          // It is possible that ProcessRecord is called multiple times
          // when the Name parameter receives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across multiple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
        } // if (criticalProcess...
        // Stop the named process.
        try
        {
          process.Kill();
        }
        catch (Exception e)
        {
          if ((e is Win32Exception) || (e is SystemException) ||
              (e is InvalidOperationException))
          {
            // This process could not be stopped so write
            // a non-terminating error.
            string message = String.Format("{0} {1} {2}",
                             "Could not stop process \"", processName,
                             "\".");
            WriteError(new ErrorRecord(e, message,
                       ErrorCategory.CloseError, process));
                       continue;
          } // if ((e is...
          else throw;
        } // catch

        // If the PassThru parameter argument is
        // True, pass the terminated process on.
        if (passThru)
        {
          WriteObject(process);
        }
    } // foreach (Process...
  } // foreach (string...
} // ProcessRecord
```

## <a name="calling-the-shouldprocess-method"></a>调用 ShouldProcess 方法

Cmdlet 的输入处理方法应调用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，以确认在更改之前（例如，删除文件）对系统运行状态进行的操作的执行操作是否正常。 这允许 Windows PowerShell 运行时在 shell 内提供正确的 "WhatIf" 和 "Confirm" 行为。

> [!NOTE]
> 如果某个 cmdlet 指出它支持的操作应该处理并无法进行[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用，则用户可能会意外地修改系统。

对[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)的调用将向用户发送要更改的资源的名称，Windows PowerShell 运行时在确定哪些内容行设置或首选项变量的作用应显示给用户。

下面的示例演示了如何调用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ，以便从示例停止过程 Cmdlet 中的[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的重写中调用该方法的调用。

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a>调用 ShouldContinue 方法

对[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法的调用会向用户发送一条辅助消息。 如果 `Force` 参数未设置为 `true`，则在对 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 的调用 `true` 返回后，就会调用 。 然后，用户可以提供反馈来指出是否应继续操作。 你的 cmdlet 会调用[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)作为额外的检查，以查看是否存在潜在的危险系统修改，或者你希望为用户提供 "全部" 和 "无" 选项。

下面的示例演示了如何调用[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) ，以便从示例停止过程 Cmdlet 中的[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的重写中调用该方法的调用。

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter receives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across multiple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (criticalProcess...
```

## <a name="stopping-input-processing"></a>正在停止输入处理

进行系统修改的 cmdlet 的输入处理方法必须提供一种方法来停止处理输入。 对于这种停止过程 cmdlet，将从[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法发出到 system.exception [*](/dotnet/api/System.Diagnostics.Process.Kill)方法的调用。 "..." 的方法是。 由于将 `PassThru` 参数设置为 `true`，因此 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 还会调用 [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)，以将进程对象发送到管道中的对象。

## <a name="code-sample"></a>代码示例

有关完整C#的示例代码，请参阅[StopProcessSample01 示例](./stopprocesssample01-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定义对象类型和格式设置

Windows PowerShell 使用 .Net 对象在 cmdlet 之间传递信息。 因此，cmdlet 可能需要定义自己的类型，或者该 cmdlet 可能需要扩展另一个 cmdlet 提供的现有类型。 有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式](/previous-versions//ms714665(v=vs.85))。

## <a name="building-the-cmdlet"></a>构建 Cmdlet

实现 cmdlet 后，必须通过 Windows PowerShell 管理单元向 Windows PowerShell 注册它。 有关注册 cmdlet 的详细信息，请参阅[如何注册 cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))。

## <a name="testing-the-cmdlet"></a>测试 Cmdlet

向 Windows PowerShell 注册 cmdlet 后，可以通过在命令行上运行 cmdlet 来对其进行测试。 下面是测试停止过程 cmdlet 的几个测试。 有关从命令行使用 cmdlet 的详细信息，请参阅[使用 Windows PowerShell 的入门](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

- 启动 Windows PowerShell 并使用 Stop Proc cmdlet 停止处理，如下所示。 由于该 cmdlet 将 `Name` 参数指定为必需，因此该 cmdlet 会查询参数。

    ```powershell
    PS> stop-proc
    ```

此时将显示以下输出。

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- 现在，让我们使用 cmdlet 来停止名为 "NOTEPAD" 的进程。 Cmdlet 会要求你确认操作。

    ```powershell
    PS> stop-proc -Name notepad
    ```

此时将显示以下输出。

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- 使用所示的停止进程来停止名为 "WINLOGON" 的关键进程。 系统将提示您执行此操作，并向您发出警告，因为这会导致操作系统重启。

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

此时将显示以下输出。

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- 现在，让我们尝试停止 WINLOGON 进程，而不会收到警告。 请注意，此命令项使用 `Force` 参数来覆盖该警告。

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

此时将显示以下输出。

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>另请参阅

[添加用于处理命令行输入的参数](./adding-parameters-that-process-command-line-input.md)

[扩展对象类型和格式](/previous-versions//ms714665(v=vs.85))

[如何注册 Cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Cmdlet 示例](./cmdlet-samples.md)