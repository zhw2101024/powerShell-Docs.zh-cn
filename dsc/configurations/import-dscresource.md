---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 使用 Import-DSCResource
ms.openlocfilehash: ee0b2f0469c6507c8f0148138198597a9e57cdd7
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/25/2019
ms.locfileid: "56803406"
---
# <a name="using-import-dscresource"></a>使用 Import-DSCResource

`Import-DScResource` 是只能在配置脚本块内使用的动态关键字。 `Import-DSCResource`关键字来导入你的配置中所需的任何资源。 下的资源`$pshome`将自动导入它仍被视为显式导入中使用的所有资源的最佳做法，但您[配置](Configurations.md)。

语法`Import-DSCResource`如下所示。  按名称指定模块，时，需要列出每个新行上。

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|参数  |说明  |
|---------|---------|
|`-Name`|必须导入 DSC 资源名称。 如果指定模块名称，该命令将搜索在此模块中; 这些 DSC 资源否则该命令在所有 DSC 资源路径中搜索的 DSC 资源。 支持使用通配符。|
|`-ModuleName`|模块名称或模块规范。  如果指定要从模块导入的资源，该命令将尝试导入的资源。 如果指定的模块仅，命令将导入模块中的所有 DSC 资源。|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>在配置的示例： 使用导入-DSCResource

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
> 不支持在同一命令中指定资源名称和模块名称的多个值。 它可以具有相同的资源存在多个模块中的情况下，从哪些模块加载哪些资源有关的非确定性行为。 以下命令将导致错误在编译过程。
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

使用仅 Name 参数时要考虑的事项：

- 它是资源密集型操作具体取决于计算机上安装的模块数量。
- 它将加载找到具有给定名称的第一个资源。 在这种情况中的多个具有相同名称安装资源，它可以加载错误的资源。

建议的用法是指定`–ModuleName`与`-Name`参数，如下所述。

这种用法具有以下优势：

- 它可减少性能造成影响限制搜索范围为指定的资源。
- 它显式定义的模块定义的资源，确保加载正确的资源。

> [!NOTE]
> 在 PowerShell 5.0 中，DSC 资源可以拥有多个版本，并且这些版本可以并行安装在计算机上。 这是通过将多个版本的资源模块包含在同一个模块文件夹中实现的。
> 有关详细信息，请参阅[使用具有多个版本的资源](sxsresource.md)。

## <a name="intellisense-with-import-dscresource"></a>使用导入 DSCResource 的 Intellisense

在创作时在 ISE 中的 DSC 配置，PowerShell 提供 IntelliSence 资源和资源属性。 在资源定义`$pshome`会自动加载模块路径。 导入使用的资源时`Import-DSCResource`关键字指定的资源定义添加和 Intellisense 扩展以包含导入的资源的架构。

![资源的 Intellisense](/media/resource-intellisense.png)

> [!NOTE]
> 从 PowerShell 5.0 开始，tab 自动补全已添加到 ISE 有关 DSC 资源及其属性。 有关详细信息，请参阅[资源](../resources/resources.md)。

在编译配置时，PowerShell 将使用导入的资源定义来验证配置中的所有资源块。
使用资源的架构定义的以下规则，验证每个资源块。

- 使用仅在架构中定义的属性。
- 每个属性的数据类型正确。
- 指定密钥属性。
- 不使用任何只读属性。
- 验证的值将类型映射。

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

Intellisense 和架构验证，可以在运行时避免复杂情况分析和编译时间，在捕获更多的错误。

> [!NOTE]
> 每个 DSC 资源可以具有一个名称，和一个**FriendlyName**由资源的架构定义。 以下是"MSFT_ServiceResource.shema.mof"的前两行。
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> 当在配置中使用此资源，可以指定**MSFT_ServiceResource**或**服务**。

## <a name="powershell-v4-and-v5-differences"></a>PowerShell v4 和 v5 差异

有多个差异在 PowerShell 4.0 vs 中创作配置时，将显示。PowerShell 5.0 及更高版本。 本部分将突出显示差异，您会看到与本文相关。

### <a name="multiple-resource-versions"></a>多个资源版本

在 PowerShell 4.0 中，不支持安装和使用的资源并排显示多个版本。 如果你注意到问题的资源导入你的配置，请确保只有一个版本安装的资源。

在下面的两个版本的映像**xPSDesiredStateConfiguration**安装模块。

![修复了多个资源版本](/media/multiple-resource-versions-broken.md)

将所需的模块版本的内容复制到模块目录的顶层。

![修复了多个资源版本](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a>资源位置

你的资源时创作和编译配置，可以存储在指定的任何目录中您[PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path)。 在 PowerShell 4.0 中，LCM 将要求要存储在"程序 Files\WindowsPowerShell\Modules"下的所有 DSC 资源模块或`$pshome\Modules`。 从 PowerShell 5.0 开始，此要求已被删除，并且可以指定任何目录中存储资源模块`PSModulePath`。

## <a name="see-also"></a>另请参阅

- [资源](../resources/resources.md)
