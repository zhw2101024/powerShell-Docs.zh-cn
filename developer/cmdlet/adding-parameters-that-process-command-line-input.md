---
title: 将处理命令行输入的参数添加 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: c9ad84c5bcb6826fcf51db9a1f1a578a65a1f275
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854946"
---
# <a name="adding-parameters-that-process-command-line-input"></a>添加用于处理命令行输入的参数

一个用于某个 cmdlet 的源是输入的命令行。 本主题介绍如何将参数添加到**Get-proc** cmdlet (中所述[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md))，以便该 cmdlet 可以处理来自基于显式的本地计算机的输入对象传递给 cmdlet。 **Get-proc**所述的 cmdlet 此处检索的过程基于它们的名称，然后显示在命令提示符下的进程的信息。

## <a name="defining-the-cmdlet-class"></a>定义在 Cmdlet 类

Cmdlet 创建的第一步是 cmdlet 命名和.NET Framework 类实现该 cmdlet 的声明。 此 cmdlet 检索进程信息，因此在此处选择谓词名称为"Get"。 （几乎任何类型的检索信息的 cmdlet 可以处理命令行输入）。有关已批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 的动词名称](./approved-verbs-for-windows-powershell-commands.md)。

下面是有关在类声明**Get-proc** cmdlet。 中提供了有关此定义的详细信息[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md)。

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a>声明参数

Cmdlet 参数使用户能够向该 cmdlet 提供输入。 在以下示例中， **Get-proc**并`Get-Member`是通过管道传递 cmdlet 的名称和`MemberType`是一个参数为`Get-Member`cmdlet。 该参数具有参数"属性"。

**PS > 获取进程;`get-member` -membertype 属性**

若要声明 cmdlet 的参数，必须首先定义表示参数的属性。 在中**Get-proc** cmdlet，唯一的参数是`Name`，在这种情况下表示要检索的.NET Framework 进程对象的名称。 因此，在 cmdlet 类定义为接受名称的数组为类型字符串的属性。

下面是参数声明`Name`的参数**Get-proc** cmdlet。

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

若要通知的 Windows PowerShell 运行此属性时`Name`参数， [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)属性添加到属性定义。 声明此属性的基本语法是`[Parameter()]`。

> [!NOTE]
> 参数必须显式标记为公共。 未标记为公共的默认为内部和通过 Windows PowerShell 运行时找不到的参数。

此 cmdlet 使用的字符串数组`Name`参数。 如果可能，你的 cmdlet 还应定义参数作为一个数组，因为这允许该 cmdlet 将接受多个项。

#### <a name="things-to-remember-about-parameter-definitions"></a>要记住有关参数定义的事项

- 预定义的 Windows PowerShell 参数名称和数据类型应重复使用尽可能多地以确保你的 cmdlet 使用 Windows PowerShell cmdlet 兼容。 例如，如果所有 cmdlet 都使用预定义`Id`参数名称，若要轻松地识别资源，用户将可理解的参数，而不考虑他们使用哪些 cmdlet 的含义。 基本上，参数名称遵循相同的规则所使用的公共语言运行时 (CLR) 中的变量名称。 有关参数命名的详细信息，请参阅[Cmdlet 参数名称](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb)。

- Windows PowerShell 保留几个参数名称，以提供一致的用户体验。 不使用这些参数名称： `WhatIf`， `Confirm`， `Verbose`， `Debug`， `Warn`， `ErrorAction`， `ErrorVariable`， `OutVariable`，和`OutBuffer`。 此外，保留这些参数名称的下列别名： `vb`， `db`， `ea`， `ev`， `ov`，并`ob`。

- `Name` 是简单和常见的参数名称，建议在 cmdlet 中使用。 最好选择类似下面的参数名称是唯一的一个特定的 cmdlet 和难以记住的复杂名称。

- 参数是在 Windows PowerShell 中，不区分大小写的尽管默认情况下在 shell 保留大小写。 参数区分大小写取决于该 cmdlet 的操作。 参数指定在命令行传递到参数。

- 有关其他参数声明的示例，请参阅[Cmdlet 参数](./cmdlet-parameters.md)。

## <a name="declaring-parameters-as-positional-or-named"></a>将参数声明为位置或命名

Cmdlet 必须为位置或命名参数设置每个参数。 这两种类型的参数采用单个参数，用逗号隔开和布尔值设置的多个自变量。 一个布尔型参数，也称为*切换*，处理仅布尔设置。 开关用于确定参数存在。 建议的默认值是`false`。

该示例**Get-proc** cmdlet 定义`Name`参数用作位置参数具有位置 0。 这意味着用户输入的命令行的第一个参数将自动插入此参数。 如果你想要定义一个命名的参数，用户必须指定用于将参数名称从命令行中，将保留`Position`带特性声明的关键字。

> [!NOTE]
> 除非必须命名参数，否则我们建议您进行最常用的参数位置，以便用户不需要键入参数名称。

## <a name="declaring-parameters-as-mandatory-or-optional"></a>将参数声明为必需或可选

Cmdlet 必须设置每个参数为可选或必需的参数。 在此示例中**Get-proc** cmdlet，`Name`参数定义为可选，因为`Mandatory`在特性声明中未设置关键字。

## <a name="supporting-parameter-validation"></a>支持的参数验证

该示例**Get-proc** cmdlet 添加输入的验证属性[System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute)到`Name`参数来启用验证，既不是输入`null`也不为空。 此属性是由 Windows PowerShell 提供的多个验证属性之一。 有关其他验证特性的示例，请参阅[验证参数输入](./validating-parameter-input.md)。

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a>重写方法的处理的输入

如果你的 cmdlet 将处理命令行输入，则必须重写相应的输入处理方法。 中引入的基本输入的处理方法[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md)。

**Get-proc** cmdlet 将重写[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法以处理`Name`参数输入提供的用户或脚本。 如果未提供名称，此方法获取每个请求的进程名称，或全部进程的进程。 请注意，在[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)，在调用[System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)是输出机制，用于将输出发送到管道对象。 此调用，第二个参数`enumerateCollection`，设置为`true`以通知 Windows PowerShell 运行时枚举的进程对象的输出数组和一个进程一次写入命令行。

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
    // Write the processes to the pipeline making them available
    // to the next cmdlet. The second argument of this call tells
    // PowerShell to enumerate the array, and send one process at a
    // time to the pipeline.
    WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>代码示例

有关完整C#示例代码，请参阅[GetProcessSample02 示例](./getprocesssample02-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定义对象类型和格式设置

Windows PowerShell cmdlet 通过使用.NET Framework 对象之间传递信息。 因此，一个 cmdlet 可能需要定义其自己的类型，或者一个 cmdlet 可能需要扩展现有类型提供的另一个 cmdlet。 有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。

## <a name="building-the-cmdlet"></a>生成该 Cmdlet

实现一个 cmdlet 后，必须使用 Windows PowerShell 使用 Windows PowerShell 管理单元来注册它。 有关注册 cmdlet 的详细信息，请参阅[如何注册 Cmdlet、 提供商和主机应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-cmdlet"></a>测试 Cmdlet

使用 Windows PowerShell 注册 cmdlet 时，可以通过运行命令行上对它进行测试。 以下是两种方法来测试该示例 cmdlet 的代码。 有关使用命令行中的 cmdlet 的详细信息，请参阅[Windows PowerShell 入门学习](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

- 在 Windows PowerShell 提示符下，使用以下命令列出 Internet Explorer 进程，名为"IEXPLORE。"

    ```powershell
    PS> get-proc -name iexplore
    ```

将显示以下输出。

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- 若要列出名为"IEXPLORE"的 Internet Explorer、 Outlook 和记事本进程，"OUTLOOK"和"记事本"，请使用以下命令。 如果有多个进程，将显示所有这些。

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

将显示以下输出。

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a>另请参阅

[添加进程管道输入的参数](./adding-parameters-that-process-pipeline-input.md)

[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md)

[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[如何注册 Cmdlet、 提供程序，和托管应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell 参考](../windows-powershell-reference.md)

[Cmdlet 示例](./cmdlet-samples.md)
