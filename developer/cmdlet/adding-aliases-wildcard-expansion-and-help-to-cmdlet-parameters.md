---
title: 添加别名，通配符扩展，并帮助对 Cmdlet 参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: bc921537062e35aa203fa3ee95d3b7211c89cb28
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733848"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>向 Cmdlet 参数添加别名、通配符扩展和帮助

本部分介绍如何添加别名，通配符扩展和帮助消息到停止进程 cmdlet 的参数 (中所述[创建一个 Cmdlet 来修改系统](./creating-a-cmdlet-that-modifies-the-system.md))。

此停止进程 cmdlet 会尝试停止使用 Get-proc cmdlet 检索的进程 (中所述[创建第一个 Cmdlet](./creating-a-cmdlet-without-parameters.md))。

## <a name="defining-the-cmdlet"></a>定义 Cmdlet

Cmdlet 创建的第一步是始终命名 cmdlet 和实现该 cmdlet 的.NET 类声明。 因为你正在编写 cmdlet 来更改的系统，应相应地命名。 此 cmdlet 停止系统进程，因为它使用定义的谓词"停止" [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)类，使用名词"Proc"以指示过程。 有关已批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 的动词名称](./approved-verbs-for-windows-powershell-commands.md)。

以下代码是此停止进程 cmdlet 的类定义。

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>系统修改为定义参数

Cmdlet 需要该支持系统修改和用户反馈定义参数。 该 cmdlet 应定义`Name`参数或等效身份，以便该 cmdlet 将能够通过某种形式的标识符修改系统。 此外，该 cmdlet 应定义`Force`和`PassThru`参数。 有关这些参数的详细信息，请参阅[创建一个 Cmdlet 来修改系统](./creating-a-cmdlet-that-modifies-the-system.md)。

## <a name="defining-a-parameter-alias"></a>定义参数别名

参数别名可以是一个备用名称或 cmdlet 参数的定义完善 1 号或两个字母短名称。 在这两种情况下，使用别名的目标是简化从命令行的用户条目。 Windows PowerShell 支持通过参数别名[System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute，它使用声明语法 [Alias()]。

下面的代码演示如何将别名添加到`Name`参数。

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

除了使用之外[System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)属性中，Windows PowerShell 运行时执行部分名称匹配，即使不指定了任何别名。 例如，如果你的 cmdlet 具有`FileName`参数，即开头的唯一参数`F`，用户可以输入`Filename`， `Filenam`， `File`， `Fi`，或`F`和仍然识别项作为`FileName`参数。

## <a name="creating-help-for-parameters"></a>创建参数的帮助

Windows PowerShell 允许你为 cmdlet 参数创建帮助。 执行此操作用于系统修改和用户反馈的任何参数。 对于以支持帮助每个参数，可以设置`HelpMessage`属性中的关键字[System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)特性声明。 此关键字定义中使用参数的帮助针对向用户显示的文本。 您还可以设置`HelpMessageBaseName`关键字来标识要用于消息的资源的基名称。 如果设置此关键字，则还必须设置`HelpMessageResourceId`关键字来指定资源标识符。

此停止进程 cmdlet 中的以下代码定义`HelpMessage`属性的关键字`Name`参数。

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a>重写方法的处理的输入

你的 cmdlet 必须重写方法的处理的输入，这是最常[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。 该 cmdlet 时修改系统，应调用[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)并[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，允许用户若要进行更改之前，请提供反馈。 有关这些方法的详细信息，请参阅[创建一个 Cmdlet 来修改系统](./creating-a-cmdlet-that-modifies-the-system.md)。

## <a name="supporting-wildcard-expansion"></a>支持通配符扩展

若要允许选择多个对象，你的 cmdlet 可以使用[System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern)并[System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions)类来提供输入参数的通配符扩展支持。 通配符模式的示例包括 lsa * \*.txt 和 [a-c]\*。 模式包含应按原义使用的字符时，请使用反引号字符 （'） 作为转义符。

通配符扩展的文件和路径名称是该 cmdlet 可能想要允许对路径输入的支持，需要选择多个对象时的常见方案的示例。 常见的情况是在文件系统中，用户要查看当前文件夹中驻留的所有文件。

您应只是偶尔需要自定义的通配符模式匹配实现。 在这种情况下，你的 cmdlet 应支持完整的 POSIX 1003.2、 3.13 规范通配符扩展或以下的简化的子集：

- **问号 （？）。** 匹配任何字符的指定位置。

- **星号 (\*)。** 匹配零个或多个字符的指定位置开始。

- **左大括号 ([])。** 引入了可以包含字符或一系列字符模式大括号表达式。 如果范围是必需的连字符 （-） 用于指示该范围。

- **右大括号 (])。** 结束模式括号表达式。

- **反引号转义符 （'）。** 指示应按字面解释的下一个字符。 请注意，在指定的反引号字符，从命令行 （而不是以编程方式指定） 时，反引号转义符必须指定两次。

> [!NOTE]
> 有关通配符模式的详细信息，请参阅[中的 Cmdlet 参数支持通配符](./supporting-wildcard-characters-in-cmdlet-parameters.md)。

下面的代码演示如何设置通配符选项和定义用于解析的通配符模式`Name`对于此 cmdlet 的参数。

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

下面的代码显示了如何测试进程名称是否与定义的通配符模式匹配。 请注意，在这种情况下，是否进程名称不匹配模式，该 cmdlet 将继续上获取下一步的过程名称。

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>代码示例

有关完整C#示例代码，请参阅[StopProcessSample03 示例](./stopprocesssample03-sample.md)。

## <a name="define-object-types-and-formatting"></a>定义对象类型和格式设置

Windows PowerShell cmdlet 使用.Net 对象之间传递信息。 因此，一个 cmdlet 可能需要定义其自己的类型，或者该 cmdlet 可能需要扩展现有类型提供的另一个 cmdlet。 有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式设置](/previous-versions//ms714665(v=vs.85))。

## <a name="building-the-cmdlet"></a>生成该 Cmdlet

执行后一个 cmdlet，它必须向注册 Windows PowerShell 通过 Windows PowerShell 管理单元。 有关注册 cmdlet 的详细信息，请参阅[如何注册 Cmdlet、 提供商和主机应用程序](/previous-versions//ms714644(v=vs.85))。

## <a name="testing-the-cmdlet"></a>测试 Cmdlet

当已使用 Windows PowerShell 注册你的 cmdlet 时，可以通过运行命令行上测试它。 让我们测试示例停止进程 cmdlet。 有关使用命令行中的 cmdlet 的详细信息，请参阅[Windows PowerShell 入门学习](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

- 启动 Windows PowerShell 并使用停止的进程来停止使用的 ProcessName 别名的进程`Name`参数。

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

将显示以下输出。

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- 请在命令行上的以下条目。 Name 参数是必需的因为系统会提示输入它。 输入"！？" 将显示与参数关联的帮助文本。

    ```powershell
    PS> stop-proc
    ```

将显示以下输出。

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- 现在，请停止与通配符模式匹配的所有进程的以下条目"* 注意\*"。 系统会提示停止与模式匹配每个进程之前。

    ```powershell
    PS> stop-proc -Name *note*
    ```

将显示以下输出。

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

将显示以下输出。

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

将显示以下输出。

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>另请参阅

[创建用于修改系统的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)

[如何创建 Windows PowerShell Cmdlet](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[扩展对象类型和格式设置](/previous-versions//ms714665(v=vs.85))

[如何注册 Cmdlet、 提供程序，和托管应用程序](/previous-versions//ms714644(v=vs.85))

[中的 Cmdlet 参数支持通配符](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
