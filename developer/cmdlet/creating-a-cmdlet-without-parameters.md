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
ms.openlocfilehash: 75a45e539b45b50714951f2b992d9ecf69de4664
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860643"
---
# <a name="creating-a-cmdlet-without-parameters"></a>创建不具有参数的 Cmdlet

本部分介绍如何创建从本地计算机而不使用参数，检索的信息，然后将信息写入管道的 cmdlet。 此处所述的 cmdlet 是检索本地计算机的进程的信息，然后在命令行中显示该信息的 Get-proc cmdlet。

在本部分中的主题包括：

- [命名该 Cmdlet](#Naming-the-Cmdlet)

- [定义在 Cmdlet 类](#Defining-the-Cmdlet-Class)

- [重写方法的处理的输入](#Overriding-an-Input-Processing-Method)

- [代码示例](#Code-Sample)

- [定义对象类型和格式设置](#Defining-Object-Types-and-Formatting)

- [生成该 Cmdlet](#Building-the-Cmdlet)

- [测试 Cmdlet](#Testing-the-Cmdlet)

> [!NOTE]
> 请注意，在编写 cmdlet，Windows PowerShell® 引用程序集下载到磁盘上 （通过默认位于 C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0）。它们不被安装在全局程序集缓存 (GAC) 中。

## <a name="naming-the-cmdlet"></a>命名该 Cmdlet

Cmdlet 名称由指示将该 cmdlet 的操作动词和名词，该值指示该 cmdlet 作用于的项组成。 由于此示例 Get-proc cmdlet 检索进程对象，它使用谓词"Get"，定义[System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon)枚举和名词"Proc"以指示该 cmdlet 适用于进程的项。

当命名 cmdlet 时，请不要使用任何以下字符: #，（） {} [] &-/ \ $;:"<> &#124; ？ @ ` .

### <a name="choosing-a-noun"></a>选择某个名词

应选择特定的名词。 最好使用单数形式的名词前缀为产品名称的缩写形式。 此类型的示例 cmdlet 名称是"`Get-SQLServer`"。

### <a name="choosing-a-verb"></a>选择谓词

应使用已批准的 cmdlet 的动词名称的集中的谓词。 有关已批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 的动词名称](./approved-verbs-for-windows-powershell-commands.md)。

## <a name="defining-the-cmdlet-class"></a>定义在 Cmdlet 类

一旦您选择了 cmdlet 名称，定义一个.NET 类来实现该 cmdlet。 下面是此示例 Get-proc cmdlet 类定义：

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

请注意，上一步类定义中， [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute)属性，使用语法`[Cmdlet(verb, noun, ...)]`，用于标识此类作为一个 cmdlet。 这是唯一的必需的属性为所有的 cmdlet，并允许 Windows PowerShell 运行时，若要正确地调用它们。 可以设置属性关键字，以进一步声明类，如有必要。 请注意，我们的示例 GetProcCommand 类的特性声明声明了仅 Get-proc cmdlet 的名词和动词名称。

> [!NOTE]
> 对于所有 Windows PowerShell 属性类，可以设置的关键字对应于特性类的属性。

命名该 cmdlet 的类，很好的做法，以反映类名称中的 cmdlet 名称。 若要执行此操作，使用窗体"VerbNounCommand"，并替换动词和名词的 cmdlet 名称中使用"谓词"和"名词"。 示例 Get-proc cmdlet 以前的类定义中所示，定义一个名为 GetProcCommand，派生自类[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)基类。

> [!IMPORTANT]
> 如果你想要定义一个 cmdlet，直接访问 Windows PowerShell 运行时，.NET 类应派生自[System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基类。 有关此类的详细信息，请参阅[创建该定义的参数集的一个 Cmdlet](./adding-parameter-sets-to-a-cmdlet.md)。

> [!NOTE]
> Cmdlet 类必须显式标记为公共。 未标记为公共的类将默认为内部和 Windows PowerShell 运行时将不会找到。

使用 Windows PowerShell [Microsoft.Powershell.Commands](/dotnet/api/Microsoft.PowerShell.Commands)其 cmdlet 类的命名空间。 建议将 cmdlet 类放置在你的 API 命名空间，例如，xxx.PS.Commands 命令命名空间。

## <a name="overriding-an-input-processing-method"></a>重写方法的处理的输入

[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)类提供了三个主要的输入的处理方法，你的 cmdlet 必须在至少一个替代。 有关 Windows PowerShell 如何处理记录的详细信息，请参阅[Windows PowerShell 的工作原理](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)。

对于所有类型的输入，Windows PowerShell 运行时调用[System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)启用处理。 如果你的 cmdlet 必须执行一些预处理或安装程序，它可以执行此操作通过重写此方法。

> [!NOTE]
> Windows PowerShell 使用术语"记录"来描述调用 cmdlet 时提供的参数值的组。

如果你的 cmdlet 接受管道输入，则必须重写[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，并选择性地[System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。 例如，一个 cmdlet 可能会替代这两种方法，如果收集使用的所有输入[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) ，然后输入作为一个整体，而不是一个元素一次，作为运行`Sort-Object`cmdlet 的用途。

如果你的 cmdlet 不接受管道输入，应重写[System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。 注意： 此方法经常用来代替到[System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)时该 cmdlet 不能作用于一个元素一次排序 cmdlet 的情况一样。

此示例 Get-proc cmdlet 必须接收管道输入，因为它将替代[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法，并使用的默认实现[System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)并[System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)。 [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)替代检索进程，并将其写入到命令行中使用[System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。

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

#### <a name="things-to-remember-about-input-processing"></a>要记住有关输入处理的事项

- 输入的默认源是由命令行上的用户提供一个显式对象 （例如，字符串）。 有关详细信息，请参阅[创建进程命令行输入到 Cmdlet](./adding-parameters-that-process-command-line-input.md)。

- 输入处理方法，还可以从在管道上的上游 cmdlet 的输出对象接收输入。 有关详细信息，请参阅[创建到进程管道输入 Cmdlet](./adding-parameters-that-process-pipeline-input.md)。 请注意 cmdlet 可以接收来自命令行组成的输入和管道源。

- 对于较长时间，或根本不可能不会返回下游 cmdlet。 因此，处理您的 cmdlet 中的方法的输入应不持有的锁期间调用到[System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)，尤其是为其范围超出 cmdlet 实例的锁。

> [!IMPORTANT]
> Cmdlet 应永远不会调用[System.Console.Writeline*](/dotnet/api/System.Console.WriteLine)或其等效项。

- Cmdlet 可能具有对象变量来完成后清理处理 (例如，如果该表已打开的文件句柄[System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法，并保留句柄打开供使用[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord))。 务必要记住 Windows PowerShell 运行时不会始终调用[System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法，应执行对象清理。

例如， [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)如果正中取消该 cmdlet，或者如果终止该 cmdlet 的任何部分中会发生错误可能不会调用。 因此，需要对象清理 cmdlet 应实现的完整[System.Idisposable](/dotnet/api/System.IDisposable)模式，以便在运行时可以调用都包括终结器， [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)并[System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose)处理结束时。

## <a name="code-sample"></a>代码示例

有关完整C#示例代码，请参阅[GetProcessSample01 Sample](./getprocesssample01-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定义对象类型和格式设置

Windows PowerShell cmdlet 使用.NET 对象之间传递信息。 因此，一个 cmdlet 可能需要定义其自己的类型，或者该 cmdlet 可能需要扩展现有类型提供的另一个 cmdlet。 有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式设置](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。

## <a name="building-the-cmdlet"></a>生成该 Cmdlet

实现一个 cmdlet 之后, 您必须注册它使用 Windows PowerShell 通过 Windows PowerShell 管理单元。 有关注册 cmdlet 的详细信息，请参阅[如何注册 Cmdlet、 提供商和主机应用程序](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-cmdlet"></a>测试 Cmdlet

当已使用 Windows PowerShell 注册你的 cmdlet 时，可以通过运行命令行上测试它。 我们示例 Get-proc cmdlet 的代码较小，但它仍使用 Windows PowerShell 运行时和现有的.NET 对象，就足以使其发挥作用。 让我们测试，以更好地了解 Get-proc 可以执行的操作以及可以如何使用其输出。 有关使用命令行中的 cmdlet 的详细信息，请参阅[Windows PowerShell 入门学习](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

1. 启动 Windows PowerShell，并获取当前进程在计算机上运行。

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

2. 将一个变量分配给 cmdlet 结果以便于操作。

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

4. 检索特定的进程。

    ```powershell
    $p[6]
    ```

    将显示以下输出。

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. 获取此进程的开始时间。

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

6. 获取进程的句柄计数大于 500，并对结果进行排序。

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

7. 使用`Get-Member`cmdlet 可列出可用于每个进程的属性。

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

[创建用于处理命令行输入的 Cmdlet](./adding-parameters-that-process-command-line-input.md)

[创建用于处理管道输入的 Cmdlet](./adding-parameters-that-process-pipeline-input.md)

[如何创建 Windows PowerShell Cmdlet](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[扩展对象类型和格式设置](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Windows PowerShell 的工作原理](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[如何注册 Cmdlet、 提供程序，和托管应用程序](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell 参考](../windows-powershell-reference.md)

[Cmdlet 示例](./cmdlet-samples.md)