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
ms.openlocfilehash: f2c9e10f0dc392399cf062500b7f28b3d1c07f6e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055115"
---
# <a name="creating-a-windows-powershell-item-provider"></a>创建 Windows PowerShell 项提供程序

本主题介绍如何创建可以处理数据存储区中的数据的 Windows PowerShell 提供程序。 本主题中的存储中的数据元素都称为"项"的数据存储。 因此，可以处理的数据存储区中的提供程序被称为 Windows PowerShell 项提供程序。

> [!NOTE]
> 您可以下载C#Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件使用此提供程序的源文件 (AccessDBSampleProvider03.cs)。 有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> 已下载的源文件中有 **\<PowerShell 示例 >** 目录。
>
> 有关其他 Windows PowerShell 提供程序实现的详细信息，请参阅[设计你 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)。

本主题中所述的 Windows PowerShell 项提供程序从 Access 数据库中获取项的数据。 在这种情况下，"项"是访问数据库中的表或表中的行。

以下列表包含本主题中的部分。 如果您不熟悉编写 Windows PowerShell 项提供程序，阅读这些部分中显示的顺序。 但是，如果你熟悉编写 Windows PowerShell 项提供程序，直接转到所需的信息：

- [定义 Windows PowerShell 项提供程序类](#Defining-the-Windows-PowerShell-Item-Provider-Class)

- [定义基本功能](#Defining-Base-Functionality)

- [路径有效性检查](#Checking-for-Path-Validity)

- [确定项是否存在](#Determining-if-an-Item-Exists)

- [附加到的动态参数`Test-Path`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Test-Path-Cmdlet)

- [检索项](#Retrieving-an-Item)

- [附加到的动态参数`Get-Item`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-Item-Cmdlet)

- [将项目设置](#Setting-an-Item)

- [附加到的动态参数`Set-Item`Cmdlet](#Retrieving-Dynamic-Parameters-for-SetItem)

- [清除某一项](#Clearing-an-Item)

- [附加到 Clear-item Cmdlet 的动态参数](#Retrieve-Dynamic-Parameters-for-ClearItem)

- [项执行默认操作](#Performing-a-Default-Action-for-an-Item)

- [检索 InvokeDefaultAction 动态参数](#Retrieve-Dynamic-Parameters-for-InvokeDefaultAction)

- [实现帮助器方法和类](#Implementing-Helper-Methods-and-Classes)

- [代码示例](#Code-Sample)

- [定义对象类型和格式设置](#Defining-Object-Types-and-Formatting)

- [生成 Windows PowerShell 提供程序](#Building-the-Windows-PowerShell-provider)

- [测试 Windows PowerShell 提供程序](#Testing-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-item-provider-class"></a>定义 Windows PowerShell 项提供程序类

Windows PowerShell 项提供程序必须定义一个.NET 类，派生自[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基类。 下面是在本部分中所述的项提供程序的类定义。

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L34-L36 "AccessDBProviderSample03.cs")]

请注意，在此类定义后， [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)属性包含两个参数。 第一个参数指定由 Windows PowerShell 提供程序的用户友好名称。 第二个参数指定的 Windows PowerShell 的特定功能的提供程序公开到 Windows PowerShell 运行时在命令处理过程。 为此提供程序，没有添加了的 Windows PowerShell 特定功能。

## <a name="defining-base-functionality"></a>定义基本功能

如中所述[设计您的 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)，则[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类派生自多个其他提供不同的类提供程序功能。 Windows PowerShell 项提供程序，因此，必须定义所有这些类提供的功能。

有关如何实现用于添加特定于会话的初始化信息和用于释放资源提供程序使用的功能的详细信息，请参阅[创建一个基本的 Windows PowerShell 提供程序](./creating-a-basic-windows-powershell-provider.md)。 但是，大多数提供程序，包括本文所述的提供程序可以使用 Windows PowerShell 提供此功能的默认实现。

Windows PowerShell 项提供程序可以操作存储区中的项之前，它必须实现的方法[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基类，以访问数据存储空间。 有关实现此类的详细信息，请参阅[创建一个 Windows PowerShell 驱动器提供程序](./creating-a-windows-powershell-drive-provider.md)。

## <a name="checking-for-path-validity"></a>路径有效性检查

查看对于数据的项，Windows PowerShell 运行时提供给提供程序，Windows PowerShell 路径的"PSPath 概念"部分中定义[Windows PowerShell 的工作原理](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)。 Windows PowerShell 项提供程序必须验证传递给它的实现的任何路径的语法和语义有效性[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)方法。 此方法返回`true`路径是否有效，和`false`否则为。 要注意，此方法的实现应验证该路径在语法上的路径，但仅在项目是否存在且语义正确。

下面是实现[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)此提供程序的方法。 请注意，此实现会调用将在路径中的所有分隔符都转换为一个统一的 NormalizePath 帮助器方法。

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L274-L298 "AccessDBProviderSample03.cs")]

## <a name="determining-if-an-item-exists"></a>确定项是否存在

验证路径后, Windows PowerShell 运行时必须确定数据的项是否位于该路径存在。 若要支持此类型的查询，Windows PowerShell 项提供程序实现[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)方法。 此方法返回`true`指定路径处找到的项和`false`（默认），否则。

下面是实现[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)此提供程序的方法。 请注意，此方法调用 PathIsDrive、 ChunkPath 和 GetTable 帮助程序方法，并且使用提供程序定义的 DatabaseTableInfo 对象。

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L229-L267 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-itemexists"></a>要实现 ItemExists 记住的事项

以下条件可能适用于特定的实现[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists):

- 在定义的提供程序类时，Windows PowerShell 项提供程序可能会从声明提供程序功能 ExpandWildcards、 筛选器、 包括或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下，实现[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)方法必须确保传递给方法的路径是否满足指定的功能的要求。 若要执行此操作，该方法应访问相应的属性，例如，则[System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性。

- 此方法的实现应处理任何形式的访问可能会使该项对用户可见的项。 例如，如果用户具有到通过 FileSystem 提供程序 （由 Windows PowerShell 提供），但不能读取访问的文件的写访问权限，该文件仍存在和[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)返回`true`。 您的实现可能需要检查父项以查看子项目可进行枚举。

## <a name="attaching-dynamic-parameters-to-the-test-path-cmdlet"></a>附加到测试路径 Cmdlet 的动态参数

有时`Test-Path`调用的 cmdlet [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)需要在运行时动态指定的其他参数。 若要提供这些动态参数在 Windows PowerShell 项提供程序必须实现[System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters)方法。 此方法检索指定的路径处的项的动态参数并返回具有属性和字段与分析属性类似于 cmdlet 类的对象或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。 Windows PowerShell 运行时使用返回的对象添加到参数`Test-Path`cmdlet。

此 Windows PowerShell 项提供程序未实现此方法。 但是，以下代码是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovideritemexistdynamicparameters](Msh_samplestestcmdlets#testprovideritemexistdynamicparameters)]  -->

## <a name="retrieving-an-item"></a>检索项

若要检索某个项，Windows PowerShell 项提供程序必须重写[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法，以支持来自调用`Get-Item`cmdlet。 此方法写入项使用[System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法。

下面是实现[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)此提供程序的方法。 请注意，此方法使用 GetTable 和 GetRow 帮助器方法来检索访问数据库中的表或数据的表中的行的项。

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L132-L163 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-getitem"></a>要实现 GetItem 记住的事项

以下条件可能适用于的实现[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem):

- 在定义的提供程序类时，Windows PowerShell 项提供程序可能会从声明提供程序功能 ExpandWildcards、 筛选器、 包括或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下，实现[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)必须确保传递给方法的路径是否满足这些要求。 若要执行此操作，该方法应访问相应的属性，例如，则[System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性。

- 默认情况下，重写此方法应检索除非通常隐藏从用户的对象[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为`true`。 例如， [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) FileSystem 提供程序检查方法[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性尝试调用之前[System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)隐藏或系统文件。

## <a name="attaching-dynamic-parameters-to-the-get-item-cmdlet"></a>附加到的 Get-item Cmdlet 的动态参数

有时`Get-Item`cmdlet 需要在运行时动态指定的其他参数。 若要提供这些动态参数在 Windows PowerShell 项提供程序必须实现[System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法。 此方法检索指定的路径处的项的动态参数并返回具有属性和字段与分析属性类似于 cmdlet 类的对象或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。 Windows PowerShell 运行时使用返回的对象添加到参数`Get-Item`cmdlet。

此提供程序未实现此方法。 但是，以下代码是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetitemdynamicparameters](Msh_samplestestcmdlets#testprovidergetitemdynamicparameters)]  -->

## <a name="setting-an-item"></a>将项目设置

若要设置某项，Windows PowerShell 项提供程序必须重写[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法，以支持来自调用`Set-Item`cmdlet。 在指定的路径，此方法设置项的值。

此提供程序不提供的替代[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法。 但是，下面是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitem](Msh_samplestestcmdlets#testprovidersetitem)]  -->

#### <a name="things-to-remember-about-implementing-setitem"></a>要实现 SetItem 记住的事项

以下条件可能适用于特定的实现[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem):

- 在定义的提供程序类时，Windows PowerShell 项提供程序可能会从声明提供程序功能 ExpandWildcards、 筛选器、 包括或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下，实现[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)必须确保传递给方法的路径是否满足这些要求。 若要执行此操作，该方法应访问相应的属性，例如，则[System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性。

- 默认情况下，重写此方法不应设置或写入对象，除非用户隐藏[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为`true`。 错误应发送到[System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法，如果路径表示隐藏的项和[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)设置为`false`。

- 实现[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法应调用[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)，并向数据存储区进行任何更改之前验证它的返回值。 此方法用于更改数据存储，例如，删除文件时确认执行操作。 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)方法发送给用户，与 Windows PowerShell 运行时将考虑在内的任何命令行设置要更改的资源的名称或在确定应显示的内容的首选项变量。

  在调用[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)返回`true`，则[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法应调用[System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法。 此方法将消息发送到用户允许反馈，以验证是否应继续执行该操作。 在调用[System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)允许具有潜在危险的系统修改为其他检查。

## <a name="retrieving-dynamic-parameters-for-setitem"></a>检索 SetItem 动态参数

有时`Set-Item`cmdlet 需要在运行时动态指定的其他参数。 若要提供这些动态参数在 Windows PowerShell 项提供程序必须实现[System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)方法。 此方法检索指定的路径处的项的动态参数并返回具有属性和字段与分析属性类似于 cmdlet 类的对象或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。 Windows PowerShell 运行时使用返回的对象添加到参数`Set-Item`cmdlet。

此提供程序未实现此方法。 但是，以下代码是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitemdynamicparameters](Msh_samplestestcmdlets#testprovidersetitemdynamicparameters)]  -->

## <a name="clearing-an-item"></a>清除某一项

若要清除某个项，Windows PowerShell 项提供程序实现[System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)方法，以支持来自调用`Clear-Item`cmdlet。 此方法会清除指定路径处的数据项目。

此提供程序未实现此方法。 但是，以下代码是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitem](Msh_samplestestcmdlets#testproviderclearitem)]  -->

#### <a name="things-to-remember-about-implementing-clearitem"></a>要实现 ClearItem 记住的事项

以下条件可能适用于的实现[System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem):

- 在定义的提供程序类时，Windows PowerShell 项提供程序可能会从声明提供程序功能 ExpandWildcards、 筛选器、 包括或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下，实现[System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)必须确保传递给方法的路径是否满足这些要求。 若要执行此操作，该方法应访问相应的属性，例如，则[System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性。

- 默认情况下，重写此方法不应设置或写入对象，除非用户隐藏[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为`true`。 错误应发送到[System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)如果路径表示对用户隐藏的项的方法和[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)设置为`false`。

- 实现[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法应调用[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)，并向数据存储区进行任何更改之前验证它的返回值。 此方法用于更改数据存储，例如，删除文件时确认执行操作。 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)方法发送给用户，与 Windows PowerShell 运行时更改和处理的任何命令行设置或首选项的资源的名称确定应显示的内容中的变量。

  在调用[System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)返回`true`，则[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法应调用[System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法。 此方法将消息发送到用户允许反馈，以验证是否应继续执行该操作。 在调用[System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)允许具有潜在危险的系统修改为其他检查。

## <a name="retrieve-dynamic-parameters-for-clearitem"></a>检索 ClearItem 动态参数

有时`Clear-Item`cmdlet 需要在运行时动态指定的其他参数。 若要提供这些动态参数在 Windows PowerShell 项提供程序必须实现[System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters)方法。 此方法检索指定的路径处的项的动态参数并返回具有属性和字段与分析属性类似于 cmdlet 类的对象或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。 Windows PowerShell 运行时使用返回的对象添加到参数`Clear-Item`cmdlet。

此项提供程序未实现此方法。 但是，以下代码是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitemdynamicparameters](Msh_samplestestcmdlets#testproviderclearitemdynamicparameters)]  -->

## <a name="performing-a-default-action-for-an-item"></a>项执行默认操作

Windows PowerShell 项提供程序可以实现[System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)方法，以支持来自调用`Invoke-Item`cmdlet，后者允许提供程序到针对指定的路径处的项执行默认操作。 例如，FileSystem 提供程序可能会使用此方法要为特定项调用 ShellExecute。

此提供程序未实现此方法。 但是，以下代码是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultaction](Msh_samplestestcmdlets#testproviderinvokedefaultaction)]  -->

#### <a name="things-to-remember-about-implementing-invokedefaultaction"></a>要实现 InvokeDefaultAction 记住的事项

以下条件可能适用于的实现[System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction):

- 在定义的提供程序类时，Windows PowerShell 项提供程序可能会从声明提供程序功能 ExpandWildcards、 筛选器、 包括或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下，实现[System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)必须确保传递给方法的路径是否满足这些要求。 若要执行此操作，该方法应访问相应的属性，例如，则[System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性。

- 默认情况下，重写此方法不应设置或写入对象隐藏用户，除非[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为`true`。 错误应发送到[System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)如果路径表示对用户隐藏的项的方法和[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)设置为`false`。

## <a name="retrieve-dynamic-parameters-for-invokedefaultaction"></a>检索 InvokeDefaultAction 动态参数

有时`Invoke-Item`cmdlet 需要在运行时动态指定的其他参数。 若要提供这些动态参数在 Windows PowerShell 项提供程序必须实现[System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters)方法。 此方法检索指定的路径处的项的动态参数并返回具有属性和字段与分析属性类似于 cmdlet 类的对象或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。 Windows PowerShell 运行时使用返回的对象添加到的动态参数`Invoke-Item`cmdlet。

此项提供程序未实现此方法。 但是，以下代码是此方法的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters](Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters)]  -->

## <a name="implementing-helper-methods-and-classes"></a>实现帮助器方法和类

此项提供程序实现几个帮助器方法，并使用由公共类重写方法定义的 Windows PowerShell。 这些帮助器方法和类的代码所示[代码示例](#Code-Sample)部分。

### <a name="normalizepath-method"></a>NormalizePath 方法

此项提供程序实现 NormalizePath 帮助器方法，以确保该路径具有一致的格式。 指定的格式使用反斜杠 (\\) 作为分隔符。

### <a name="pathisdrive-method"></a>PathIsDrive 方法

此项提供程序实现一个 PathIsDrive 帮助器方法，以确定指定的路径是否实际的驱动器名称。

### <a name="chunkpath-method"></a>ChunkPath 方法

此项提供程序实现分解，以便该提供程序可以确定它的各个元素的指定路径的 ChunkPath 帮助器方法。 它将返回一个数组组成的路径元素。

### <a name="gettable-method"></a>GetTable 方法

此项提供程序实现返回一个 DatabaseTableInfo 对象，表示在调用中指定的表有关的信息的 GetTables 帮助器方法。

### <a name="getrow-method"></a>GetRow 方法

[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)的此项提供程序的方法调用 GetRows 帮助器方法。 此帮助器方法检索 DatabaseRowInfo 对象，表示表中的指定行的相关信息。

### <a name="databasetableinfo-class"></a>DatabaseTableInfo 类

此项提供程序定义 DatabaseTableInfo 类表示在数据库中的数据表中的信息的集合。 此类是类似于[System.IO.Directoryinfo](/dotnet/api/System.IO.DirectoryInfo)类。

示例项提供程序定义 DatabaseTableInfo.GetTables 方法，它返回数据库中定义表的表信息对象的集合。 此方法包括 try/catch 块，以确保，任何数据库错误显示为行与零个条目。

### <a name="databaserowinfo-class"></a>DatabaseRowInfo 类

此项提供程序定义表示数据库的表中的行的 DatabaseRowInfo 帮助器类。 此类是类似于[System.IO.FileInfo](/dotnet/api/System.IO.FileInfo)类。

示例提供程序定义一个 DatabaseRowInfo.GetRows 方法来返回指定表的行信息对象的集合。 此方法包括一个 try/catch 块来捕获的异常。 任何错误将导致在没有行信息。

## <a name="code-sample"></a>代码示例

有关完整的示例代码，请参阅[AccessDbProviderSample03 代码示例](./accessdbprovidersample03-code-sample.md)。

## <a name="defining-object-types-and-formatting"></a>定义对象类型和格式设置

当编写提供程序，它可能有必要，若要将成员添加到现有对象或定义新对象。 完成后，创建 Windows PowerShell 可用于标识对象的成员的类型文件和格式化文件，用于定义如何显示该对象。 有关详细信息，请参阅[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)。

## <a name="building-the-windows-powershell-provider"></a>生成 Windows PowerShell 提供程序

请参阅[如何注册 Cmdlet、 提供程序，和托管应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="testing-the-windows-powershell-provider"></a>测试 Windows PowerShell 提供程序

此 Windows PowerShell 项提供程序注册到 Windows PowerShell 中，只能测试基本和驱动器的提供程序的功能。 若要测试项的操作，还必须实现中所述的容器功能[实现容器 Windows PowerShell 提供程序](./creating-a-windows-powershell-container-provider.md)。

## <a name="see-also"></a>另请参阅

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 程序员指南](./windows-powershell-programmer-s-guide.md)

[创建 Windows PowerShell 提供程序](./how-to-create-a-windows-powershell-provider.md)

[设计您的 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)

[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Windows PowerShell 的工作原理](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[创建容器的 Windows PowerShell 提供程序](./creating-a-windows-powershell-container-provider.md)

[创建驱动器的 Windows PowerShell 提供程序](./creating-a-windows-powershell-drive-provider.md)

[如何注册 Cmdlet、 提供程序，和托管应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)