---
title: 向 Cmdlet 参数添加别名、通配符扩展和帮助 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: bc921537062e35aa203fa3ee95d3b7211c89cb28
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72370086"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>向 Cmdlet 参数添加别名、通配符扩展和帮助

本部分介绍如何将别名、通配符扩展和帮助消息添加到 Stop Proc cmdlet 的参数（如[创建修改系统的 cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)中所述）。

此 Stop Proc cmdlet 尝试使用 Get-help cmdlet （在[创建第一个 cmdlet](./creating-a-cmdlet-without-parameters.md)时进行介绍）来停止检索的进程。

## <a name="defining-the-cmdlet"></a>定义 Cmdlet

创建 cmdlet 的第一步是始终命名 cmdlet 并声明实现 cmdlet 的 .NET 类。 因为你要编写一个 cmdlet 来更改系统，所以应该相应地对其进行命名。 由于此 cmdlet 停止系统进程，因此它使用由[Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle)类定义的谓词 "Stop"，名词 "Proc" 表示进程。 有关批准的 cmdlet 谓词的详细信息，请参阅[Cmdlet 谓词名称](./approved-verbs-for-windows-powershell-commands.md)。

下面的代码是此 Stop Proc cmdlet 的类定义。

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>定义系统修改的参数

Cmdlet 需要定义支持系统修改和用户反馈的参数。 该 cmdlet 应定义 `Name` 参数或等效参数，以使 cmdlet 能够按某种标识符修改系统。 此外，该 cmdlet 还应定义 `Force` 和 @no__t 参数。 有关这些参数的详细信息，请参阅[创建修改系统的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。

## <a name="defining-a-parameter-alias"></a>定义参数别名

参数别名可以是 cmdlet 参数的替代名称，也可以是定义完善的1个字母或2个字母的短名称。 在这两种情况下，使用别名的目标是简化命令行中的用户输入。 Windows PowerShell 通过使用声明语法 [Alias （）] 的[Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)特性支持参数别名。

下面的代码演示如何将别名添加到 @no__t 参数中。

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

除了使用[Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)属性，Windows PowerShell 运行时还执行部分名称匹配，即使未指定别名。 例如，如果你的 cmdlet 有 @no__t 0 参数，并且该参数是以 `F` 开头的唯一参数，则用户可以输入 `Filename`，`Filenam`，`File`，`Fi`，或者 `F`，仍可将该条目识别为 `FileName` 参数。

## <a name="creating-help-for-parameters"></a>创建参数的帮助

Windows PowerShell 允许你为 cmdlet 参数创建帮助。 对用于系统修改和用户反馈的任何参数执行此操作。 对于每个支持帮助的参数，可以在[Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute)特性声明中设置 `HelpMessage` attribute 关键字。 此关键字定义要向用户显示的文本，以便在使用参数时获得帮助。 你还可以设置 @no__t 的关键字，以标识用于消息的资源的基名称。 如果设置此关键字，则还必须将 @no__t 关键字设置为指定资源标识符。

此 Stop Proc cmdlet 中的以下代码定义了 @no__t 参数的 `HelpMessage` attribute 关键字。

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

## <a name="overriding-an-input-processing-method"></a>重写输入处理方法

Cmdlet 必须重写输入处理方法，最常见的情况是[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)。 当修改系统时，cmdlet 应调用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，以允许用户在进行更改之前提供反馈信息。 "请确保用户在进行更改之前提供反馈。 有关这些方法的详细信息，请参阅[创建修改系统的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)。

## <a name="supporting-wildcard-expansion"></a>支持通配符扩展

若要允许选择多个对象，你的 cmdlet 可以使用[Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern)和[Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions)类来为参数输入提供通配符扩展支持。 通配符模式的示例包括 lsa *、@no__t 旁1/-0 和 [c] \*。 如果模式包含应按原义使用的字符，则使用后引号字符（'）作为转义符。

文件和路径名的通配符扩展是常见方案的示例，其中，cmdlet 可能需要在需要选择多个对象时允许对路径输入提供支持。 常见的情况是在文件系统中，用户想要查看位于当前文件夹中的所有文件。

只需很少使用自定义通配符模式匹配实现。 在这种情况下，你的 cmdlet 应支持通配符扩展的完整 POSIX 1003.2、3.13 规范或以下简化子集：

- **问号（？）。** 匹配指定位置的任何字符。

- **星号（\*）。** 匹配从指定位置开始的零个或多个字符。

- **左方括号（[）。** 引入一个可包含字符或一系列字符的模式括号表达式。 如果范围是必需的，则使用连字符（-）指示范围。

- **右方括号（]）。** 结束模式方括号表达式。

- **后引号转义符（'）。** 指示应按原义取下一个字符。 请注意，当从命令行（而不是以编程方式指定它）中指定后引号字符时，必须两次指定后引号转义符。

> [!NOTE]
> 有关通配符模式的详细信息，请参阅[在 Cmdlet 参数中支持通配符](./supporting-wildcard-characters-in-cmdlet-parameters.md)。

下面的代码演示如何设置通配符选项，并定义用于解析此 cmdlet 的 `Name` 参数的通配符模式。

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

下面的代码演示如何测试进程名称是否与定义的通配符模式匹配。 请注意，在这种情况下，如果进程名称与模式不匹配，该 cmdlet 将继续获取下一个进程名称。

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>代码示例

有关完整C#的示例代码，请参阅[StopProcessSample03 示例](./stopprocesssample03-sample.md)。

## <a name="define-object-types-and-formatting"></a>定义对象类型和格式设置

Windows PowerShell 使用 .Net 对象在 cmdlet 之间传递信息。 因此，cmdlet 可能需要定义自己的类型，或者该 cmdlet 可能需要扩展另一个 cmdlet 提供的现有类型。 有关定义新类型或扩展现有类型的详细信息，请参阅[扩展对象类型和格式](/previous-versions//ms714665(v=vs.85))。

## <a name="building-the-cmdlet"></a>构建 Cmdlet

实现 cmdlet 后，必须通过 Windows PowerShell 管理单元向 Windows PowerShell 注册它。 有关注册 cmdlet 的详细信息，请参阅[如何注册 cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))。

## <a name="testing-the-cmdlet"></a>测试 Cmdlet

向 Windows PowerShell 注册 cmdlet 后，可以通过在命令行上运行 cmdlet 来对其进行测试。 接下来，请测试示例的停止过程 cmdlet。 有关从命令行使用 cmdlet 的详细信息，请参阅[使用 Windows PowerShell 的入门](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

- 启动 Windows PowerShell，并使用 ProcessName 参数为 @no__t 的别名停止进程。

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

此时将显示以下输出。

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- 在命令行上生成以下项。 因为 Name 参数是必需的，所以系统会提示你输入。 正在输入 "！？" 显示与参数相关联的帮助文本。

    ```powershell
    PS> stop-proc
    ```

此时将显示以下输出。

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- 现在，请执行以下条目来停止所有匹配通配符模式 "* note @ no__t-0" 的进程。 在停止每个与模式匹配的进程之前，系统将提示您。

    ```powershell
    PS> stop-proc -Name *note*
    ```

此时将显示以下输出。

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

此时将显示以下输出。

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

此时将显示以下输出。

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>另请参阅

[创建用于修改系统的 Cmdlet](./creating-a-cmdlet-that-modifies-the-system.md)

[如何创建 Windows PowerShell Cmdlet](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[扩展对象类型和格式](/previous-versions//ms714665(v=vs.85))

[如何注册 Cmdlet、提供程序和主机应用程序](/previous-versions//ms714644(v=vs.85))

[支持 Cmdlet 参数中的通配符](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
