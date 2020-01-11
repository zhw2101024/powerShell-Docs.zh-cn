---
title: 创建 Windows PowerShell 项提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- item providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], item provider
ms.assetid: a5a304ce-fc99-4a5b-a779-de7d85e031fe
caps.latest.revision: 6
ms.openlocfilehash: a64e49894ce5195cc177e97a7049740389b09456
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870704"
---
# <a name="creating-a-windows-powershell-item-provider"></a>创建 Windows PowerShell 项提供程序

本主题介绍如何创建可操作数据存储中的数据的 Windows PowerShell 提供程序。 在本主题中，存储中的数据元素称为数据存储的 "项"。 因此，可以操作存储中的数据的提供程序称为 Windows PowerShell 项提供程序。

> [!NOTE]
> 你可以使用适用C#于 windows Vista 的 Microsoft Windows 软件开发工具包和 .NET Framework 3.0 运行时组件下载此提供程序的源文件（AccessDBSampleProvider03.cs）。 有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。
> 下载的源文件在 **\<PowerShell 示例 >** 目录中提供。 有关其他 Windows PowerShell 提供程序实现的详细信息，请参阅[设计 Windows Powershell 提供程序](./designing-your-windows-powershell-provider.md)。

本主题中所述的 Windows PowerShell 项提供程序从 Access 数据库获取数据的项。 在这种情况下，"项" 是 Access 数据库中的表或表中的行。

## <a name="defining-the-windows-powershell-item-provider-class"></a>定义 Windows PowerShell 项提供程序类

Windows PowerShell 项提供程序必须定义一个从[Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基类派生的 .net 类的类。 下面是本部分中所述的项提供程序的类定义。

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L34-L36 "AccessDBProviderSample03.cs")]

请注意，在此类定义中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)属性包括两个参数。 第一个参数指定 Windows PowerShell 使用的提供程序的用户友好名称。 第二个参数指定 Windows PowerShell 特定功能，该功能是在命令处理过程中提供给 Windows PowerShell 运行时的。 对于此提供程序，没有添加 Windows PowerShell 特定功能。

## <a name="defining-base-functionality"></a>定义基本功能

如[设计你的 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)中所述， [Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类从提供不同提供程序功能的其他一些类派生。 因此，Windows PowerShell 项提供程序必须定义这些类提供的所有功能。

若要详细了解如何实现添加特定于会话的初始化信息以及释放提供程序所使用的资源的功能，请参阅[创建基本 Windows PowerShell 提供程序](./creating-a-basic-windows-powershell-provider.md)。
但是，大多数提供程序（包括此处所述的提供程序）都可以使用 Windows PowerShell 提供的此功能的默认实现。

在 Windows PowerShell 项提供程序可以操作存储区中的项之前，它必须实现[Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基类的方法以访问数据存储区。 有关实现此类的详细信息，请参阅[创建 Windows PowerShell 驱动器提供程序](./creating-a-windows-powershell-drive-provider.md)。

## <a name="checking-for-path-validity"></a>检查路径有效性

查找数据项时，Windows powershell 运行时 furnishes 提供程序的 Windows PowerShell 路径，如[Windows powershell 的工作](/previous-versions/ms714658(v=vs.85))原理中的 "PSPath 概念" 一节中所述。
Windows PowerShell 项提供程序必须通过实现[Itemcmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)方法，验证传递给它的任何路径的语法和语义有效性。 如果路径有效，则此方法返回 `true`; 否则返回 `false`。 请注意，此方法的实现不应验证路径中的项是否存在，但仅限于路径在语法和语义上是正确的。

下面是此提供程序的[Itemcmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)方法的实现。 请注意，此实现调用 NormalizePath helper 方法将路径中的所有分隔符转换为统一的。

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L274-L298 "AccessDBProviderSample03.cs")]

## <a name="determining-if-an-item-exists"></a>确定项是否存在

验证路径后，Windows PowerShell 运行时必须确定该路径中是否存在数据项。 为了支持这种类型的查询，Windows PowerShell 项提供程序会实现[Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)方法。 此方法返回 `true` 在指定路径找到项，否则返回 `false` （默认值）。

下面是此提供程序的[Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)方法的实现。 请注意，此方法将调用 PathIsDrive、ChunkPath 和 GetTable helper 方法，并使用提供程序定义的 DatabaseTableInfo 对象。

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L229-L267 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-itemexists"></a>有关实现 ItemExists 的注意事项

以下情况可能适用于你的[Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)实现：

- 定义提供程序类时，Windows PowerShell 项提供程序可能会声明 ExpandWildcards、Filter、Include 或 Exclude 来自[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举的提供程序功能。 在这些情况下， [Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)方法的实现必须确保传递给该方法的路径满足指定功能的要求。 若要执行此操作，方法应访问相应的属性，例如， [Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性中的相应属性，例如 ""。

- 此方法的实现应处理对该项的任何形式的访问权限，从而使该项对用户可见。 例如，如果用户通过 FileSystem 提供程序（由 Windows PowerShell 提供）对文件的写入访问权限，但不是读取访问权限，则该文件仍然存在，并且[Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)返回 `true`。 您的实现可能需要检查父项，以查看是否可以枚举该子项。

## <a name="attaching-dynamic-parameters-to-the-test-path-cmdlet"></a>将动态参数附加到测试路径 Cmdlet

有时，调用[Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)的 `Test-Path` cmdlet 会要求在运行时动态指定的附加参数。 若要提供这些动态参数，Windows PowerShell 项提供程序必须实现[Itemcmdletprovider. Itemexistsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters)方法。 此方法检索指定路径处的项的动态参数，并返回一个对象，该对象具有分析特性类似于 cmdlet 类或 [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 对象的属性和字段。 Windows PowerShell 运行时使用返回的对象将参数添加到 `Test-Path` cmdlet 中。

此 Windows PowerShell 项提供程序未实现此方法。 但是，下面的代码是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovideritemexistdynamicparameters](Msh_samplestestcmdlets#testprovideritemexistdynamicparameters)]  -->

## <a name="retrieving-an-item"></a>检索项

若要检索项，Windows PowerShell 项提供程序必须重写[Itemcmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法，以支持来自 `Get-Item` cmdlet 的调用。 此方法将使用[Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法写入项中的项。

下面是此提供程序的[Itemcmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法的实现。 请注意，此方法使用 GetTable 和 GetRow 帮助器方法检索 Access 数据库中的表或数据表中的行的项。

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L132-L163 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-getitem"></a>有关实现 GetItem 的注意事项

以下条件可能适用于[Itemcmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)的实现：。

- 定义提供程序类时，Windows PowerShell 项提供程序可能会声明 ExpandWildcards、Filter、Include 或 Exclude 来自[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举的提供程序功能。 在这些情况下， [Itemcmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)的实现必须确保传递给方法的路径满足这些要求。 若要执行此操作，方法应访问相应的属性，例如， [Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性中的相应属性，例如 ""。

- 默认情况下，此方法的重写不应检索用户通常隐藏的对象，除非[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为 `true`。 例如，FileSystem 提供程序的[Itemcmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法将检查的[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性，然后再尝试为隐藏文件或系统文件调用 *. [Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)的 * 属性中的文件。

## <a name="attaching-dynamic-parameters-to-the-get-item-cmdlet"></a>将动态参数附加到获取项 Cmdlet

有时 `Get-Item` cmdlet 需要在运行时动态指定的其他参数。 若要提供这些动态参数，Windows PowerShell 项提供程序必须实现[Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法。 此方法检索指定路径处的项的动态参数，并返回一个对象，该对象具有分析特性类似于 cmdlet 类或 [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 对象的属性和字段。 Windows PowerShell 运行时使用返回的对象将参数添加到 `Get-Item` cmdlet 中。

此提供程序未实现此方法。 但是，下面的代码是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetitemdynamicparameters](Msh_samplestestcmdlets#testprovidergetitemdynamicparameters)]  -->

## <a name="setting-an-item"></a>设置项

若要设置项，Windows PowerShell 项提供程序必须重写[Itemcmdletprovider. Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法，以支持来自 `Set-Item` cmdlet 的调用。 此方法设置指定路径处的项的值。

此提供程序不提供[Itemcmdletprovider. Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法的重写。 但是，下面是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitem](Msh_samplestestcmdlets#testprovidersetitem)]  -->

#### <a name="things-to-remember-about-implementing-setitem"></a>有关实现 SetItem 的注意事项

以下情况可能适用于你的[Itemcmdletprovider. Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)实现：

- 定义提供程序类时，Windows PowerShell 项提供程序可能会声明 ExpandWildcards、Filter、Include 或 Exclude 来自[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举的提供程序功能。 在这些情况下， [Itemcmdletprovider. Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)的实现必须确保传递给方法的路径满足这些要求。 若要执行此操作，方法应访问相应的属性，例如， [Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性中的相应属性，例如 ""。

- 默认情况下，此方法的重写不应设置或写入从用户隐藏的对象，除非[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为 `true`。 如果路径表示隐藏项，则应将错误发送到 WriteError 方法，并将[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)设置为 `false`。 [Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) * 设置为 ""。

- 在对数据存储进行任何更改之前，你的[Itemcmdletprovider 和 Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法的实现应调用[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ，并验证其返回值的返回值。 此方法用于在对数据存储进行更改时（例如，删除文件时）确认操作的执行。 [Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)方法发送要更改为用户的资源的名称，Windows PowerShell 运行时在确定应显示的内容时考虑了任何命令行设置或首选项变量。

  在对 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 的调用返回 `true` 后，[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 方法应调用 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 方法。 此方法向用户发送一条消息，以允许反馈验证是否应继续进行操作。 对[Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)的调用允许对潜在的危险系统修改进行额外检查。

## <a name="retrieving-dynamic-parameters-for-setitem"></a>正在为 SetItem 检索动态参数

有时 `Set-Item` cmdlet 需要在运行时动态指定的其他参数。 若要提供这些动态参数，Windows PowerShell 项提供程序必须实现[Itemcmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)方法。 此方法检索指定路径处的项的动态参数，并返回一个对象，该对象具有分析特性类似于 cmdlet 类或 [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 对象的属性和字段。 Windows PowerShell 运行时使用返回的对象将参数添加到 `Set-Item` cmdlet 中。

此提供程序未实现此方法。 但是，下面的代码是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitemdynamicparameters](Msh_samplestestcmdlets#testprovidersetitemdynamicparameters)]  -->

## <a name="clearing-an-item"></a>清除项

为了清除某一项，Windows PowerShell 项提供程序会实现[Itemcmdletprovider. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)方法，以支持 `Clear-Item` cmdlet 的调用。 此方法将清除指定路径处的数据项。

此提供程序未实现此方法。 但是，下面的代码是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitem](Msh_samplestestcmdlets#testproviderclearitem)]  -->

#### <a name="things-to-remember-about-implementing-clearitem"></a>有关实现 ClearItem 的注意事项

以下条件可能适用于[Itemcmdletprovider. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)的实现：。

- 定义提供程序类时，Windows PowerShell 项提供程序可能会声明 ExpandWildcards、Filter、Include 或 Exclude 来自[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举的提供程序功能。 在这些情况下， [Itemcmdletprovider. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)的实现必须确保传递给方法的路径满足这些要求。 若要执行此操作，方法应访问相应的属性，例如， [Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性中的相应属性，例如 ""。

- 默认情况下，此方法的重写不应设置或写入从用户隐藏的对象，除非[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为 `true`。 如果路径表示在用户和 Cmdletprovider 中隐藏的项，则应将错误发送到[WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法。 [Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)被设置为 "`false`"，则应发送到该方法。

- 在对数据存储进行任何更改之前，你的[Itemcmdletprovider 和 Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法的实现应调用[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ，并验证其返回值的返回值。 此方法用于在对数据存储进行更改时（例如，删除文件时）确认操作的执行。 [Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)方法通过 Windows PowerShell 运行时向用户发送要更改的资源的名称，并处理任何命令行设置或首选项变量来确定应显示的内容。

  在对 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 的调用返回 `true` 后，[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 方法应调用 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 方法。 此方法向用户发送一条消息，以允许反馈验证是否应继续进行操作。 对[Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)的调用允许对潜在的危险系统修改进行额外检查。

## <a name="retrieve-dynamic-parameters-for-clearitem"></a>检索 ClearItem 的动态参数

有时 `Clear-Item` cmdlet 需要在运行时动态指定的其他参数。 若要提供这些动态参数，Windows PowerShell 项提供程序必须实现[Itemcmdletprovider. Clearitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters)方法。 此方法检索指定路径处的项的动态参数，并返回一个对象，该对象具有分析特性类似于 cmdlet 类或 [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 对象的属性和字段。 Windows PowerShell 运行时使用返回的对象将参数添加到 `Clear-Item` cmdlet 中。

此项提供程序不实现此方法。 但是，下面的代码是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitemdynamicparameters](Msh_samplestestcmdlets#testproviderclearitemdynamicparameters)]  -->

## <a name="performing-a-default-action-for-an-item"></a>为项执行默认操作

Windows PowerShell 项提供程序可以实现[Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)方法，以支持来自 `Invoke-Item` cmdlet 的调用，这允许提供程序为指定路径处的项执行默认操作。 例如，FileSystem 提供程序可能使用此方法来调用特定项的 ShellExecute。

此提供程序未实现此方法。 但是，下面的代码是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultaction](Msh_samplestestcmdlets#testproviderinvokedefaultaction)]  -->

#### <a name="things-to-remember-about-implementing-invokedefaultaction"></a>有关实现 InvokeDefaultAction 的注意事项

以下条件可能适用于[Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)的实现：。

- 定义提供程序类时，Windows PowerShell 项提供程序可能会声明 ExpandWildcards、Filter、Include 或 Exclude 来自[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举的提供程序功能。 在这些情况下， [Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)的实现必须确保传递给方法的路径满足这些要求。 若要执行此操作，方法应访问相应的属性，例如， [Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性中的相应属性，例如 ""。

- 默认情况下，此方法的重写不应设置或写入用户隐藏的对象，除非[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为 `true`。 如果路径表示在用户和 Cmdletprovider 中隐藏的项，则应将错误发送到[WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法。 [Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)被设置为 "`false`"，则应发送到该方法。

## <a name="retrieve-dynamic-parameters-for-invokedefaultaction"></a>检索 InvokeDefaultAction 的动态参数

有时 `Invoke-Item` cmdlet 需要在运行时动态指定的其他参数。 若要提供这些动态参数，Windows PowerShell 项提供程序必须实现[Itemcmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters)方法。 此方法检索指定路径处的项的动态参数，并返回一个对象，该对象具有分析特性类似于 cmdlet 类或 [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 对象的属性和字段。 Windows PowerShell 运行时使用返回的对象将动态参数添加到 `Invoke-Item` cmdlet 中。

此项提供程序不实现此方法。 但是，下面的代码是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters](Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters)]  -->

## <a name="implementing-helper-methods-and-classes"></a>实现 Helper 方法和类

此项提供程序实现由 Windows PowerShell 定义的公共重写方法所使用的几个帮助器方法和类。 下面的[代码示例](#code-sample)部分中显示了这些帮助器方法和类的代码。

### <a name="normalizepath-method"></a>NormalizePath 方法

此项提供程序实现了 NormalizePath helper 方法，以确保路径的格式一致。 指定的格式使用反斜杠（\\）作为分隔符。

### <a name="pathisdrive-method"></a>PathIsDrive 方法

此项提供程序实现 PathIsDrive helper 方法，以确定指定的路径是否确实为驱动器名称。

### <a name="chunkpath-method"></a>ChunkPath 方法

此项提供程序实现了一个 ChunkPath helper 方法，该方法可分解指定的路径，以便提供程序可以标识其各个元素。 它返回由路径元素组成的数组。

### <a name="gettable-method"></a>GetTable 方法

此项提供程序实现 GetTables helper 方法，该方法返回一个 DatabaseTableInfo 对象，该对象表示调用中指定的表的相关信息。

### <a name="getrow-method"></a>GetRow 方法

此项提供程序的[Itemcmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法调用 GetRows helper 方法。 此帮助器方法检索表示有关表中指定行的信息的 DatabaseRowInfo 对象。

### <a name="databasetableinfo-class"></a>DatabaseTableInfo 类

此项提供程序定义了一个 DatabaseTableInfo 类，该类表示数据库中数据表的信息集合。 此类类似于[Directoryinfo](/dotnet/api/System.IO.DirectoryInfo)类。

示例项提供程序定义了 DatabaseTableInfo. GetTables 方法，该方法返回一个表信息对象的集合，这些对象定义数据库中的表。 此方法包含一个 try/catch 块，以确保任何数据库错误都显示为包含零个项的行。

### <a name="databaserowinfo-class"></a>DatabaseRowInfo 类

此项提供程序定义了 DatabaseRowInfo helper 类，该类表示数据库的表中的行。 此类类似于[FileInfo](/dotnet/api/System.IO.FileInfo)类。

示例提供程序定义 DatabaseRowInfo 方法，以返回指定表的行信息对象的集合。 此方法包含用于捕获异常的 try/catch 块。 任何错误都将导致没有行信息。

## <a name="code-sample"></a>代码示例

有关完整的示例代码，请参阅[AccessDbProviderSample03 代码示例](./accessdbprovidersample03-code-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定义对象类型和格式设置

编写提供程序时，可能需要将成员添加到现有对象或定义新的对象。 完成后，创建一个类型文件，Windows PowerShell 可以使用该文件来标识该对象的成员和定义如何显示该对象的格式化文件。 有关的详细信息，请参阅[扩展对象类型和格式](/previous-versions/ms714665(v=vs.85))。

## <a name="building-the-windows-powershell-provider"></a>生成 Windows PowerShell 提供程序

请参阅[如何注册 cmdlet、提供程序和主机应用程序](/previous-versions/ms714644(v=vs.85))。

## <a name="testing-the-windows-powershell-provider"></a>测试 Windows PowerShell 提供程序

向 Windows PowerShell 注册此 Windows PowerShell 项提供程序后，只能测试提供程序的基本和驱动器功能。 若要测试项的操作，还必须实现[实现容器 Windows PowerShell 提供程序](./creating-a-windows-powershell-container-provider.md)中所述的容器功能。

## <a name="see-also"></a>另请参阅

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 程序员指南](./windows-powershell-programmer-s-guide.md)

[创建 Windows PowerShell 提供程序](./how-to-create-a-windows-powershell-provider.md)

[设计你的 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)

[扩展对象类型和格式](/previous-versions/ms714665(v=vs.85))

[Windows PowerShell 的工作原理](/previous-versions/ms714658(v=vs.85))

[创建容器 Windows PowerShell 提供程序](./creating-a-windows-powershell-container-provider.md)

[创建驱动器 Windows PowerShell 提供程序](./creating-a-windows-powershell-drive-provider.md)

[如何注册 Cmdlet、提供程序和主机应用程序](/previous-versions/ms714644(v=vs.85))
