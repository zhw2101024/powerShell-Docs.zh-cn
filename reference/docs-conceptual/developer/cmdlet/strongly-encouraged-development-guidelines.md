---
title: 强烈建议开发指南 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d68a8f3-fba0-44c5-97b9-9fc191d269a5
caps.latest.revision: 13
ms.openlocfilehash: 0906d0d37c66b8c1538a0b2e9e0f1ff2fba12ac0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369336"
---
# <a name="strongly-encouraged-development-guidelines"></a>强烈建议的开发指南

本部分介绍编写 cmdlet 时应遵循的准则。 它们分为准则，用于设计 cmdlet 以及编写 cmdlet 代码的准则。 你可能会发现这些指南不适用于每个方案。 但是，如果它们确实适用，并且你未遵循这些指导原则，则用户在使用 cmdlet 时可能会遇到不佳的体验。

## <a name="design-guidelines"></a>设计准则

- [使用特定名词作为 Cmdlet 名称（SD01）](./strongly-encouraged-development-guidelines.md#use-a-specific-noun-for-a-cmdlet-name-sd01)

- [对 Cmdlet 名称使用 Pascal 大小写（SD02）](./strongly-encouraged-development-guidelines.md#use-pascal-case-for-cmdlet-names-sd02)

- [参数设计准则（SD03）](./strongly-encouraged-development-guidelines.md#parameter-design-guidelines-sd03)

- [向用户提供反馈（SD04）](./strongly-encouraged-development-guidelines.md#provide-feedback-to-the-user-sd04)

- [创建 Cmdlet 帮助文件（SD05）](./strongly-encouraged-development-guidelines.md#create-a-cmdlet-help-file-sd05)

## <a name="code-guidelines"></a>代码准则

- [编码参数（SC01）](./strongly-encouraged-development-guidelines.md#coding-parameters-sc01)

- [支持定义良好的管道输入（SC02）](./strongly-encouraged-development-guidelines.md#support-well-defined-pipeline-input-sc02)

- [将单个记录写入管道（SC03）](./strongly-encouraged-development-guidelines.md#write-single-records-to-the-pipeline-sc03)

- [使 Cmdlet 不区分大小写并保留大小写（SC04）](./strongly-encouraged-development-guidelines.md#make-cmdlets-case-insensitive-and-case-preserving-sc04)

## <a name="design-guidelines"></a>设计准则

设计 cmdlet 时应遵循以下指导原则，以确保在使用 cmdlet 和其他 cmdlet 之间保持一致的用户体验。 如果找到适用于你的情况的设计准则，请务必查看类似准则的代码准则。

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>使用特定名词作为 Cmdlet 名称（SD01）

Cmdlet 命名中使用的名词需要是非常具体的，以便用户能够发现你的 cmdlet。 将泛型名词（例如 "server"）的前缀作为产品名称的缩写形式。 例如，如果名词引用运行 Microsoft SQL Server 实例的服务器，请使用名词，如 "SQLServer"。 特定名词和批准的动词的简短列表组合使用户能够快速发现并预测功能，同时避免 cmdlet 名称之间的重复。

为了增强用户体验，你为 cmdlet 名称选择的名词应为单数形式。 例如，使用名称 `Get-Process` 而不是**进程**。 最好对所有 cmdlet 名称遵循此规则，即使 cmdlet 可能会对多个项执行操作。

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>对 Cmdlet 名称使用 Pascal 大小写（SD02）

对于参数名称使用 Pascal 大小写。 换言之，将动词的第一个字母和名词中使用的所有字词都大写。 例如，"`Clear-ItemProperty`"。

### <a name="parameter-design-guidelines-sd03"></a>参数设计准则（SD03）

Cmdlet 需要用于接收必须操作的数据的参数，以及指示用于确定操作特征的信息的参数。 例如，一个 cmdlet 可能有一个从管道接收数据的 @no__t 0 参数，该 cmdlet 可能有一个 @no__t 的参数，用于指示该 cmdlet 可以强制执行其操作。 Cmdlet 可以定义的参数数量没有限制。

#### <a name="use-standard-parameter-names"></a>使用标准参数名称

你的 cmdlet 应使用标准参数名称，以便用户可以快速确定特定参数的含义。 如果需要更具体的名称，请使用标准参数名称，然后将更具体的名称指定为别名。 例如，@no__t cmdlet 有一个参数，该参数具有通用名称（`Name`）和更具体的别名（`ServiceName`）。 这两个术语可用于指定参数。

有关参数名称及其数据类型的详细信息，请参阅[Cmdlet 参数名称和功能准则](./standard-cmdlet-parameter-names-and-types.md)。

#### <a name="use-singular-parameter-names"></a>使用单数参数名称

避免对值为单个元素的参数使用复数名称。 这包括采用数组或列表的参数，因为用户可能会提供只包含一个元素的数组或列表。

复数参数名称只能在参数值始终为多元素值的情况下使用。 在这些情况下，cmdlet 应验证是否提供了多个元素，如果未提供多个元素，则 cmdlet 应向用户显示警告。

#### <a name="use-pascal-case-for-parameter-names"></a>对于参数名称使用 Pascal 大小写

对于参数名称使用 Pascal 大小写。 换句话说，将参数名称中每个单词的首字母大写，包括名称的第一个字母。 例如，参数名 `ErrorAction` 使用正确的大小写。 以下参数名称使用了不正确的大小写：

- `errorAction`

- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>采用选项列表的参数

可以通过两种方法来创建参数，该参数的值可以从一组选项中进行选择。

- 定义指定有效值的枚举类型（或使用现有枚举类型）。 然后，使用枚举类型创建该类型的参数。

- 将**ValidateSet**特性添加到参数声明。 有关此属性的详细信息，请参阅[ValidateSet 属性声明](./validateset-attribute-declaration.md)。

#### <a name="use-standard-types-for-parameters"></a>使用参数的标准类型

若要确保与其他 cmdlet 的一致性，请在可能的情况下使用标准类型的参数。 有关应该用于不同参数的类型的详细信息，请参阅[标准 Cmdlet 参数名称和类型](./standard-cmdlet-parameter-names-and-types.md)。 本主题提供了一些主题链接，这些主题描述了标准参数组的名称和 .NET Framework 类型，例如 "活动参数"。

#### <a name="use-strongly-typed-net-framework-types"></a>使用强类型 .NET Framework 类型

应将参数定义为 .NET Framework 类型，以提供更好的参数验证。 例如，限制为一组值中的一个值的参数应定义为枚举类型。 若要支持统一资源标识符（URI）值，请将参数定义为[system.string 类型。](/dotnet/api/System.Uri) 避免为所有自由格式的文本属性提供基本的字符串参数。

#### <a name="use-consistent-parameter-types"></a>使用一致的参数类型

当多个 cmdlet 使用同一个参数时，请始终使用相同的参数类型。  例如，如果 @no__t 参数为一个 cmdlet 的[Int16](/dotnet/api/System.Int16)类型，请不要为另一个 cmdlet 创建[一个类型为的 @no__t](/dotnet/api/System.UInt16) -2 参数。

#### <a name="parameters-that-take-true-and-false"></a>采用 True 和 False 的参数

如果参数仅使用 `true` 并 `false`，则将参数定义为[SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)类型。 在命令中指定开关参数时，该参数将被视为 `true`。 如果命令中未包含该参数，则 Windows PowerShell 会将参数的值视为 `false`。 不要定义布尔参数。

如果参数需要区分三个值： $true、$false 和 "未指定"，则定义类型为 Nullable @ no__t-0bool > 的参数。  当 cmdlet 可以修改对象的布尔属性时，通常会出现第三个 "未指定" 值。 在这种情况下，"未指定" 表示不更改属性的当前值。

#### <a name="support-arrays-for-parameters"></a>支持参数的数组

用户经常需要对多个参数执行相同的操作。 对于这些用户，cmdlet 应接受一个数组作为参数输入，以便用户可以将参数作为 Windows PowerShell 变量传递到参数。 例如，对于标识要检索的进程的名称的字符串， [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 使用数组。

#### <a name="support-the-passthru-parameter"></a>支持 PassThru 参数

默认情况下，修改系统的许多 cmdlet （如[Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet）都充当对象的 "接收器"，不返回结果。 这些 cmdlet 应实现 `PassThru` 参数以强制 cmdlet 返回对象。 当指定 @no__t 的参数时，该 cmdlet 将使用对[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法的调用来返回一个对象。 例如，以下命令将停止 Calc 进程，并将生成的进程传递给管道。

```powershell
Stop-Process calc -passthru
```

在大多数情况下，添加、设置和新的 cmdlet 应支持 @no__t 0 参数。

#### <a name="support-parameter-sets"></a>支持参数集

Cmdlet 用于实现单一目的。 但是，通常有多种方法来描述操作或操作目标。 例如，进程可以通过其名称、其标识符或进程对象进行标识。 该 cmdlet 应支持其目标的所有合理表示形式。 通常，该 cmdlet 通过指定一起操作的参数集（称为 "参数集"）来满足此要求。 单个参数可以属于任意数量的参数集。 有关参数集的详细信息，请参阅[Cmdlet 参数集](./cmdlet-parameter-sets.md)。

指定参数集时，请在 "设置为 ValueFromPipeline" 中仅设置一个参数。 有关如何声明**参数**属性的详细信息，请参阅[ParameterAttribute 声明](./parameter-attribute-declaration.md)。

使用参数集时，默认参数集由**Cmdlet**特性定义。 默认参数集应包含交互 Windows PowerShell 会话中最可能使用的参数。 有关如何声明**Cmdlet**特性的详细信息，请参阅[CmdletAttribute 声明](./cmdlet-attribute-declaration.md)。

### <a name="provide-feedback-to-the-user-sd04"></a>向用户提供反馈（SD04）

使用此部分中的指导原则向用户提供反馈。 此反馈允许用户了解系统中发生的情况，并做出更好的管理决策。

Windows PowerShell 运行时允许用户通过设置首选项变量来指定如何处理对 `Write` 方法的每个调用的输出。 用户可以设置多个首选项变量，包括确定系统是否应显示信息的变量和确定系统是否应在采取进一步操作之前查询用户的变量。

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>支持 WriteWarning、WriteVerbose 和 WriteDebug 方法

当 cmdlet 要执行可能会产生意外结果的操作时，cmdlet 应调用[WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法来调用。 例如，如果 cmdlet 即将覆盖只读文件，则 cmdlet 应调用此方法。

如果用户需要有关 cmdlet 执行的操作的一些详细信息，则 cmdlet 应调用[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法。 例如，如果 cmdlet 作者认为某些方案可能需要有关 cmdlet 执行的操作的详细信息，则 cmdlet 应调用此信息。

当开发人员或产品支持工程师必须了解已损坏 cmdlet 操作时，该 cmdlet 应调用[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法。 对于调用[WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法的相同代码，此 cmdlet 不需要调用[WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法，因为 `Debug` 参数同时提供了两个参数的两种方法。信息集。

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>支持对耗时较长的操作的 WriteProgress

需要很长时间才能完成并且无法在后台运行的 Cmdlet 操作应该支持通过定期调用[WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)方法来报告进度。

#### <a name="use-the-host-interfaces"></a>使用宿主接口

有时，cmdlet 必须直接与用户通信，而不是使用[系统管理](/dotnet/api/System.Management.Automation.Cmdlet)类支持的各种写入或应方法。 在这种情况下，该 cmdlet 应派生自[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)类，并使用[PSCmdlet *](/dotnet/api/System.Management.Automation.PSCmdlet.Host)属性来实现。 此属性支持不同级别的通信类型，包括 PromptForChoice、Prompt 和 WriteLine/ReadLine 类型。 在最具体的层面上，它还提供了读取和写入单个密钥并处理缓冲区的方法。

除非 cmdlet 专用于生成图形用户界面（GUI），否则它不应使用[PSCmdlet *](/dotnet/api/System.Management.Automation.PSCmdlet.Host)属性来绕过该主机。 为生成 GUI 而设计的 cmdlet 的一个示例是 "[外](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView)" cmdlet。

> [!NOTE]
> Cmdlet 不应使用[系统控制台](/dotnet/api/System.Console)API。

### <a name="create-a-cmdlet-help-file-sd05"></a>创建 Cmdlet 帮助文件（SD05）

对于每个 cmdlet 程序集，创建一个包含有关该 cmdlet 的信息的 Help .xml 文件。 此信息包括 cmdlet 的说明、cmdlet 的参数说明、cmdlet 使用的示例等。

## <a name="code-guidelines"></a>代码准则

编写 cmdlet 时应遵循以下准则，以确保在使用 cmdlet 和其他 cmdlet 之间保持一致的用户体验。 如果你发现适用于你的情况的代码准则，请务必查看类似指导原则的设计指南。

### <a name="coding-parameters-sc01"></a>编码参数（SC01）

通过声明使用**parameter**特性修饰的 cmdlet 类的公共属性来定义参数。 参数不一定是 cmdlet 的派生 .NET Framework 类的静态成员。 有关如何声明**参数**属性的详细信息，请参阅[参数属性声明](./parameter-attribute-declaration.md)。

#### <a name="support-windows-powershell-paths"></a>支持 Windows PowerShell 路径

Windows PowerShell 路径是用于规范化对命名空间的访问的机制。 将 Windows PowerShell 路径分配到 cmdlet 中的参数时，用户可以定义一个自定义 "驱动器"，它充当特定路径的快捷方式。 当用户指定此类驱动器时，可以通过一致的方式使用存储的数据（如注册表中的数据）。

如果你的 cmdlet 允许用户指定文件或数据源，则它应定义类型为[system.string](/dotnet/api/System.String)的参数。 如果支持多个驱动器，则类型应为数组。 参数的名称应为 `Path`，别名为 `PSPath`。 此外，@no__t 的参数应支持通配符。 如果不需要支持通配符，请定义 `LiteralPath` 参数。

如果 cmdlet 读取或写入的数据必须是文件，则该 cmdlet 应接受 Windows PowerShell 路径输入，并且该 cmdlet 应使用[Sessionstate](/dotnet/api/System.Management.Automation.SessionState.Path)属性将 Windows powershell 路径转换为文件系统识别的路径。 具体的机制包括以下方法：

- [PSCmdlet. GetResolvedProviderPathFromPSPath。](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)

- [PSCmdlet. GetUnresolvedProviderPathFromPSPath。](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)

- [PathIntrinsics. GetResolvedProviderPathFromPSPath。](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)

- [PathIntrinsics. GetUnresolvedProviderPathFromPSPath。](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

如果 cmdlet 读取或写入的数据只是一组字符串而不是文件，则该 cmdlet 应该使用提供程序内容信息（@no__t 0 成员）进行读取和写入。 此信息是从[CmdletProvider. InvokeProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider)属性获取的。 这些机制允许其他数据存储区参与数据的读取和写入。

#### <a name="support-wildcard-characters"></a>支持通配符

如果可能，cmdlet 应支持通配符。 对通配符的支持发生在 cmdlet 中的多个位置（特别是当参数采用字符串来标识一组对象中的一个对象时）。 例如， [StopProc 教程](./stopproc-tutorial.md)中**的示例**cmdlet 定义了一个 `Name` 参数，用于处理表示进程名称的字符串。 此参数支持通配符，使用户能够轻松地指定要停止的进程。

当支持通配符时，cmdlet 操作通常会生成一个数组。 有时，如果支持数组，则没有意义，因为用户一次只能使用一个项。 例如，[设置位置](/powershell/module/Microsoft.PowerShell.Management/Set-Location)cmdlet 不需要支持数组，因为用户仅设置一个位置。 在这种情况下，该 cmdlet 仍支持通配符，但会强制将分辨率转换为单一位置。

有关通配符模式的详细信息，请参阅[在 Cmdlet 参数中支持通配符](./supporting-wildcard-characters-in-cmdlet-parameters.md)。

#### <a name="defining-objects"></a>定义对象

本部分包含有关为 cmdlet 定义对象以及扩展现有对象的准则。

##### <a name="define-standard-members"></a>定义标准成员

定义标准成员以在自定义 types.ps1xml 文件中扩展对象类型（使用 Windows PowerShell types.ps1xml 文件作为模板）。 标准成员由名称为 PSStandardMembers 的节点定义。 这些定义允许其他 cmdlet 和 Windows PowerShell 运行时以一致的方式处理对象。

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>定义要用作参数的 ObjectMembers

如果要为 cmdlet 设计对象，请确保其成员直接映射到将使用它的 cmdlet 的参数。 通过此映射，可轻松地将对象发送到管道，并将其从一个 cmdlet 传递到另一个 cmdlet。

Cmdlet 返回的预先存在的 .NET Framework 对象常常缺少脚本开发人员或用户所需的一些重要或便捷的成员。 这些缺少的成员对于显示和创建正确的成员名称尤其重要，这样就可以正确地将对象传递到管道。 创建自定义 types.ps1xml 文件来记录这些必需成员。 创建此文件时，建议采用以下命名约定： *< Your_Product_Name >* 。Types.ps1xml。

例如，可以将 `Mode` 脚本属性添加到[FileInfo](/dotnet/api/System.IO.FileInfo)类型，以更清晰地显示文件的属性。 此外，您还可以将 `Count` alias 属性添加到[system.string 类型，](/dotnet/api/System.Array)以允许一致地使用该属性名称（而不是 `Length`）。

##### <a name="implement-the-icomparable-interface"></a>实现 IComparable 接口

在所有输出对象上实现[system.icomparable](/dotnet/api/System.IComparable)接口。 这样，就可以轻松地将输出对象输送到各种排序和分析 cmdlet 中。

##### <a name="update-display-information"></a>更新显示信息

如果对象的显示未提供预期结果，请创建自定义 *\<YourProductName >* 。该对象的 types.ps1xml 文件。

### <a name="support-well-defined-pipeline-input-sc02"></a>支持定义良好的管道输入（SC02）

#### <a name="implement-for-the-middle-of-a-pipeline"></a>实现管道的中间

实现一个 cmdlet，假设它将从管道的中间调用（也就是说，其他 cmdlet 将生成其输入或使用其输出）。 例如，你可能会假设 @no__t 的 cmdlet，因为它会生成数据，仅用作管道中的第一个 cmdlet。 但是，由于此 cmdlet 是为管道的中间设计的，因此此 cmdlet 允许管道中的上一个 cmdlet 或数据指定要检索的进程。

#### <a name="support-input-from-the-pipeline"></a>支持管道中的输入

在 cmdlet 的每个参数集中，至少包括一个支持管道输入的参数。 支持管道输入允许用户检索数据或对象，以将其发送到正确的参数集，并将结果直接传递给 cmdlet。

如果**参数**属性包含 `ValueFromPipeline` 关键字、`ValueFromPipelineByPropertyName` 关键字特性或其声明中的这两个关键字，则参数接受来自管道的输入。 如果参数集中的参数均不支持 `ValueFromPipeline` 或 `ValueFromPipelineByPropertyName` 关键字，则无法有意义地将 cmdlet 置于另一个 cmdlet 之后，因为它将忽略任何管道输入。

#### <a name="support-the-processrecord-method"></a>支持 ProcessRecord 方法

若要接受来自管道中前面的 cmdlet 的所有记录，cmdlet 必须实现[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。 Windows PowerShell 多次调用此方法，一次针对发送到 cmdlet 的每个记录调用一次。

### <a name="write-single-records-to-the-pipeline-sc03"></a>将单个记录写入管道（SC03）

当 cmdlet 返回对象时，cmdlet 应在生成对象时立即写入它们。 Cmdlet 不应包含它们，以便将它们缓冲到合并的数组中。 作为输入接收对象的 cmdlet 将能够处理、显示或处理并显示输出对象，而无需延迟。 一个 cmdlet，它一次生成一个输出对象应调用[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。 成批生成输出对象的 cmdlet （例如，由于基础 API 返回输出对象的数组），应调用[WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法，并将第二个参数设置为 `true`。

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>使 Cmdlet 不区分大小写并保留大小写（SC04）

默认情况下，Windows PowerShell 本身不区分大小写。 然而，由于它处理许多预先存在的系统，因此 Windows PowerShell 确实会保留大小写，以方便操作和兼容性。 换句话说，如果字符以大写字母形式提供，则 Windows PowerShell 会将其保留为大写字母。 为了使系统正常工作，cmdlet 需要遵循此约定。 如果可能，它应以不区分大小写的方式运行。 但是，它应保留在命令中或在管道中随后出现的 cmdlet 的原始事例。

## <a name="see-also"></a>另请参阅

[必需的开发指南](./required-development-guidelines.md)

[咨询开发指南](./advisory-development-guidelines.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
