---
title: 创建 Windows PowerShell 属性提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- property providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], property provider
ms.assetid: a6adca44-b94b-4103-9970-a9b414355e60
caps.latest.revision: 5
ms.openlocfilehash: c36b93a5b4d3e7ef92d7f5b16381a8def2dd5466
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323102"
---
# <a name="creating-a-windows-powershell-property-provider"></a>创建 Windows PowerShell 属性提供程序

本主题介绍如何创建一个提供程序，该提供程序使用户能够操作数据存储区中的项的属性。 因此，这种类型的提供程序称为 Windows PowerShell 属性提供程序。 例如，Windows PowerShell 提供的注册表提供程序将注册表项值作为该注册表项的属性进行处理。 这种类型的提供程序必须将[Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)接口添加到 .net 类的实现。

> [!NOTE]
> Windows PowerShell 提供了一个可用于开发 Windows PowerShell 提供程序的模板文件。 TemplateProvider.cs 文件位于适用于 Windows Vista 的 Microsoft Windows 软件开发工具包和 .NET Framework 3.0 运行时组件中。 有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> > Directory 中的 **\<PowerShell 示例**中提供了下载的模板。 应创建此文件的副本，并使用该副本创建新的 Windows PowerShell 提供程序，删除不需要的任何功能。
>
> 有关其他 Windows PowerShell 提供程序实现的详细信息，请参阅[设计 Windows Powershell 提供程序](./designing-your-windows-powershell-provider.md)。

> [!CAUTION]
> 您的属性提供程序的方法应使用[Cmdletprovider. Writepropertyobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject)方法编写任何对象。

## <a name="defining-the-windows-powershell-provider"></a>定义 Windows PowerShell 提供程序

属性提供程序必须创建一个支持[Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)接口的 .net 类。 下面是 Windows PowerShell 提供的 TemplateProvider.cs 文件中的默认类声明。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>定义基本功能

可以将[Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)接口附加到任何提供程序基类，但[Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类除外，这种情况下，可能会出现这种情况。 添加所使用的基类所需的基本功能。 有关基类的详细信息，请参阅[设计 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)。

## <a name="retrieving-properties"></a>检索属性

若要检索属性，提供程序必须实现[Ipropertycmdletprovider. Getproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)方法，以支持来自 cmdlet 的`Get-ItemProperty`调用。 此方法检索位于指定提供程序-内部路径（完全限定）中的项的属性。

`providerSpecificPickList`参数指示要检索的属性。 如果此参数为`null`或空，则该方法应检索所有属性。 此外， [Ipropertycmdletprovider. Getproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)将写入表示检索到的属性的属性包的[对象的](/dotnet/api/System.Management.Automation.PSObject)实例中的一个实例。 方法应不返回任何内容。

建议为选取列表中的每个元素的属性名称提供通配符扩展。 [Ipropertycmdletprovider. Getproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)的实现。 为此，请使用[Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern)类来执行通配符模式匹配。

下面是 Windows PowerShell 提供的 TemplateProvider.cs 文件中的[Ipropertycmdletprovider. Getproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>有关实现 GetProperty 的注意事项

以下情况可能适用于你的[Ipropertycmdletprovider. Getproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)实现：

- 定义提供程序类时，Windows PowerShell 属性提供程序可能会声明 ExpandWildcards、Filter、Include 或 Exclude 的提供程序功能， [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下， [Ipropertycmdletprovider. Getproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)方法的实现需要确保传递给方法的路径满足指定的功能的要求。）。 若要执行此操作，方法应访问相应的属性，例如， [Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性中的相应属性，例如 ""。

- 默认情况下，除非[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为`true`，否则此方法的重写不应检索用户隐藏的对象的读取器。 如果路径表示从用户和[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)中隐藏的项被设置为`false`，则应将错误写入错误。

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>将动态参数附加到 Set-itemproperty Cmdlet

`Get-ItemProperty` Cmdlet 可能需要在运行时动态指定的其他参数。 为了提供这些动态参数，Windows PowerShell 属性提供程序必须实现[Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)方法。 参数指示完全限定的提供程序内部路径， `providerSpecificPickList`而参数指定在命令行上输入的特定于提供程序的属性。 `path` 如果将属性传递`null`给 cmdlet，则此参数可以为或空。 在这种情况下，此方法将返回一个对象，该对象具有与 cmdlet 类或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象类似的分析特性的属性和字段。 Windows PowerShell 运行时使用返回的对象将参数添加到 cmdlet。

下面是 Windows PowerShell 提供的 TemplateProvider.cs 文件中的[Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>设置属性

若要设置属性，Windows PowerShell 属性提供程序必须实现[Ipropertycmdletprovider *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)方法，以支持来自 cmdlet 的`Set-ItemProperty`调用。 此方法设置指定路径处的项的一个或多个属性，并根据需要覆盖提供的属性。 [Ipropertycmdletprovider *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)还会写入一个表示已更新属性的属性包的[system.servicemodel 对象的](/dotnet/api/System.Management.Automation.PSObject)实例，该对象表示更新后的属性的属性包。

下面是由 Windows PowerShell 提供的 TemplateProvider.cs 文件中的[Ipropertycmdletprovider *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)的默认实现方式。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>有关实现 Set-itemproperty 的注意事项

以下情况可能适用于[Ipropertycmdletprovider *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)的实现：：（）

- 定义提供程序类时，Windows PowerShell 属性提供程序可能会声明 ExpandWildcards、Filter、Include 或 Exclude 的提供程序功能， [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下， [Ipropertycmdletprovider *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)方法的实现必须确保传递给该方法的路径满足指定功能的要求。）。 若要执行此操作，方法应访问相应的属性，例如， [Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性中的相应属性，例如 ""。

- 默认情况下，除非[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为`true`，否则此方法的重写不应检索用户隐藏的对象的读取器。 如果路径表示从用户和[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)中隐藏的项被设置为`false`，则应将错误写入错误。

- 你的[Ipropertycmdletprovider *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)方法的实现应调用[Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) ，并验证其返回值是否为 ""。在对数据存储进行任何更改之前。 此方法用于在对系统状态进行更改时（例如，重命名文件）确认操作的执行。 [Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)发送要更改为用户的资源的名称，以及 Windows PowerShell 运行时和处理任何命令行设置或首选项变量，以确定应显示。

  在对[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)的调用返回`true`后，如果可以进行潜在的危险系统修改，则[Ipropertycmdletprovider *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)方法应调用[Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法的调用者的方法的调用者。 此方法向用户发送一条确认消息，以允许其他反馈指示该操作应继续。

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>为 Set-itemproperty Cmdlet 附加动态参数

`Set-ItemProperty` Cmdlet 可能需要在运行时动态指定的其他参数。 为了提供这些动态参数，Windows PowerShell 属性提供程序必须实现[Ipropertycmdletprovider. Setpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)方法。 此方法返回一个对象，该对象具有与 cmdlet 类或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象类似的分析特性的属性和字段。 如果`null`未添加任何动态参数，则可以返回值。

下面是 Windows PowerShell 提供的 TemplateProvider.cs 文件中的[Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>清除属性

若要清除属性，Windows PowerShell 属性提供程序必须实现[Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)方法，以支持来自 cmdlet 的`Clear-ItemProperty`调用。 此方法设置位于指定路径的项的一个或多个属性。

下面是 Windows PowerShell 提供的 TemplateProvider.cs 文件中的[Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>要记住如何实现 ClearProperty

以下情况可能适用于你的[Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)实现：

- 定义提供程序类时，Windows PowerShell 属性提供程序可能会声明 ExpandWildcards、Filter、Include 或 Exclude 的提供程序功能， [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下， [Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)方法的实现需要确保传递给方法的路径满足指定的功能的要求。）。 若要执行此操作，方法应访问相应的属性，例如， [Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性中的相应属性，例如 ""。

- 默认情况下，除非[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为`true`，否则此方法的重写不应检索用户隐藏的对象的读取器。 如果路径表示从用户和[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)中隐藏的项被设置为`false`，则应将错误写入错误。

- 你的 Ipropertycmdletprovider 的实现应调用[Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)方法，并验证其返回值是否为 " [Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) "。在对数据存储进行任何更改之前。 此方法用于在更改系统状态之前确认操作的执行，例如清除内容。 [Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)发送要更改为用户的资源的名称，并且 Windows PowerShell 运行时将考虑任何命令行设置或首选项变量，以确定应显示的内容。

  在对[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)的调用返回`true`后，如果可以进行潜在的危险系统修改，则[Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)方法应调用[Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法的调用者的功能。 此方法会向用户发送一条确认消息，以允许其他反馈指示应该继续进行潜在的危险操作。

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>将动态参数附加到 Set-itemproperty Cmdlet

`Clear-ItemProperty` Cmdlet 可能需要在运行时动态指定的其他参数。 为了提供这些动态参数，Windows PowerShell 属性提供程序必须实现[Ipropertycmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)方法。 此方法返回一个对象，该对象具有与 cmdlet 类或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象类似的分析特性的属性和字段。 如果`null`未添加任何动态参数，则可以返回值。

下面是 Windows PowerShell 提供的 TemplateProvider.cs 文件中的[Ipropertycmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)的默认实现。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>生成 Windows PowerShell 提供程序

请参阅[如何注册 cmdlet、提供程序和主机应用程序](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="see-also"></a>请参阅

[Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)

[设计你的 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)

[扩展对象类型和格式](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[如何注册 Cmdlet、提供程序和主机应用程序](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)