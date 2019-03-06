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
ms.openlocfilehash: 4ed15dabffa933dee9becf2f839887eb9108775d
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57430003"
---
# <a name="creating-a-windows-powershell-property-provider"></a>创建 Windows PowerShell 属性提供程序

本主题介绍如何创建提供程序，使用户用来处理数据存储区中的项的属性。 因此，这种类型的提供程序被称为 Windows PowerShell 属性提供程序。 例如，注册表提供程序提供的 Windows PowerShell 句柄注册表项值作为注册表项的属性。 这种类型的提供程序必须添加[System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) .NET 类的实现的接口。

> [!NOTE]
> Windows PowerShell 提供了可用于开发 Windows PowerShell 提供程序的模板文件。 TemplateProvider.cs 文件是适用于 Microsoft Windows 软件开发工具包适用于 Windows Vista 和.NET Framework 3.0 运行时组件。 有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。
>
> 下载的模板现已推出 **\<PowerShell 示例 >** 目录。 应使此文件的副本并使用该副本进行创建新的 Windows PowerShell 提供程序，删除不需要任何功能。
>
> 有关其他 Windows PowerShell 提供程序实现的详细信息，请参阅[设计你 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)。

> [!CAUTION]
> 属性提供程序的方法应编写使用的任何对象[System.Management.Automation.Provider.Cmdletprovider.Writepropertyobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject)方法。

以下列表包含本主题中的部分。 如果您不熟悉编写 Windows PowerShell 属性提供程序，读取此信息显示的顺序。 但是，如果你熟悉编写 Windows PowerShell 属性提供程序，请直接转到所需的信息。

- [定义 Windows PowerShell 提供程序](#Defining-the-Windows-PowerShell-provider)

- [定义基本功能](#Defining-Base-Functionality)

- [检索属性](#Retrieving-Properties)

- [附加到的动态参数`Get-ItemProperty`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-ItemProperty-Cmdlet)

- [设置属性](#Setting-Properties)

- [附加到的动态参数`Set-ItemProperty`Cmdlet](#Attaching-Dynamic-Parameters-for-the-Set-ItemProperty-Cmdlet)

- [清除属性](#Clearing-Properties)

- [附加到的动态参数`Clear-ItemProperty`Cmdlet](#Attaching-Dynamic-Parameters-to-the-Clear-ItemProperty-Cmdlet)

- [生成 Windows PowerShell 提供程序](#Building-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-provider"></a>定义 Windows PowerShell 提供程序

属性提供程序必须创建一个支持的.NET 类[System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)接口。 下面是从 Windows powershell 提供的 TemplateProvider.cs 文件的默认类声明。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>定义基本功能

[System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)接口可以附加到任何提供程序基类除[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)类。 添加所需的基本类使用的基本功能。 有关基类的详细信息，请参阅[设计你 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)。

## <a name="retrieving-properties"></a>检索属性

若要检索属性，该提供程序必须实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)方法，以支持来自调用`Get-ItemProperty`cmdlet。 此方法检索位于指定的提供程序内部路径 （完全限定的） 处的项的属性。

`providerSpecificPickList`参数指示要检索的属性。 如果此参数为`null`或为空，该方法应检索的所有属性。 此外， [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)的实例将写入[System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject)表示的对象检索到的属性的属性包。 该方法应返回任何内容。

建议的实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)选取列表中支持的每个元素的属性名的通配符扩展。 若要执行此操作，请使用[System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern)类来执行通配符模式匹配。

下面是的默认实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) TemplateProvider.cs 文件提供的 Windows PowerShell 中。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>要实现 GetProperty 记住的事项

以下条件可能适用于特定的实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty):

- 在定义的提供程序类时，Windows PowerShell 属性提供程序可能会从声明提供程序功能 ExpandWildcards、 筛选器、 包括或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下，实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)方法需要确保传递给方法的路径满足指定的要求功能。 若要执行此操作，该方法应访问相应的属性，例如，则[System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性。

- 默认情况下，重写此方法应检索除非用户隐藏的对象的读取器[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为`true`。 如果路径表示对用户隐藏的项写入错误和[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)设置为`false`。

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>附加到的 Get-itemproperty Cmdlet 的动态参数

`Get-ItemProperty` Cmdlet 可能需要在运行时动态指定的附加参数。 若要提供这些动态参数，Windows PowerShell 属性提供程序必须实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)方法。 `path`参数指示的完全限定提供程序内部路径，而`providerSpecificPickList`参数指定输入命令行上的特定于提供程序的属性。 此参数可能是`null`或为空，如果属性传递给 cmdlet。 在这种情况下，此方法返回具有属性和字段与分析属性类似于 cmdlet 类的对象或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。 Windows PowerShell 运行时使用返回的对象将参数添加到 cmdlet。

下面是的默认实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) TemplateProvider.cs 文件提供的 Windows PowerShell 中。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>设置属性

若要设置的属性，Windows PowerShell 属性提供程序必须实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)方法，以支持来自调用`Set-ItemProperty`cmdlet。 此方法在指定的路径，设置项的一个或多个属性，并覆盖所需的提供的属性。 [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)还将写入的实例[System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject)对象，表示更新后的一个属性包属性。

下面是的默认实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) TemplateProvider.cs 文件提供的 Windows PowerShell 中。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>要实现 Set-itemproperty 记住的事项

以下条件可能适用于的实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty):

- 在定义的提供程序类时，Windows PowerShell 属性提供程序可能会从声明提供程序功能 ExpandWildcards、 筛选器、 包括或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下，实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)方法必须确保传递给方法的路径满足指定的要求功能。 若要执行此操作，该方法应访问相应的属性，例如，则[System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性。

- 默认情况下，重写此方法应检索除非用户隐藏的对象的读取器[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为`true`。 如果路径表示对用户隐藏的项写入错误和[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)设置为`false`。

- 实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)方法应调用[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)和到数据存储进行任何更改之前验证它的返回值。 此方法用于确认操作的执行时更改为系统状态，例如，重命名文件。 [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)发送要更改为具有 Windows PowerShell 运行时，可处理任何命令行设置或首选项变量中的用户的资源的名称确定应显示的内容。

  在调用[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)返回`true`，则可以进行具有潜在危险的系统修改， [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)方法应调用[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法。 此方法将一条确认消息发送到用户允许其他反馈，以指示应继续执行该操作。

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>Set-itemproperty cmdlet 附加动态参数

`Set-ItemProperty` Cmdlet 可能需要在运行时动态指定的附加参数。 若要提供这些动态参数，Windows PowerShell 属性提供程序必须实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)方法。 此方法返回具有属性和字段与分析属性类似于 cmdlet 类的对象或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。 `null`可以返回值，如果不不添加任何动态参数。

下面是的默认实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) TemplateProvider.cs 文件提供的 Windows PowerShell 中。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>清除属性

若要清除的属性，Windows PowerShell 属性提供程序必须实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)方法，以支持来自调用`Clear-ItemProperty`cmdlet。 此方法设置位于指定路径处的项的一个或多个属性。

下面是的默认实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) TemplateProvider.cs 文件提供的 Windows PowerShell 中。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>请记住有关实现 ClearProperty

以下条件可能适用于特定的实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty):

- 在定义的提供程序类时，Windows PowerShell 属性提供程序可能会从声明提供程序功能 ExpandWildcards、 筛选器、 包括或排除， [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举。 在这些情况下，实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)方法需要确保传递给方法的路径满足指定的要求功能。 若要执行此操作，该方法应访问相应的属性，例如，则[System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude)和[System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)属性。

- 默认情况下，重写此方法应检索除非用户隐藏的对象的读取器[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)属性设置为`true`。 如果路径表示对用户隐藏的项写入错误和[System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force)设置为`false`。

- 实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)方法应调用[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)和到数据存储进行任何更改之前验证它的返回值。 此方法用于更改系统状态，例如清除内容之前确认执行操作。 [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)发送要更改对用户来说，与 Windows PowerShell 运行时将考虑在内的任何命令行设置或首选项变量中的资源的名称确定应显示的内容。

  在调用[System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)返回`true`，则可以进行具有潜在危险的系统修改， [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)方法应调用[System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)方法。 此方法将一条确认消息发送到用户允许其他反馈，以指示应继续执行该具有潜在危险的操作。

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>附加到 Clear-itemproperty Cmdlet 的动态参数

`Clear-ItemProperty` Cmdlet 可能需要在运行时动态指定的附加参数。 若要提供这些动态参数，Windows PowerShell 属性提供程序必须实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)方法。 此方法返回具有属性和字段与分析属性类似于 cmdlet 类的对象或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)对象。 `null`可以返回值，如果不不添加任何动态参数。

下面是的默认实现[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) TemplateProvider.cs 文件提供的 Windows PowerShell 中。

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>生成 Windows PowerShell 提供程序

请参阅[如何注册 Cmdlet、 提供程序，和托管应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)。

## <a name="see-also"></a>另请参阅

[Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)

[设计您的 Windows PowerShell 提供程序](./designing-your-windows-powershell-provider.md)

[扩展对象类型和格式设置](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[如何注册 Cmdlet、 提供程序，和托管应用程序](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)