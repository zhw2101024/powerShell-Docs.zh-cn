---
title: Windows PowerShell 提供程序概述 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82244fbd-07b9-47f3-805c-3fb90ebbf58a
caps.latest.revision: 13
ms.openlocfilehash: 0d4addc0a064873701ae15c204dbd335f3374ab7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080895"
---
# <a name="windows-powershell-provider-overview"></a>Windows PowerShell 提供程序概述

Windows PowerShell 提供程序允许将任何数据存储，就好像已装载的驱动器进行公开与文件系统类似。 例如，内置的注册表提供程序，可像你可以导航导航注册表`c`您的计算机的驱动器。 一个提供程序还可以重写`Item`cmdlet (例如， `Get-Item`，`Set-Item`等)，以便可以将数据存储区中的数据视为文件并且导航文件系统时，将被视为目录。 有关提供程序和驱动器，以及在 Windows PowerShell 中的内置提供程序的详细信息，请参阅[about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)。

## <a name="providers-and-drives"></a>提供程序和驱动器

一个提供程序定义用于访问、 导航和编辑数据存储，而在驱动器中指定的提供程序定义的类型的指定入口点到数据存储区 （或数据存储区的一部分） 的逻辑。 例如，注册表提供程序可以访问配置单元和注册表中的密钥和 HKLM 和 HKCU 驱动器指定注册表中相应的配置单元。 HKLM 和 HKCU 驱动器这两个使用注册表提供程序。

当您编写一个提供程序时，可以指定默认驱动器驱动器提供程序可用时自动创建的。 您还可以定义用于创建使用该提供程序的新驱动器的方法。

## <a name="type-of-providers"></a>提供程序的类型

有几种类型的提供程序，其中每个提供不同级别的功能。 一个提供程序实现为类派生的后代之一[System.Management.Automation.Sessionstatecategory.Cmdletprovider](/dotnet/api/System.Management.Automation.SessionStateCategory.CmdletProvider)类。 有关不同类型的提供程序的信息，请参阅[提供程序类型](./provider-types.md)。

## <a name="provider-cmdlets"></a>提供程序 cmdlet

提供程序可以实现方法对应的 cmdlet，创建时为该提供程序在驱动器中使用这些 cmdlet 的自定义行为。 具体取决于提供程序的类型，提供了不同的 cmdlet 集。 有关可用于自定义提供程序中的 cmdlet 的完整列表，请参阅[提供程序 cmdlet](./provider-cmdlets.md)。

## <a name="provider-paths"></a>提供程序路径

用户导航文件系统一样的提供程序驱动器。 因此，他们希望要对应于文件系统导航中使用的路径的路径的语法。 当用户运行提供程序 cmdlet 时，它们指定要访问的项的路径。 可以多种方式解释指定的路径。 提供程序应支持一个或多个以下的路径类型。

### <a name="drive-qualified-paths"></a>驱动器限定路径

驱动器限定的路径是项名称、 容器和子容器中的项所在，并通过其访问项的 Windows PowerShell 驱动器的组合。 （驱动器定义用于访问数据存储区提供程序。 此路径的开头使用驱动器名称后接一个冒号 （:）。 例如：`get-childitem C:`

### <a name="provider-qualified-paths"></a>提供程序限定路径

若要允许 Windows PowerShell 引擎初始化和取消初始化您的提供程序，该提供程序必须支持的提供程序限定路径。 例如，用户可以初始化和取消初始化 FileSystem 提供程序，因为它定义了以下提供程序限定路径： `FileSystem::\\uncshare\abc\bar`。

### <a name="provider-direct-paths"></a>提供程序直接路径

若要允许远程访问 Windows PowerShell 提供程序，它应支持的提供程序直接路径要直接传递到 Windows PowerShell 提供程序为当前的位置。 例如，可以使用注册表的 Windows PowerShell 提供程序`\\server\regkeypath`作为提供程序直接路径。

### <a name="provider-internal-paths"></a>提供程序内部的路径

若要允许使用 Windows PowerShell 应用程序编程接口 (Api) 访问数据的提供程序 cmdlet，Windows PowerShell 提供程序应支持的提供程序内部的路径。 此路径指示后"::"中的提供程序限定路径。 例如，文件系统的 Windows PowerShell 提供程序的提供程序内部路径是`\\uncshare\abc\bar`。

## <a name="overriding-cmdlet-parameters"></a>重写 cmdlet 参数

由提供程序可以重写的某些特定于提供程序的 cmdlet 的行为。 可以重写的参数的列表以及如何在提供程序类中重写它们，请参阅[提供程序 cmdlet 参数](./provider-cmdlet-parameters.md)

## <a name="dynamic-parameters"></a>动态参数

提供程序可以定义当用户指定一个 cmdlet 的静态参数的值会添加到提供程序 cmdlet 的动态参数。 一个提供程序通过实现一个或多个动态参数方法执行此操作。 Cmdlet 可用于添加动态参数，以及用于实现它们的方法的参数的列表，请参阅[提供程序 cmdlet 的动态参数](./provider-cmdlet-dynamic-parameters.md)。

## <a name="provider-capabilities"></a>提供程序的功能

[System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举定义的提供程序可以支持的功能数。 其中包括使用通配符、 筛选器项和支持事务的功能。 若要指定提供程序的功能，请添加一系列的值[System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)枚举，与逻辑组合`OR`操作，作为[System.Management.Automation.Provider.Cmdletproviderattribute.Providercapabilities*](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities)属性 （该属性的第二个参数） 的[System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)提供程序类的属性。 例如，以下属性指定的提供程序支持[System.Management.Automation.Provider.Providercapabilities.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities.ShouldProcess)和[System.Management.Automation.Provider.Providercapabilities.Transactions](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities.Transactions)功能。

```csharp
[CmdletProvider(RegistryProvider.ProviderName, ProviderCapabilities.ShouldProcess | ProviderCapabilities.Transactions)]

```

## <a name="provider-cmdlet-help"></a>提供程序 cmdlet 帮助

当编写提供程序，可以实现您自己支持的提供程序 cmdlet 的帮助。 这包括适用于每个提供程序 cmdlet 或多个版本帮助主题的情况下提供程序 cmdlet 的作用根据动态参数使用不同的单个帮助主题。 若要支持提供程序特定于 cmdlet 的帮助，您的提供程序必须实现[System.Management.Automation.Provider.Icmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp)接口。

Windows PowerShell 引擎调用[System.Management.Automation.Provider.Icmdletprovidersupportshelp.Gethelpmaml*](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml)方法以显示提供程序 cmdlet 的帮助主题。 引擎提供了用户在运行时指定该 cmdlet 的名称`Get-Help`cmdlet 和用户的当前路径。 如果您的提供程序实现了不同版本的同一提供程序 cmdlet 对不同的驱动器，则需要使用当前路径。 该方法必须返回一个字符串，包含于 cmdlet 帮助的 XML。

使用 PSMAML XML 写入的帮助文件的内容。 这是用于编写针对独立 cmdlet 的帮助内容的相同 XML 架构。 添加自定义 cmdlet 帮助您的提供程序的帮助文件的内容在`CmdletHelpPaths`元素。 下面的示例演示`command`单个提供程序 cmdlet，和它的元素将显示如何指定提供程序 cmdlet 的名称，您的提供程序。 支持

```xml
<CmdletHelpPaths>
  <command:command>
    <command:details>
      <command:name>ProviderCmdletName</command:name>
      <command:verb>Verb</command:verb>
      <command:noun>Noun</command:noun>
    <command:details>
  </command:command>
<CmdletHelpPath>
```

## <a name="see-also"></a>另请参阅

[Windows PowerShell 提供程序功能](./provider-types.md)

[提供程序 Cmdlet](./provider-cmdlets.md)

[编写 Windows PowerShell 提供程序](./writing-a-windows-powershell-provider.md)