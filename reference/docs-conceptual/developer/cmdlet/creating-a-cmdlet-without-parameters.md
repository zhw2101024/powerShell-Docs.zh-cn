---
title: 创建不带参数的 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: af41c2c9855310d047404114a07b27180a7aa8fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74415670"
---
# <a name="creating-a-cmdlet-without-parameters"></a>创建不具有参数的 Cmdlet

本部分介绍如何创建一个 cmdlet，用于在不使用参数的情况下从本地计算机检索信息，然后将该信息写入管道。 此处所述的 cmdlet 是一个用于检索有关本地计算机的进程的信息，然后在命令行中显示该信息的 Get Proc cmdlet。

> [!NOTE]
> 请注意，在编写 cmdlet 时，Windows PowerShell®引用程序集会下载到磁盘上（默认情况下，C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0）。 它们未安装在全局程序集缓存（GAC）中。

## <a name="naming-the-cmdlet"></a>命名 Cmdlet

Cmdlet 名称由指示 cmdlet 所采用的操作的谓词和指示该 cmdlet 操作的项的名词组成。 由于此示例处理程序 cmdlet 可检索进程对象，因此它使用由[Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon)枚举定义的谓词 "Get"，并使用名词 "Proc" 指示该 cmdlet 处理进程项。

命名 cmdlet 时，请不要使用以下任何字符： #、（） {} [] &-/\ $;： "" < > &#124; ？ @ ` .

### <a name="choosing-a-noun"></a>选择名词

应选择特定的名词。 最好使用带有缩写形式的产品名称的单数名词。 此类型的示例 cmdlet 名称为 "`Get-SQLServer`"。

### <a name="choosing-a-verb"></a>选择谓词

应使用已批准的 cmdlet 动词名称集中的动词。 有关批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 谓词名称](./approved-verbs-for-windows-powershell-commands.md)。

## <a name="defining-the-cmdlet-class"></a>定义 Cmdlet 类

选择了 cmdlet 名称后，定义一个 .NET 类来实现该 cmdlet。 下面是此示例的 Get Proc cmdlet 的类定义：

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

请注意，在类定义之前， [CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)属性（带有语法 `[Cmdlet(verb, noun, ...)]`）用于将此类标识为 cmdlet。 这是所有 cmdlet 的唯一必需的属性，它允许 Windows PowerShell 运行时正确调用它们。 如有必要，可以设置属性关键字以进一步声明该类。 请注意，我们的示例 GetProcCommand 类的属性声明仅声明了 Get-help cmdlet 的名词和动词名称。

> [!NOTE]
> 对于所有 Windows PowerShell 特性类，可以设置的关键字与特性类的属性相对应。

命名 cmdlet 的类时，最好在类名称中反映 cmdlet 名称。 为此，请使用格式 "VerbNounCommand"，并将 "Verb" 和 "名词" 替换为 cmdlet 名称中使用的动词和名词。 如前一类定义中所示，示例获取处理器 cmdlet 定义了一个名为[GetProcCommand 的类](/dotnet/api/System.Management.Automation.Cmdlet)，该类派生自一个

> [!IMPORTANT]
> 如果要定义直接访问 Windows PowerShell 运行时的 cmdlet，你的 .NET 类应派生自[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基类。 有关此类的详细信息，请参阅[创建定义参数集的 Cmdlet](./adding-parameter-sets-to-a-cmdlet.md)。

> [!NOTE]
> Cmdlet 的类必须显式标记为公共。 未标记为 "公共" 的类将默认为内部类，且不会由 Windows PowerShell 运行时找到。

Windows PowerShell 使用其 cmdlet 类[的 "the](/dotnet/api/Microsoft.PowerShell.Commands) " 命名空间。 建议将 cmdlet 类放在 API 命名空间的命令命名空间中，例如，xxx。

## <a name="overriding-an-input-processing-method"></a>重写输入处理方法

[System.web](/dotnet/api/System.Management.Automation.Cmdlet)类提供三个主要的输入处理方法，其中至少有一个 Cmdlet 必须重写。 有关 Windows PowerShell 如何处理记录的详细信息，请参阅[Windows powershell 的工作](/previous-versions//ms714658(v=vs.85))原理。

对于所有类型的输入，Windows PowerShell 运行时都会调用[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)来启用处理。 如果 cmdlet 必须执行一些预处理或设置，则可以通过重写此方法来执行此操作。

> [!NOTE]
> Windows PowerShell 使用术语 "记录" 来描述在调用 cmdlet 时提供的参数值集。

如果你的 cmdlet 接受管道输入，则它必须重写[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，还可以重[写方法（可选）。](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 例如，如果 cmdlet 收集所有使用 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 的输入，则它可能会重写这两种方法，然后一次对输入（而不是一个元素）进行操作，因为 `Sort-Object` cmdlet 执行。

如果 cmdlet 不接受管道输入，则它应重写[system.web](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。 请注意，当 cmdlet 无法一次对一个元素进行操作时，此方法经常用于替代[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) ，这与排序 Cmdlet 的情况相同。

由于此示例中的ProcessRecord cmdlet 必须接收管道输入，因此它将重写 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 方法，并使用默认的[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 和 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 实现方法。 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)重写将检索进程，并使用[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法将这些进程写入命令行的命令行中。

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a>有关输入处理的注意事项

- 输入的默认源是用户在命令行上提供的显式对象（例如，字符串）。 有关详细信息，请参阅[创建 Cmdlet 来处理命令行输入](./adding-parameters-that-process-command-line-input.md)。

- 输入处理方法还可以从管道上的上游 cmdlet 的输出对象接收输入。 有关详细信息，请参阅[创建用于处理管道输入的 Cmdlet](./adding-parameters-that-process-pipeline-input.md)。 请注意，cmdlet 可以从命令行和管道源的组合接收输入。

- 下游 cmdlet 可能不会长时间返回，或者根本不会返回。 出于此原因，在调用[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)期间，cmdlet 中的输入处理方法不应持有锁，尤其是范围超出 cmdlet 实例的锁。

> [!IMPORTANT]
> Cmdlet 不应调用 system.exception [*](/dotnet/api/System.Console.WriteLine)或其等效的。

- Cmdlet 在处理完成后可能会有要清理的对象变量（例如，如果它打开[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法中的文件句柄，并使该句柄处于打开状态以供[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)使用）。 请记住，Windows PowerShell 运行时并不总是调用应执行对象清理的[system.web](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法，这一点很重要。

例如，如果 cmdlet 在中间取消或在 cmdlet 的任何部分中出现终止错误，则可能不会调用[system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 。 因此，需要对象清理的 cmdlet 应该实现完整的 [System.IDisposable](/dotnet/api/System.IDisposable) 模式（包括终结器），以便运行时可以调用 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 和 [System.IDisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) 处理结束时 IDisposable *。

## <a name="code-sample"></a>代码示例

有关完整C#的示例代码，请参阅[GetProcessSample01 示例](./getprocesssample01-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定义对象类型和格式设置

Windows PowerShell 使用 .NET 对象在 cmdlet 之间传递信息。 因此，cmdlet 可能需要定义自己的类型，或者该 cmdlet 可能需要扩展另一个 cmdlet 提供的现有类型。 有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式](/previous-versions//ms714665(v=vs.85))。

## <a name="building-the-cmdlet"></a>构建 Cmdlet

实现 cmdlet 后，必须通过 Windows PowerShell 管理单元将其注册到 Windows PowerShell。 有关注册 cmdlet 的详细信息，请参阅[如何注册 cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))。

## <a name="testing-the-cmdlet"></a>测试 Cmdlet

向 Windows PowerShell 注册 cmdlet 后，可以通过在命令行上运行 cmdlet 来对其进行测试。 示例处理器 cmdlet 的代码很小，但它仍使用 Windows PowerShell 运行时和现有的 .NET 对象，这足以使其变得非常有用。 让我们对它进行测试，以便更好地了解该过程的功能，以及如何使用其输出。 有关从命令行使用 cmdlet 的详细信息，请参阅[使用 Windows PowerShell 的入门](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

1. 启动 Windows PowerShell，并获取正在计算机上运行的当前进程。

    ```powershell
    get-proc
    ```

    将显示以下输出。

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. 将一个变量分配给 cmdlet 结果，以便更轻松地执行操作。

    ```powershell
    $p=get-proc
    ```

3. 获取进程数。

    ```powershell
    $p.length
    ```

    将显示以下输出。

    ```output
    63
    ```

4. 检索特定进程。

    ```powershell
    $p[6]
    ```

    将显示以下输出。

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. 获取此过程的开始时间。

    ```powershell
    $p[6].starttime
    ```

    将显示以下输出。

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. 获取句柄计数大于500的进程，并对结果进行排序。

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    将显示以下输出。

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. 使用 `Get-Member` cmdlet 列出可用于每个进程的属性。

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    将显示以下输出。

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a>另请参阅

[创建 Cmdlet 来处理命令行输入](./adding-parameters-that-process-command-line-input.md)

[创建用于处理管道输入的 Cmdlet](./adding-parameters-that-process-pipeline-input.md)

[如何创建 Windows PowerShell Cmdlet](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[扩展对象类型和格式](/previous-versions//ms714665(v=vs.85))

[Windows PowerShell 的工作原理](/previous-versions//ms714658(v=vs.85))

[如何注册 Cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell 参考](../windows-powershell-reference.md)

[Cmdlet 示例](./cmdlet-samples.md)
