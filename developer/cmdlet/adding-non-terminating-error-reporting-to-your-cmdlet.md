---
title: 添加非终止错误报告到 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2a1531a-a92a-4606-9d54-c5df80d34f33
caps.latest.revision: 8
ms.openlocfilehash: 2f3bb481722363557c93ebbc5e6df62baeff2555
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862003"
---
# <a name="adding-non-terminating-error-reporting-to-your-cmdlet"></a>向 Cmdlet 添加非终止错误报告

Cmdlet 可以通过调用报告非终止错误[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法和仍继续运行当前的输入对象或更多传入管道对象。 本部分介绍如何创建 cmdlet，它报告从其输入的处理方法的非终止错误。

非终止错误 （以及终止错误） 必须通过该 cmdlet [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord)标识错误的对象。 由名为"错误标识符。"的唯一字符串标识每个错误记录 指定定义常量的标识符，除了每个错误的类别[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)枚举。 用户可以查看根据其类别设置的错误`$ErrorView`"CategoryView"变量。

错误记录的详细信息，请参阅[Windows PowerShell 错误记录](./windows-powershell-error-records.md)。

在本部分中的主题包括：

- [定义 Cmdlet](#Defining-the-Cmdlet)

- [定义参数](#Defining-Parameters)

- [重写输入处理方法](#Overriding-Input-Processing-Methods)

- [报告非终止错误](#Reporting-Nonterminating-Errors)

- [代码示例](#Code-Sample)

- [定义对象类型和格式设置](#Define-Object-Types-and-Formatting)

- [生成该 Cmdlet](#Building-the-Cmdlet)

- [测试 Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>定义 Cmdlet

Cmdlet 创建的第一步是始终命名 cmdlet 和实现该 cmdlet 的.NET 类声明。 此 cmdlet 检索进程信息，因此在此处选择谓词名称为"Get"。 （几乎任何类型的检索信息的 cmdlet 可以处理命令行输入）。有关已批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 的动词名称](./approved-verbs-for-windows-powershell-commands.md)。

下面是此 Get-proc cmdlet 的定义。 此定义的详细信息中提供了[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md)。

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

如有必要，你的 cmdlet 必须定义用于处理输入的参数。 定义此 Get-proc cmdlet`Name`参数中所述[添加该进程的命令行输入的参数](./adding-parameters-that-process-command-line-input.md)。

下面是参数声明为`Name`此 Get-proc cmdlet 的参数。

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

所有 cmdlet 必须重都写的输入处理方法提供的至少[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)类。 在讨论这些方法[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md)。

> [!NOTE]
> 你的 cmdlet 应尽可能独立处理每条记录。

此 Get-proc cmdlet 覆盖[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法以处理`Name`输入提供的用户或脚本的参数。 如果未提供名称，此方法将获取每个请求的进程名称或所有进程的进程。 此替代的详细信息中提供了[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md)。

#### <a name="things-to-remember-when-reporting-errors"></a>要记住时报告错误的事项

[System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) cmdlet 将写入错误需要在其核心异常时传递给对象。 确定要使用的异常时，请遵循.NET 准则。 基本上，如果错误是在语义上与现有异常不同，该 cmdlet 应使用或派生自该异常。 否则，它应派生的新异常或直接从异常层次结构[System.Exception](/dotnet/api/System.Exception)类。

创建错误标识符 （通过 ErrorRecord 类的 FullyQualifiedErrorId 属性访问） 时请记住以下。

- 为诊断目的，以便检查完全限定的标识符时能够确定哪些错误以及错误来自针对使用字符串。

- 格式正确的完全限定的错误标识符可能按如下所示。

`CommandNotFoundException,Micrososft.PowerShell.Commands.GetCommanddCommand.`

请注意，在上一示例中，错误标识符 （第一个标记） 指定的错误和剩余部分指示错误来自。

- 对于更复杂的方案，错误标识符可以是可以分析在检查点分隔标记。 这允许过分支上的部分错误标识符，以及错误标识符和错误类别。

该 cmdlet 应将特定的错误标识符分配给不同的代码路径。 请注意分配错误标识符的以下信息：

- 错误标识符应保持不变 cmdlet 生命周期内。 不要更改错误标识符 cmdlet 版本之间的语义。

- 使用文本 tersely 对应于所报告的错误的错误标识符。 不要使用空格或标点。

- 具有你生成仅是可重现的错误标识符的 cmdlet。 例如，它不应生成包括进程标识符的标识符。 仅当它们对应于被其他用户遇到相同问题的标识符时，错误标识符是对用户有用。

未经处理的异常不会捕获 Windows PowerShell 在下列情况：

- 如果 cmdlet 创建新线程并运行，因为线程引发未经处理的异常的代码，Windows PowerShell 将不会捕获该错误，并将终止进程。

- 如果一个对象将在其析构函数或 Dispose 方法会导致未经处理的异常的代码，Windows PowerShell 将不会捕获该错误，并将终止进程。

## <a name="reporting-nonterminating-errors"></a>报告非终止错误

输入处理方法之一可以向输出流使用报告非终止错误[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)方法。 下面是一个代码示例演示对调用此 Get-proc cmdlet [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)从在重写中的[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。 在这种情况下，如果该 cmdlet 找不到指定的进程标识符的过程进行调用。

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

#### <a name="things-to-remember-about-writing-nonterminating-errors"></a>要记住有关编写非终止错误的事项

对于非终止错误，该 cmdlet 必须生成每个特定的输入对象的特定错误标识符。

Cmdlet 常常需要修改 Windows PowerShell 操作生成的非终止错误。 它可以执行此操作通过定义`ErrorAction`和`ErrorVariable`参数。 如果定义`ErrorAction`参数，cmdlet 提供的用户选项[System.Management.Automation.Actionpreference](/dotnet/api/system.management.automation.actionpreference)，您可以通过设置直接影响操作`$ErrorActionPreference`变量。

该 cmdlet 可以将非终止错误保存到变量使用`ErrorVariable`参数，它的设置不影响`ErrorAction`。 故障可以将追加到现有错误变量通过添加一个加号 （+） 向变量名称的开头。

## <a name="code-sample"></a>代码示例

有关完整C#示例代码，请参阅[GetProcessSample04 示例](./getprocesssample04-sample.md)。

## <a name="define-object-types-and-formatting"></a>定义对象类型和格式设置

Windows PowerShell cmdlet 使用.NET 对象之间传递信息。 因此，一个 cmdlet 可能需要定义其自己的类型，或者该 cmdlet 可能需要扩展现有类型提供的另一个 cmdlet。 有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。

## <a name="building-the-cmdlet"></a>生成该 Cmdlet

实现一个 cmdlet 之后, 您必须注册它使用 Windows PowerShell 通过 Windows PowerShell 管理单元。 有关注册 cmdlet 的详细信息，请参阅[如何注册 Cmdlet、 提供商和主机应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-cmdlet"></a>测试 Cmdlet

当已使用 Windows PowerShell 注册你的 cmdlet 时，可以通过运行命令行上测试它。 让我们测试示例 Get-proc cmdlet，以查看它是否报告了错误：

- 启动 Windows PowerShell，并使用 Get-proc cmdlet 来检索名为"TEST"的进程。

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

[添加进程管道输入的参数](./adding-parameters-that-process-pipeline-input.md)

[添加处理命令行输入的参数](./adding-parameters-that-process-command-line-input.md)

[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md)

[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[如何注册 Cmdlet、 提供程序，和托管应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell 参考](../windows-powershell-reference.md)

[Cmdlet 示例](./cmdlet-samples.md)
