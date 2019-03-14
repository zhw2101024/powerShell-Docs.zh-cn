---
title: 强烈建议在开发指导原则设置 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d68a8f3-fba0-44c5-97b9-9fc191d269a5
caps.latest.revision: 13
ms.openlocfilehash: c11e50913d2654b786e0e8cfeaf41454999bf75e
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794960"
---
# <a name="strongly-encouraged-development-guidelines"></a>强烈建议的开发指南

本部分介绍当编写 cmdlet 时应遵循的准则。 它们分为设计 cmdlet 和指引，用于编写 cmdlet 代码的准则。 您可能会发现这些准则不是适用于每个方案。 但是，如果它们适用，并且不遵循这些指导原则，你的用户可能必须在使用 cmdlet 时体验不佳。

## <a name="design-guidelines"></a>设计指南

- [使用特定名词的 Cmdlet 名称 (SD01)](./strongly-encouraged-development-guidelines.md#use-a-specific-noun-for-a-cmdlet-name-sd01)

- [使用 pascal 大小写的 Cmdlet 名称 (SD02)](./strongly-encouraged-development-guidelines.md#use-pascal-case-for-cmdlet-names-sd02)

- [参数设计准则 (SD03)](./strongly-encouraged-development-guidelines.md#parameter-design-guidelines-sd03)

- [向用户 (SD04) 提供反馈](./strongly-encouraged-development-guidelines.md#provide-feedback-to-the-user-sd04)

- [创建 Cmdlet 帮助文件 (SD05)](./strongly-encouraged-development-guidelines.md#create-a-cmdlet-help-file-sd05)

## <a name="code-guidelines"></a>代码指南

- [编码的参数 (SC01)](./strongly-encouraged-development-guidelines.md#coding-parameters-sc01)

- [支持定义完善的管道输入 (SC02)](./strongly-encouraged-development-guidelines.md#support-well-defined-pipeline-input-sc02)

- [单个记录写入管道 (SC03)](./strongly-encouraged-development-guidelines.md#write-single-records-to-the-pipeline-sc03)

- [使 Cmdlet 不区分大小写和保留大小写的 (SC04)](./strongly-encouraged-development-guidelines.md#make-cmdlets-case-insensitive-and-case-preserving-sc04)

## <a name="design-guidelines"></a>设计指南

Cmdlet 以确保使用 cmdlet 和其他 cmdlet 之间一致的用户体验在设计时应遵循以下准则。 找到一个设计指导原则适用于你的情况，请务必查看类似的指导原则的代码准则。

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>使用特定名词的 Cmdlet 名称 (SD01)

Cmdlet 名称中使用的名词必须非常具体，以便用户可以发现 cmdlet。 前缀"server"产品名称的缩写版本，例如泛型名词。 例如，如果某个名词所引用的运行 Microsoft SQL Server 实例的服务器，使用如"SQLServer"名词。 特定名词组成和批准的动词的简短列表使用户能够快速发现并避免在 cmdlet 名称之间的重复时预测其功能。

若要增强用户体验，名词的 cmdlet 名称选择应为单数形式。 例如，使用名称`Get-Process`而不是**Get 进程**。 最好是时要遵循此规则的所有 cmdlet 名称，甚至是可能对其多个项执行操作。

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>使用 pascal 大小写的 Cmdlet 名称 (SD02)

为参数名称使用 Pascal 大小写。 换而言之，动词和名词中使用的所有字词的第一个字母大写。 例如，"`Clear-ItemProperty`"。

### <a name="parameter-design-guidelines-sd03"></a>参数设计准则 (SD03)

Cmdlet 需要接收的它必须运行的数据的参数和参数，可指示用于确定操作的特征的信息。 例如，可能有 cmdlet`Name`接收管道，并使用 cmdlet 提供的数据的参数可能具有`Force`参数以指示该 cmdlet，可以被强制执行其操作。 可以定义一个 cmdlet 的参数的数目没有限制。

#### <a name="use-standard-parameter-names"></a>使用标准参数名称

你的 cmdlet 应使用标准参数名称，以便用户能够快速确定某个特定参数的含义。 如果需要更具体的名称，使用标准参数的名称，，然后指定作为别名的更具体的名称。 例如， `Get-Service` cmdlet 具有一个参数具有通用名称 (`Name`) 和更具体的别名 (`ServiceName`)。 这两个术语可以用于指定该参数。

有关参数的名称和数据类型的详细信息，请参阅[Cmdlet 参数名称和功能的指导原则](./standard-cmdlet-parameter-names-and-types.md)。

#### <a name="use-singular-parameter-names"></a>使用单数形式的参数名称

避免使用其值为单个元素的参数的复数形式的名称。 这包括获取数组的参数或列表，因为用户可能会提供的数组或列表仅包含一个元素。

应仅在这些情况下，参数的值始终是多个元素值中使用复数形式的参数名称。 在这些情况下，该 cmdlet 应验证，提供了多个元素，并且该 cmdlet 应显示一条警告向用户如果未提供多个元素。

#### <a name="use-pascal-case-for-parameter-names"></a>为参数名称使用 Pascal 大小写

为参数名称使用 Pascal 大小写。 换而言之，每个单词中的参数名称，包括名称的第一个字母的第一个字母大写。 例如，参数名称`ErrorAction`使用正确的大小写。 以下参数名称使用不正确的大写：

- `errorAction`

- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>获取选项的列表的参数

有两种方法可创建可从一组选项中选择其值的参数。

- 定义枚举类型 （或使用现有枚举类型），它指定有效的值。 然后，使用枚举类型以创建该类型的参数。

- 添加**ValidateSet**参数声明的属性。 有关此属性的详细信息，请参阅[ValidateSet 特性声明](./validateset-attribute-declaration.md)。

#### <a name="use-standard-types-for-parameters"></a>使用标准类型作为参数

若要确保与其他 cmdlet 保持一致，请对参数使用标准类型，就可能。 应该用于不同的参数的类型的详细信息，请参阅[标准 Cmdlet 参数名称和类型](./standard-cmdlet-parameter-names-and-types.md)。 本主题提供指向介绍的名称和组的标准参数，例如"活动参数"的.NET Framework 类型的几个主题。

#### <a name="use-strongly-typed-net-framework-types"></a>使用强类型化的.NET Framework 类型

参数应定义为.NET Framework 类型，以提供更好的参数验证。 例如，被限制为一个值从一组值的参数应定义为枚举类型。 若要支持的统一资源标识符 (URI) 值，定义为参数[System.Uri](/dotnet/api/System.Uri)类型。 避免以外的所有的自由格式文本属性的基本字符串参数。

#### <a name="use-consistent-parameter-types"></a>使用一致的参数类型

由多个 cmdlet 中使用相同的参数时，始终使用相同的参数类型。  例如，如果`Process`参数是[System.Int16](/dotnet/api/System.Int16)类型的一个 cmdlet，禁止`Process`另一个 cmdlet 的参数[System.Uint16](/dotnet/api/System.UInt16)类型。

#### <a name="parameters-that-take-true-and-false"></a>参数采用 True 和 False

如果你参数仅采用`true`并`false`，此参数定义为类型[System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter)。 开关参数被视为`true`当命令中指定。 如果在命令中不包括参数，则 Windows PowerShell 会考虑参数的值`false`。 未定义布尔参数。

如果参数需要 3 个值之间进行区分： $true、 $false 和"未指定"，然后定义类型可以为 Null 的参数\<bool >。  需要第三，"未指定"的值通常发生在该 cmdlet 可以修改对象的布尔属性。 在这种情况下"未指定"意味着若要更改属性的当前值。

#### <a name="support-arrays-for-parameters"></a>支持的参数数组

通常情况下，用户必须执行针对多个自变量相同的操作。 对于这些用户，cmdlet 应作为参数输入，以便用户可以将参数传递给 Windows PowerShell 变量作为参数接受一个数组。 例如， [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 用于标识要检索的进程的名称的字符串数组。

#### <a name="support-the-passthru-parameter"></a>支持 PassThru 参数

默认情况下，许多 cmdlet 修改的系统，如[Stop-process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet，充当"接收器"的对象并不返回结果。 这些 cmdlet 应实现`PassThru`参数强制 cmdlet 返回的对象。 当`PassThru`指定参数，该 cmdlet 返回一个对象使用调用[System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。 例如，以下命令停止 Calc 进程，并将生成进程传递到管道。

```powershell
Stop-Process calc -passthru
```

在大多数情况下，添加、 集和新建 cmdlet 应支持`PassThru`参数。

#### <a name="support-parameter-sets"></a>支持的参数集

Cmdlet 用于完成单一用途。 但是，经常没有多个方法来描述该操作或操作目标。 例如，进程可能将其标识，通过其名称、 其标识符，或将进程对象。 该 cmdlet 应支持其目标的所有合理的表示形式。 通常情况下，该 cmdlet 通过指定的参数 （也称为参数集） 一起运行，集来满足此要求。 单个参数可以属于任意数量的参数集。 有关参数集的详细信息，请参阅[Cmdlet 参数可设置](./cmdlet-parameter-sets.md)。

当指定的参数集时，设置到 ValueFromPipeline 集中只有一个参数。 有关如何声明的详细信息**参数**属性，请参阅[ParameterAttribute 声明](./parameter-attribute-declaration.md)。

当使用不同参数集时，根据定义的默认参数集**Cmdlet**属性。 默认参数集应包括最有可能在交互式 Windows PowerShell 会话中使用的参数。 有关如何声明的详细信息**Cmdlet**属性，请参阅[CmdletAttribute 声明](./cmdlet-attribute-declaration.md)。

### <a name="provide-feedback-to-the-user-sd04"></a>向用户 (SD04) 提供反馈

使用本节中的准则向用户提供反馈。 此反馈可让用户需要注意的系统中所发生并做出更好地管理决策。

Windows PowerShell 运行时，用户可以指定如何处理到每个调用的输出`Write`通过设置首选项变量的方法。 用户可以设置多个首选项变量，其中包括用于确定系统是否应显示信息和确定系统是否应采取进一步操作之前查询用户的变量的变量。

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>支持 WriteWarning、 WriteVerbose 和 WriteDebug 方法

Cmdlet 应调用[System.Management.Automation.Cmdlet.Writewarning*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)方法，该 cmdlet 时要执行的操作可能产生意外的结果。 例如，一个 cmdlet 应调用此方法，如果该 cmdlet 将覆盖只读文件。

Cmdlet 应调用[System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法时用户需要深入了解有关该 cmdlet 的用途。 例如，如果 cmdlet 作者大家都有可能需要有关该 cmdlet 正在执行什么操作的详细信息的情况下 cmdlet 应调用此信息。

该 cmdlet 应调用[System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)时开发人员或产品的支持工程师必须了解什么损坏了 cmdlet 操作的方法。 没有必要 cmdlet 来调用[System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)方法中调用的相同代码[System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)方法因为`Debug`参数提供了这两组信息。

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>支持 WriteProgress 需要很长时间的操作

Cmdlet 操作的需要很长时间才能完成，不能在后台运行应支持进度报告通过定期调用[System.Management.Automation.Cmdlet.Writeprogress*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress)方法。

#### <a name="use-the-host-interfaces"></a>使用主机接口

有时，cmdlet 必须直接与用户通信而不是通过使用各种编写或应支持的方法[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)类。 在这种情况下，该 cmdlet 应派生自[System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)类并使用[System.Management.Automation.Pscmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host)属性。 此属性支持不同级别的通信类型，包括 PromptForChoice、 提示和 WriteLine/ReadLine 类型。 最特定的级别，它还提供可读取和写入单个键以及处理缓冲区的方式。

除非 cmdlet 专门用于生成图形用户界面 (GUI)，它应不绕过主机通过使用[System.Management.Automation.Pscmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host)属性。 为生成 GUI 而设计的 cmdlet 的一个示例是[Out-gridview](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView) cmdlet。

> [!NOTE]
> 不应使用 Cmdlet [System.Console](/dotnet/api/System.Console) API。

### <a name="create-a-cmdlet-help-file-sd05"></a>创建 Cmdlet 帮助文件 (SD05)

为每个 cmdlet 的程序集创建 Help.xml 文件，其中包含有关该 cmdlet 的信息。 此信息包括 cmdlet，该 cmdlet 的参数的说明，该 cmdlet 的使用和的详细信息的示例的说明。

## <a name="code-guidelines"></a>代码指南

在编写代码以确保使用 cmdlet 和其他 cmdlet 之间一致的用户体验的 cmdlet 时，应遵循以下准则。 找到适用于您的具体情况的代码准则，请务必查看类似的指导原则的设计指南。

### <a name="coding-parameters-sc01"></a>编码的参数 (SC01)

定义通过声明使用修饰在 cmdlet 类的公共属性的参数**参数**属性。 参数不需要是 cmdlet 派生的.NET Framework 类的静态成员。 有关如何声明的详细信息**参数**属性，请参阅[参数特性声明](./parameter-attribute-declaration.md)。

#### <a name="support-windows-powershell-paths"></a>支持 Windows PowerShell 路径

Windows PowerShell 路径是用于规范化的命名空间的访问权限的机制。 当将 Windows PowerShell 路径分配到该 cmdlet 中的参数时，用户可以定义自定义"驱动器"充当特定路径的快捷方式。 当用户将指定此类驱动器时，存储的数据，例如数据在注册表中，可以使用一致的方式。

如果你的 cmdlet 允许用户指定一个文件或数据源，它应定义的类型参数[System.String](/dotnet/api/System.String)。 如果支持多个驱动器，则类型应为数组。 参数的名称应`Path`，使用的别名`PSPath`。 此外，`Path`参数应支持通配符字符。 如果对通配符字符不是必需的支持，定义`LiteralPath`参数。

如果该 cmdlet 读取或写入的数据必须是一个文件，该 cmdlet 应接受 Windows PowerShell 路径输入，而应该使用 cmdlet [System.Management.Automation.Sessionstate.Path](/dotnet/api/System.Management.Automation.SessionState.Path)属性来转换 Windows为文件系统识别的路径的 PowerShell 路径。 特定机制包括以下方法：

- [System.Management.Automation.Pscmdlet.Getresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.Pscmdlet.Getunresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)

- [System.Management.Automation.Pathintrinsics.Getresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.Pathintrinsics.Getunresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

如果该 cmdlet 读取或写入的数据仅是一组字符串而不是文件，该 cmdlet 应使用的提供程序的内容信息 (`Content`成员) 来读取和写入。 从获取此信息[System.Management.Automation.Provider.Cmdletprovider.Invokeprovider*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider)属性。 这些机制允许参与的读取和写入数据的其他数据存储。

#### <a name="support-wildcard-characters"></a>支持通配符字符

如果可能，cmdlet 应支持通配符字符。 （尤其是在参数采用一个字符串来标识一组对象中的一个对象），对通配符字符的支持会发生在置于某个 cmdlet 中的多个位置。 例如，示例**停止 Proc** cmdlet 从[StopProc 教程](./stopproc-tutorial.md)定义`Name`参数，以处理表示进程名称的字符串。 此参数支持通配符字符，使用户可以轻松地指定要停止的进程。

如果支持的通配符字符可用，cmdlet 操作通常会生成一个数组。 有时，不值得以支持一个数组，因为用户可能会一次使用单个项。 例如， [Set-location](/powershell/module/Microsoft.PowerShell.Management/Set-Location) cmdlet 不需要支持一个数组，因为用户设置一个位置。 在此情况下，该 cmdlet 仍然支持通配符，但它会强制解析为单个位置。

有关通配符字符模式的详细信息，请参阅[中的 Cmdlet 参数支持通配符](./supporting-wildcard-characters-in-cmdlet-parameters.md)。

#### <a name="defining-objects"></a>定义对象

本部分包含用于定义对象的 cmdlet 和扩展现有对象的原则。

##### <a name="define-standard-members"></a>定义标准的成员

定义要扩展的自定义的 Types.ps1xml 文件 （使用 Windows PowerShell Types.ps1xml 文件作为模板） 中的对象类型的标准成员。 由具有名称 PSStandardMembers 的节点定义标准的成员。 这些定义允许其他 cmdlet 和 Windows PowerShell 运行时以一致的方式使用您的对象。

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>定义要用作参数的 ObjectMembers

如果您正在设计的 cmdlet 的对象，请确保其成员映射到将使用该 cmdlet 的参数直接。 此映射使对象轻松地发送到管道，并从一个 cmdlet 传递到另一个。

由 cmdlet 返回的预先存在.NET Framework 对象经常缺少某些重要或不方便使用的成员所需的脚本开发人员或用户。 这些缺少的成员可以是用于显示和创建正确的成员名称，以便该对象可以正确地传递给管道尤为重要。 创建自定义的 Types.ps1xml 文件，以记录这些必需的成员。 在创建此文件时，我们建议以下命名约定： *< Your_Product_Name >*。Types.ps1xml。

例如，可以添加`Mode`编写脚本属性设置为[System.IO.Fileinfo](/dotnet/api/System.IO.FileInfo)要更清楚地显示文件的属性类型。 此外，还可以添加`Count`别名属性设置为[System.Array](/dotnet/api/System.Array)类型才允许使用一致的该属性名称 (而不是`Length`)。

##### <a name="implement-the-icomparable-interface"></a>实现 IComparable 接口

实现[System.Icomparable](/dotnet/api/System.IComparable)输出的所有对象的接口。 这允许要轻松地输送到不同的排序和分析 cmdlet 的输出对象。

##### <a name="update-display-information"></a>更新显示信息

如果对象的显示不提供预期的结果，创建自定义 *\<YourProductName >*。该对象的 Format.ps1xml 文件。

### <a name="support-well-defined-pipeline-input-sc02"></a>支持定义完善的管道输入 (SC02)

#### <a name="implement-for-the-middle-of-a-pipeline"></a>管道中间的实现

实现假定将从管道的中间调用它的 cmdlet （即，其他 cmdlet 将生成其输入或使用其输出）。 例如，您可能认为`Get-Process`cmdlet，因为它会生成数据，仅用作管道中的第一个 cmdlet。 但是，因为此 cmdlet 专为管道的中间，此 cmdlet 允许上述 cmdlet 或数据管道来指定要检索的进程中。

#### <a name="support-input-from-the-pipeline"></a>支持来自管道的输入

每个参数中为 cmdlet 设置，包括支持来自管道的输入的至少一个参数。 对管道输入支持允许用户检索数据或对象，将其发送到正确的参数集，并将结果传递给某个 cmdlet 直接。

一个参数接受来自管道的输入，如果**参数**属性包括`ValueFromPipeline`关键字，`ValueFromPipelineByPropertyName`关键字属性或在其声明中的这两个关键字。 如果任何参数的参数中设置的支持`ValueFromPipeline`或`ValueFromPipelineByPropertyName`有意义的方式的关键字，该 cmdlet 不能放置后另一个 cmdlet 中，因为它将忽略任何管道输入。

#### <a name="support-the-processrecord-method"></a>支持 ProcessRecord 方法

若要接受管道中前一个 cmdlet 中的所有记录，你的 cmdlet 必须实现[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。 Windows PowerShell 调用此方法多次，一次发送到你的 cmdlet 的每个记录。

### <a name="write-single-records-to-the-pipeline-sc03"></a>单个记录写入管道 (SC03)

当一个 cmdlet 返回对象时，该 cmdlet 应写入对象立即生成它们。 该 cmdlet 不应阻止它们以便它们缓冲到组合数组。 然后，作为输入接收对象的 cmdlet 将能够处理、 显示或处理和显示的输出对象而不会延迟。 Cmdlet 将生成输出对象应调用一次一个地[System.Management.Automation.Cmdlet.Writeobject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)方法。 在批处理中生成输出对象 （例如，因为基础 API 返回的输出对象数组） 的 cmdlet 应调用[System.Managemet.Automation.Cmdlet.Writeobject](/dotnet/api/System.Managemet.Automation.Cmdlet.WriteObject)方法与第二个参数设置到`true`。

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>使 Cmdlet 不区分大小写和保留大小写的 (SC04)

默认情况下，Windows PowerShell 本身就是不区分大小写。 但是，因为它可以处理许多预先存在的系统，Windows PowerShell 会保留案例，以便简化操作和兼容性。 换而言之，如果以大写形式提供一个字符，则 Windows PowerShell 将使其以大写字母。 对于正常的系统，cmdlet 需要遵循此约定。 如果可能，它应运行的不区分大小写的方式。 它应，但是，保留原始的用例出现在命令中更高版本或管道中的 cmdlet。

## <a name="see-also"></a>另请参阅

[所需的开发指导原则](./required-development-guidelines.md)

[咨询开发指导原则](./advisory-development-guidelines.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
