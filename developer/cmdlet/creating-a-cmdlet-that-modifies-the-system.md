---
title: 创建一个 Cmdlet 来修改系统 |Microsoft Docs
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
ms.openlocfilehash: d93cc4a05a6625d073791c067d1e9b6662c3a565
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856333"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a>创建用于修改系统的 Cmdlet

有时 cmdlet 必须修改系统，而不仅仅是 Windows PowerShell 运行时的状态的运行状态。 在这些情况下，该 cmdlet 应允许用户确认要进行更改的机会。

若要支持确认 cmdlet 必须做两件事。

- 声明指定时，该 cmdlet，支持确认[System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute)通过将 SupportsShouldProcess 关键字设置为属性`true`。

- 调用[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) cmdlet （如下面的示例中所示） 执行的过程。

通过支持确认，cmdlet 公开`Confirm`和`WhatIf`参数提供的 Windows PowerShell，也满足 cmdlet 的开发准则 （有关 cmdlet 开发指导原则的详细信息，请参阅[Cmdlet 开发指导原则](./cmdlet-development-guidelines.md)。)。

## <a name="changing-the-system"></a>更改系统

"更改系统"的操作是指任何 cmdlet 的 Windows PowerShell 外部系统的状态可能会更改。 例如，正在停止过程，启用或禁用用户帐户，或添加到数据库表的行都应确认在系统的所有更改。 与此相反，读取数据或建立暂时性连接的操作不会更改系统，并且通常不需要确认。 其效果仅限于在 Windows PowerShell 运行时，如操作也不需要确认`set-variable`。 Cmdlet 可能会或可能不提供持续性的更改应声明`SupportsShouldProcess`，并调用[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)前提是这些要进行永久性更改。

> [!NOTE]
> ShouldProcess 确认仅适用于 cmdlet。 如果命令或脚本修改系统的运行状态，通过直接调用.NET 方法或属性，或者在 Windows PowerShell 之外调用应用程序，这种形式的确认将不可用。

## <a name="the-stopproc-cmdlet"></a>StopProc Cmdlet

本主题介绍停止使用 Get-proc cmdlet 检索的进程会尝试停止进程 cmdlet (中所述[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md))。

在本部分中的主题包括：

- [定义 Cmdlet](#Defining-the-Cmdlet)

- [系统修改为定义参数](#Defining-Parameters-for-System-Modification)

- [重写方法的处理的输入](#Overriding-an-Input-Processing-Method)

- [调用 ShouldProcess 方法](#Calling-the-ShouldProcess-Method)

- [调用 ShouldContinue 方法](#Calling-the-ShouldContinue-Method)

- [正在停止输入的处理](#Stopping-Input-Processing)

- [代码示例](#Code-Sample)

- [定义对象类型和格式设置](#Defining-Object-Types-and-Formatting)

- [生成该 Cmdlet](#Building-the-Cmdlet)

- [测试 Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>定义 Cmdlet

Cmdlet 创建的第一步是始终命名 cmdlet 和实现该 cmdlet 的.NET 类声明。 因为你正在编写 cmdlet 来更改的系统，应相应地命名。 此 cmdlet 停止系统进程，因此在此处选择谓词名称是"停止"，定义[System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)类，使用名词"Proc"以指示该 cmdlet 停止的进程。 有关已批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 的动词名称](./approved-verbs-for-windows-powershell-commands.md)。

下面是此停止进程 cmdlet 的类定义。

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

请注意，在[System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute)声明，`SupportsShouldProcess`属性关键字设置为`true`若要启用 cmdlet 来调用[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)并[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)。 如果不设置此关键字，`Confirm`和`WhatIf`参数将不向用户提供。

### <a name="extremely-destructive-actions"></a>极具破坏性操作

某些操作是极具破坏性，如重新格式化活动硬盘分区。 在这些情况下，该 cmdlet 应设置`ConfirmImpact`  =  `ConfirmImpact.High`声明时[System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute)属性。 此设置为请求用户确认强制 cmdlet，即使用户未指定`Confirm`参数。 但是，cmdlet 开发人员应避免过度使用`ConfirmImpact`是只具有潜在破坏性，如删除用户帐户的操作。 请记住，如果`ConfirmImpact`设置为[System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High)。

同样，某些操作不太可能会破坏性，尽管它们在理论上修改 Windows PowerShell 外部系统的运行状态。 此类 cmdlet 可以设置`ConfirmImpact`到[System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0)。 这将绕过其中已要求用户确认仅中影响和影响较大的操作的确认请求。

## <a name="defining-parameters-for-system-modification"></a>系统修改为定义参数

本部分介绍如何定义 cmdlet 参数，包括所需的支持系统修改。 请参阅[添加该进程的命令行输入的参数](./adding-parameters-that-process-command-line-input.md)如果需要有关如何定义参数的常规信息。

停止进程 cmdlet 定义了三个参数： `Name`， `Force`，和`PassThru`。

`Name`参数对应于`Name`过程输入对象的属性。 请注意，`Name`在此示例中的参数是必需的因为如果它不具有已命名的进程停止，该 cmdlet 将会失败。

`Force`参数允许用户重写调用[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)。 事实上，用于调用的任何 cmdlet [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)应具有`Force`参数，以便当`Force`指定，则该 cmdlet 将跳过调用[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)和继续执行该操作。 请注意这不会对的调用会影响[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)。

`PassThru`参数允许用户指示是否 cmdlet 将传递给输出对象通过管道，在这种情况下后一个进程已停止。 请注意此参数绑定到该 cmdlet 本身而不是属性的输入对象。

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

该 cmdlet 必须重写方法的处理的输入。 下面的代码演示[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)示例停止进程 cmdlet 中使用的重写。 对于每个请求的进程名称，此方法可确保该过程不是一个特殊的过程、 尝试停止的进程，以及然后将输出对象发送如果`PassThru`指定参数。

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
          // when the Name parameter reveives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across mutilple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
        } // if (cricicalProcess...
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

输入处理的 cmdlet 的方法应调用[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法以确定执行操作之前对运行进行更改 （例如，删除文件）系统状态。 这允许 Windows PowerShell 运行时提供在 shell 中的正确"WhatIf"和"确认"行为。

> [!NOTE]
> 如果 cmdlet 表明它支持应处理和无法做出[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)调用时，用户可能意外修改系统。

在调用[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)发送要更改对用户来说，与 Windows PowerShell 运行时将考虑在内的任何命令行设置或首选项变量的资源的名称在确定向用户应显示的内容。

下面的示例演示在调用[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)重写[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)中的方法示例停止进程 cmdlet。

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a>调用 ShouldContinue 方法

在调用[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法将辅助消息发送到用户。 在调用后进行此调用[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)返回`true`; 如果`Force`参数未设置为`true`。 用户可以提供反馈以说是否应继续执行该操作。 Cmdlet 调用[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)作为额外检查潜在的危险系统修改或如果想要向用户提供是全部和否全部选项。

下面的示例演示在调用[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)重写[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)中的方法示例停止进程 cmdlet。

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter reveives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across mutilple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (cricicalProcess...
```

## <a name="stopping-input-processing"></a>正在停止输入的处理

处理方法，使系统修改某个 cmdlet 的输入必须提供一种方法停止输入的处理。 在此停止进程 cmdlet 的情况下调用了从[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法[System.Diagnostics.Process.Kill*](/dotnet/api/System.Diagnostics.Process.Kill)方法。 因为`PassThru`参数设置为`true`， [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)还会调用[System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)到将进程对象发送到管道。

## <a name="code-sample"></a>代码示例

有关完整C#示例代码，请参阅[StopProcessSample01 示例](./stopprocesssample01-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定义对象类型和格式设置

Windows PowerShell cmdlet 使用.Net 对象之间传递信息。 因此，一个 cmdlet 可能需要定义其自己的类型，或者该 cmdlet 可能需要扩展现有类型提供的另一个 cmdlet。 有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式设置](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。

## <a name="building-the-cmdlet"></a>生成该 Cmdlet

执行后一个 cmdlet，它必须向注册 Windows PowerShell 通过 Windows PowerShell 管理单元。 有关注册 cmdlet 的详细信息，请参阅[如何注册 Cmdlet、 提供商和主机应用程序](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-cmdlet"></a>测试 Cmdlet

当已使用 Windows PowerShell 注册你的 cmdlet 时，可以通过运行命令行上测试它。 以下是测试停止进程 cmdlet 的多个测试。 有关使用命令行中的 cmdlet 的详细信息，请参阅[Windows PowerShell 入门学习](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

- 启动 Windows PowerShell 并停止进程 cmdlet 用于停止处理，如下所示。 因为该 cmdlet 指定`Name`为必需参数，该参数的 cmdlet 查询。

    ```powershell
    PS> stop-proc
    ```

将显示以下输出。

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- 现在让我们使用该 cmdlet 停止名为"NOTEPAD"的过程。 该 cmdlet 会要求您确认该操作。

    ```powershell
    PS> stop-proc -Name notepad
    ```

将显示以下输出。

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- 使用停止的进程所示停止名为"WINLOGON"关键进程。 您是系统提示，警告您执行此操作，因为这将导致操作系统重新启动。

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

将显示以下输出。

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- 让我们现在尝试停止 WINLOGON 进程，而不会收到一条警告。 请注意，此命令项使用`Force`参数来重写该警告。

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

将显示以下输出。

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>另请参阅

[添加处理命令行输入的参数](./adding-parameters-that-process-command-line-input.md)

[扩展对象类型和格式设置](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[如何注册 Cmdlet、 提供程序，和托管应用程序](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Cmdlet 示例](./cmdlet-samples.md)