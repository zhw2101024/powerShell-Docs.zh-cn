---
ms.date: 12/12/2018
keywords: dsc,powershell,资源,库,安装程序
title: 安装其他 DSC 资源
ms.openlocfilehash: 7a6a935349358e11a77d2f00c0bf88e0ad18c097
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417797"
---
# <a name="install-additional-dsc-resources"></a>安装其他 DSC 资源

PowerShell 包括 Desired State Configuration (DSC) 的多个现成资源。  PSDesiredStateConfiguration 模块包含特定 PowerShell 实例上可用的所有 OOB DSC 资源。

这是包含在 PowerShell 4.0 中的 OOB 资源的列表以及资源功能的说明。

> [!NOTE]
> 此列表不完整，因为每个 PowerShell 版本都会增加 OOB 资源的数量。

|资源  |说明  |
|---------|---------|
|**文件**|控制文件和目录的状态。 将文件从“源”  复制到“目标”  ，然后在通过比较日期、校验和以及哈希确认“源”  发生更改时更新这些文件。|
|**存档**|在指定位置解压缩存档。 使用指定校验和验证存档  。|
|**环境**|管理环境变量。|
|**组**|管理本地组并控制组成员身份。|
|**日志**|将消息写入 `Microsoft-Windows-Desired State Configuration/Analytic` 事件日志。|
|**包**|使用 Arguments  、LogPath  、ReturnCode  和其他设置安装或卸载包。|
|**注册表**|管理注册表项和值。|
|**脚本**|可用于设计自己的 [get-test-set](../resources/get-test-set.md) 脚本块。|
|**服务**|配置 Windows 服务。|
|**用户** |管理本地用户和属性。|
|**WindowsFeature**|管理角色和功能。|
|**WindowsProcess**|配置 Windows 进程。|

OOB 资源可为常见操作提供良好起点。 如果 OOB 资源不能满足你的需求，则可以写入自己的[自定义资源](../resources/authoringResource.md)。 在写入自定义资源以解决问题之前，应在已通过 Microsoft 和 PowerShell 社区创建的大量 DSC 资源中查找。

可以在 [PowerShell 库](https://www.powershellgallery.com/)和 [GitHub](https://github.com/) 中查找 DSC 资源。 还可以直接从 PowerShell 控制台使用 [PowerShellGet](/powershell/module/powershellget/) 安装 DSC 资源。

## <a name="installing-powershellget"></a>安装 PowerShellGet

若要确定是否已获得 PowerShell  ，或者若要获取安装它的帮助，请参阅以下指南：[安装 PowerShellGet](/powershell/scripting/gallery/installing-psget)。

## <a name="finding-dsc-resources-using-powershellget"></a>使用 PowerShellGet 查找 DSC 资源

在系统上安装 PowerShellGet  后，可以找到并安装 [PowerShell 库](https://www.powershellgallery.com/)中托管的 DSC 资源。

首先，使用 [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet 查找 DSC 资源。 首次运行 `Find-DSCResource` 时，你会看到安装“NuGet 提供程序”的提示。

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

按“y”后，将安装“NuGet”提供程序，随后会看到可从 PowerShell 库安装的 DSC 资源的列表。

> [!NOTE]
> 由于列表非常大，因此不会显示。

还可以使用通配符指定 `-Name` 参数或指定不带通配符的 `-Filter` 参数来缩小搜索范围。 此示例尝试使用通配符查找“TimeZone”DSC 资源。

> [!IMPORTANT]
> 当前在 `Find-DSCResource` cmdlet 中有一个 bug，会阻止在 `-Name` 和 `-Filter` 参数中使用通配符。 下面的第二个示例显示了使用 `Where-Object` 的解决方法。

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

还可以使用 `Where-Object` 通过更精细的筛选来查找 DSC 资源。 此方法的速度慢于使用内置筛选参数的速度。

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

有关筛选的详细信息，请参阅 [Where-Object](/powershell/module/microsoft.powershell.core/where-object)。

## <a name="installing-dsc-resources-using-powershellget"></a>使用 PowerShellGet 安装 DSC 资源

若要安装 DSC 资源，请使用 [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet，指定搜索结果中“模块”  名称下显示的模块名称。

“TimeZone”资源存在于“ComputerManagementDSC”模块中，因此这是此示例安装的模块。

> [!NOTE]
> 如果未信任 PowerShell 库，则会看到下面要求确认的警告，并指示如何避免安装时的后续提示。

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

按“y”以继续安装模块。 安装后，可以验证新资源是否是使用 [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) 安装的。

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

还可以通过指定 `-ModuleName` 参数来查看新安装的模块中的其他资源。

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a>另请参阅

- [什么是资源？](../resources/resources.md)
