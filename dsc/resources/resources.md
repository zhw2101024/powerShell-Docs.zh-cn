---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: DSC 资源
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046685"
---
# <a name="dsc-resources"></a>DSC 资源

>适用于：Windows PowerShell 4.0 中，Windows PowerShell 5.0

Desired State Configuration (DSC) 资源为 DSC 配置提供构建基块。 资源公开可配置的属性（架构），并包含本地配置管理器 (LCM) 调用以“使其如此”的 PowerShell 脚本函数。

资源的建模对象可以是一般的文件或 Windows 进程，也可以是具体的 IIS 服务器设置。  资源等组被组合成为 DSC 模块，模块将全部所需文件组织成为一个可移植结构，该结构包含标志资源既定用途的元数据。

每个资源都有 * 确定使用中的资源所需的语法的架构[配置](../configurations/configurations.md)。 可以按以下方式定义资源的架构：

- **Schema.Mof**文件：最多的资源定义其*架构*中 schema.mof 文件，请使用[托管对象格式](/windows/desktop/wmisdk/managed-object-format--mof-)。
- **'\<资源名称\>。 schema.psm1**文件：[复合资源](../configurations/compositeConfigs.md)定义其*架构*中<ResourceName>。 schema.psm1 文件中使用[参数块](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters)。
- **'\<资源名称\>.psm1**文件：基于的 DSC 资源定义的类及其*架构*类定义中。 语法项表示为类的属性。 有关详细信息，请参阅[about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)。

若要检索的 DSC 资源的语法，请使用[Get-dscresource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet 与`-Syntax`参数。 这种用法是使用类似[Get-command](/powershell/module/microsoft.powershell.core/get-command)与`-Syntax`参数，以获取 cmdlet 的语法。 您所看到的输出将显示你指定的资源的资源块中使用的模板。

```powershell
Get-DscResource -Syntax Service
```

尽管此资源的语法可能会在将来更改，您所看到的输出应类似于下面的输出。 喜欢的 cmdlet 语法*密钥*方括号中所示，都是可选的。 类型指定每个密钥需要的数据的类型。

> [!NOTE]
> **确保**密钥是可选的因为它默认为"Present"。

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

在配置**服务**资源块可能如下所示向**确保**后台处理程序服务是否正在运行。

> [!NOTE]
> 之前在配置中使用的资源，你必须使用导入[Import-dscresource](../configurations/import-dscresource.md)。

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

配置可以包含相同的资源类型的多个实例。 每个实例必须具有唯一名称。 在以下示例中，第二个**服务**资源块已添加用于配置"DHCP"服务。

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> 从 PowerShell 5.0 开始，intellisense 添加了对 DSC。 这一新功能，可使用\<选项卡\>并\<Ctrl + 空格键\>到自动补全键名。

![资源 Tab 自动补全](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a>内置资源

除了社区资源，还有适用于 Windows、 Linux、 资源和资源的跨节点依赖关系内置资源。 可以使用上述步骤以确定这些资源以及如何使用它们的语法。 这些资源提供服务的页面已存档下**引用**。

Windows 内置资源

* [存档资源](../reference/resources/windows/archiveResource.md)
* [环境资源](../reference/resources/windows/environmentResource.md)
* [文件资源](../reference/resources/windows/fileResource.md)
* [组资源](../reference/resources/windows/groupResource.md)
* [GroupSet 资源](../reference/resources/windows/groupSetResource.md)
* [日志资源](../reference/resources/windows/logResource.md)
* [包资源](../reference/resources/windows/packageResource.md)
* [ProcessSet 资源](../reference/resources/windows/ProcessSetResource.md)
* [注册表资源](../reference/resources/windows/registryResource.md)
* [脚本资源](../reference/resources/windows/scriptResource.md)
* [服务资源](../reference/resources/windows/serviceResource.md)
* [ServiceSet 资源](../reference/resources/windows/serviceSetResource.md)
* [用户资源](../reference/resources/windows/userResource.md)
* [WindowsFeature 资源](../reference/resources/windows/windowsFeatureResource.md)
* [WindowsFeatureSet 资源](../reference/resources/windows/windowsFeatureSetResource.md)
* [WindowsOptionalFeature 资源](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [WindowsOptionalFeatureSet 资源](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [WindowsPackageCabResource 资源](../reference/resources/windows/windowsPackageCabResource.md)
* [WindowsProcess 资源](../reference/resources/windows/windowsProcessResource.md)

[跨节点依赖关系](../configurations/crossNodeDependencies.md)资源

* [WaitForAll 资源](../reference/resources/windows/waitForAllResource.md)
* [WaitForSome 资源](../reference/resources/windows/waitForSomeResource.md)
* [WaitForAny 资源](../reference/resources/windows/waitForAnyResource.md)

包管理资源

* [PackageManagement 资源](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [PackageManagementSource 资源](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

Linux 资源

* [Linux 存档资源](../reference/resources/linux/lnxArchiveResource.md)
* [Linux 环境资源](../reference/resources/linux/lnxEnvironmentResource.md)
* [Linux FileLine 资源](../reference/resources/linux/lnxFileLineResource.md)
* [Linux 文件资源](../reference/resources/linux/lnxFileResource.md)
* [Linux 组资源](../reference/resources/linux/lnxGroupResource.md)
* [Linux 包资源](../reference/resources/linux/lnxPackageResource.md)
* [Linux 脚本资源](../reference/resources/linux/lnxScriptResource.md)
* [Linux 服务资源](../reference/resources/linux/lnxServiceResource.md)
* [Linux SshAuthorizedKeys 资源](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [Linux 用户资源](../reference/resources/linux/lnxUserResource.md)
