---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 使用 Import-DSCResource
ms.openlocfilehash: ee0b2f0469c6507c8f0148138198597a9e57cdd7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080095"
---
# <a name="using-import-dscresource"></a>使用 Import-DSCResource

`Import-DScResource` 是只能在配置脚本块内使用的动态关键字。 用于导入配置中所需的任何资源的 `Import-DSCResource` 关键字。 `$pshome` 下的资源是自动导入的，但显式导入[配置](Configurations.md)中使用的所有资源仍被视为是最佳做法。

`Import-DSCResource` 的语法如下所示。  按名称指定模块时，要求在新行中列出每个模块。

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|参数  |说明  |
|---------|---------|
|`-Name`|必须导入的 DSC 资源名称。 如果指定了模块名称，命令将在该模块中搜索这些 DSC 资源；否则，命令将在所有 DSC 资源路径中搜索 DSC 资源。 支持使用通配符。|
|`-ModuleName`|模块名称或模块规范。  如果指定要从模块导入的资源，该命令将尝试只导入这些资源。 如果仅指定模块，则命令将导入模块中的所有 DSC 资源。|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>例如：在配置中使用 Import-DSCResource

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry
    
    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    Import-DSCResource -ModuleName ComputerManagementDsc
...
```

> [!NOTE]
> 不支持在同一命令中为资源名称和模块名称指定多个值。 当相同的资源存在于多个模块中时，可能会存在从哪个模块加载哪个资源的非确定性行为。 下面的命令将在编译期间导致错误。
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

仅使用 Name 参数时要考虑的事项：

- 它是一种资源密集型操作，具体取决于安装在计算机上的模块数量。
- 它将加载使用给定名称找到的第一个资源。 如果安装了多个具有相同名称的资源，则可能加载错误资源。

建议的用法是使用 `-Name` 参数指定 `–ModuleName`，如下所述。

这种用法具有以下优势：

- 它通过限制指定资源的搜索范围来降低性能影响。
- 它显式定义定义资源的模块，以确保加载正确资源。

> [!NOTE]
> 在 PowerShell 5.0 中，DSC 资源可以拥有多个版本，并且这些版本可以并行安装在计算机上。 这是通过将多个版本的资源模块包含在同一个模块文件夹中实现的。
> 有关详细信息，请参阅[使用具有多个版本的资源](sxsresource.md)。

## <a name="intellisense-with-import-dscresource"></a>Intellisense 与 Import-DSCResource

在 ISE 中编写 DSC 配置时，PowerShell 为资源和资源属性提供 IntelliSence。 `$pshome` 模块路径下的资源定义将自动加载。 当使用 `Import-DSCResource` 关键字导入资源时，将添加指定的资源定义，并扩展 Intellisense 以包含导入的资源架构。

![资源 Intellisense](/media/resource-intellisense.png)

> [!NOTE]
> 从 PowerShell 5.0 开始，已将 Tab 自动补全添加到 DSC 资源及其属性的 ISE 中。 有关详细信息，请参阅[资源](../resources/resources.md)。

在编译配置时，PowerShell 使用导入的资源定义来验证配置中的所有资源块。
根据以下规则，使用资源的架构定义对每个资源块进行验证。

- 仅使用架构中定义的属性。
- 每个属性的数据类型均正确无误。
- 指定键属性。
- 不使用只读属性。
- 验证值映射类型。

请考虑以下配置：

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

编译此配置会导致错误。

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

Intellisense 和架构验证允许在解析和编译期间捕获更多错误，从而避免了运行时的复杂性。

> [!NOTE]
> 每个 DSC 资源都可以有一个名称，以及一个由资源架构定义的 FriendlyName。 下面是“MSFT_ServiceResource.shema.mof”的前两行。
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> 在配置中使用此资源时，可以指定 MSFT_ServiceResource 或 Service。

## <a name="powershell-v4-and-v5-differences"></a>PowerShell v4 和 v5 差异

你会发现，在 PowerShell 4.0 中编写配置与在 PowerShell 5.0 及更高版本中编写配置有许多不同之处。 本节将重点介绍你所看到的与本文相关的差异。

### <a name="multiple-resource-versions"></a>多个资源版本

PowerShell 4.0 不支持同时安装和使用多个资源版本。 如果注意到将资源导入配置时存在问题，请确保只安装一个资源版本。

在下图中，安装了两个版本的 xPSDesiredStateConfiguration 模块。

![修复了多个资源版本](/media/multiple-resource-versions-broken.md)

将所需模块版本的内容复制到模块目录的顶层。

![修复了多个资源版本](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a>资源位置

在编写和编译配置时，资源可以存储在 [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path) 指定的任何目录中。 在 PowerShell 4.0 中，LCM 要求所有 DSC 资源模块都存储在“Program Files\WindowsPowerShell\Modules”或 `$pshome\Modules` 下。 从 PowerShell 5.0 开始，此要求已被删除，资源模块可以存储在 `PSModulePath` 指定的任何目录中。

## <a name="see-also"></a>另请参阅

- [资源](../resources/resources.md)
