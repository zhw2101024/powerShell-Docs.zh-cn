---
title: 向 Cmdlet 添加非终止错误报告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: a4426abec96cd922360aeef8c157b4e9f41a15b9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364606"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a>向 Cmdlet 添加非终止错误报告

Cmdlet 可以通过调用["WriteError"。][]方法来报告非终止错误，并继续对当前输入对象或更多传入管道对象执行操作。
本部分介绍如何创建一个 cmdlet，该 cmdlet 报告来自其输入处理方法的非终止错误。

对于非终止错误（以及终止错误），该 cmdlet 必须通过标识错误的[System.web. ErrorRecord][]对象。
每个错误记录均由名为 "错误标识符" 的唯一字符串标识。
除了标识符以外，每个错误的类别都由[System.web. ErrorCategory][]枚举定义的常量指定。
用户可以通过将 `$ErrorView` 变量设置为 "CategoryView" 来基于其类别查看错误。

有关错误记录的详细信息，请参阅[Windows PowerShell 错误记录](./windows-powershell-error-records.md)。

## <a name="defining-the-cmdlet"></a>定义 Cmdlet

创建 cmdlet 的第一步是始终命名 cmdlet 并声明实现 cmdlet 的 .NET 类。
此 cmdlet 检索进程信息，因此此处选择的谓词名称为 "Get"。
（几乎任何能够检索信息的 cmdlet 都可以处理命令行输入。）有关批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 谓词名称](approved-verbs-for-windows-powershell-commands.md)。

下面是此获取过程 cmdlet 的定义。
[创建第一个 Cmdlet](creating-a-cmdlet-without-parameters.md)中提供了此定义的详细信息。

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-parameters"></a>定义参数

如果需要，cmdlet 必须定义用于处理输入的参数。
此获取处理器 cmdlet 定义一个**Name**参数[，如添加处理命令行输入的参数](adding-parameters-that-process-command-line-input.md)中所述。

下面是此 Get-help cmdlet 的**Name**参数的参数声明。

```csharp
[Parameter(
           Position = 0,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
[ValidateNotNullOrEmpty]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

## <a name="overriding-input-processing-methods"></a>重写输入处理方法

所有 cmdlet 必须重写由[System.object。][]类提供的输入处理方法中的至少一个。
这些方法在[创建第一个 Cmdlet](creating-a-cmdlet-without-parameters.md)中进行了介绍。

> [!NOTE]
> 你的 cmdlet 应尽可能独立地处理每条记录。

此 Get-Proc cmdlet 将重写["ProcessRecord"。][]方法，以处理用户或脚本提供的输入的 **Name** 参数的名称。
如果未提供任何名称，则此方法将获取每个请求的进程名称或所有进程的进程。
[创建第一个 Cmdlet](creating-a-cmdlet-without-parameters.md)时提供了此替代的详细信息。

### <a name="things-to-remember-when-reporting-errors"></a>报告错误时要记住的问题

在写入错误时 cmdlet 传递的[System.web. ErrorRecord][]对象在其核心处需要异常。
确定要使用的异常时，请遵循 .NET 指导原则。
基本上，如果错误与现有异常在语义上相同，则该 cmdlet 应使用或派生自该异常。
否则，它应直接从[System.Exception][]新的异常或异常层次结构。

创建错误标识符（通过 ErrorRecord 类的 FullyQualifiedErrorId 属性访问）时，请记住以下事项。

- 使用针对诊断目的的字符串，以便在检查完全限定的标识符时，可以确定错误是什么，以及错误来自何处。

- 格式正确的完全限定的错误标识符可能如下所示。

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand`

请注意，在前面的示例中，错误标识符（第一个标记）指定了错误的含义，剩余部分指示错误来自何处。

- 对于更复杂的方案，错误标识符可以是可以在检查时进行分析的以句点分隔的标记。
  这允许你过于按错误标识符的部分以及错误标识符和错误类别进行分支。

该 cmdlet 应将特定的错误标识符分配给不同的代码路径。
请记住以下信息以分配错误标识符：

- 错误标识符在整个 cmdlet 生命周期中应保持不变。
  不要更改 cmdlet 版本之间的错误标识符的语义。

- 使用文本作为 tersely 与所报告错误相对应的错误标识符。
  不要使用空格或标点。

- 让 cmdlet 仅生成可重现的错误标识符。
  例如，它不应生成包含进程标识符的标识符。
  仅当用户与遇到相同问题的其他用户所见的标识符对应时，错误标识符才适用于用户。

未处理的异常在以下情况下不会被 PowerShell 捕获：

- 如果 cmdlet 创建新线程，并且在该线程中运行的代码引发了未经处理的异常，则 PowerShell 将不会捕获该错误，将终止该进程。

- 如果对象在其析构函数或 Dispose 方法中包含导致未经处理的异常的代码，则 PowerShell 将不会捕获该错误，将终止该进程。

## <a name="reporting-nonterminating-errors"></a>报告非终止错误

输入处理方法中的任何一种都可以使用["WriteError"。][]方法将非终止错误报告给输出流。

下面是来自此 WriteError cmdlet 的代码示例，该代码示例演示了如何从["ProcessRecord"。][]方法的重写中调用对["WriteError"。][] 的调用。
在这种情况下，如果 cmdlet 找不到指定进程标识符的进程，则调用。

```csharp
protected override void ProcessRecord()
{
  // If no name parameter passed to cmdlet, get all processes.
  if (processNames == null)
  {
    WriteObject(Process.GetProcesses(), true);
  }
    else
    {
      // If a name parameter is passed to cmdlet, get and write
      // the associated processes.
      // Write a nonterminating error for failure to retrieve
      // a process.
      foreach (string name in processNames)
      {
        Process[] processes;

        try
        {
          processes = Process.GetProcessesByName(name);
        }
        catch (InvalidOperationException ex)
        {
          WriteError(new ErrorRecord(
                     ex,
                     "NameNotFound",
                     ErrorCategory.InvalidOperation,
                     name));
          continue;
        }

        WriteObject(processes, true);
      } // foreach (...
    } // else
  }
```

### <a name="things-to-remember-about-writing-nonterminating-errors"></a>有关编写非终止错误的注意事项

对于非终止错误，cmdlet 必须为每个特定输入对象生成特定的错误标识符。

Cmdlet 经常需要修改非终止错误产生的 PowerShell 操作。
它可以通过定义 `ErrorAction` 和 `ErrorVariable` 参数来实现此目的。
如果定义 `ErrorAction` 参数，该 cmdlet 将提供用户选项[System.web. ActionPreference][]，还可以通过设置 `$ErrorActionPreference` 变量直接影响该操作。

该 cmdlet 可以使用 `ErrorVariable` 参数将非终止错误保存到变量，此参数不受 `ErrorAction`的设置影响。
可以通过将加号（+）添加到变量名前面来向现有错误变量追加失败。

## <a name="code-sample"></a>代码示例

有关完整C#的示例代码，请参阅[GetProcessSample04 示例](./getprocesssample04-sample.md)。

## <a name="define-object-types-and-formatting"></a>定义对象类型和格式设置

PowerShell 使用 .NET 对象在 cmdlet 之间传递信息。
因此，cmdlet 可能需要定义自己的类型，或者该 cmdlet 可能需要扩展另一个 cmdlet 提供的现有类型。
有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。

## <a name="building-the-cmdlet"></a>构建 Cmdlet

实现 cmdlet 后，必须通过 Windows PowerShell 管理单元将其注册到 Windows PowerShell。
有关注册 cmdlet 的详细信息，请参阅[如何注册 cmdlet、提供程序和主机应用程序](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-cmdlet"></a>测试 Cmdlet

向 PowerShell 注册 cmdlet 后，可以通过在命令行上运行 cmdlet 来对其进行测试。
让我们测试该示例的 Get Proc cmdlet，以查看它是否报告错误：

- 启动 PowerShell，并使用 Get-help cmdlet 检索名为 "TEST" 的进程。

    ```powershell
    PS> get-proc -name test
    ```

将显示以下输出。

    ```
    get-proc : Operation is not valid due to the current state of the object.
    At line:1 char:9
    + get-proc  <<<< -name test
    ```

## <a name="see-also"></a>另请参阅

[添加处理管道输入的参数](./adding-parameters-that-process-pipeline-input.md)

[添加用于处理命令行输入的参数](./adding-parameters-that-process-command-line-input.md)

[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md)

[扩展对象类型和格式](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[如何注册 Cmdlet、提供程序和主机应用程序](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell 参考](../windows-powershell-reference.md)

[Cmdlet 示例](./cmdlet-samples.md)

[System.Exception]: /dotnet/api/System.Exception
[System.web. ActionPreference]: /dotnet/api/System.Management.Automation.ActionPreference
["ProcessRecord"。]: /dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord
["WriteError"。]: /dotnet/api/System.Management.Automation.Cmdlet.WriteError
[System.object。]: /dotnet/api/System.Management.Automation.Cmdlet
[System.web. ErrorCategory]: /dotnet/api/System.Management.Automation.ErrorCategory
[System.web. ErrorRecord]: /dotnet/api/System.Management.Automation.ErrorRecord
