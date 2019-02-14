---
ms.date: 12/12/2018
keywords: dsc，powershell、 资源、 库、 安装程序
title: 安全其他 DSC 资源
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677031"
---
# <a name="install-additional-dsc-resources"></a>安全其他 DSC 资源

PowerShell Desired State Configuration (DSC) 中包含多个开箱资源。 **PSDesiredStateConfiguration**模块包含的所有 OOB DSC 资源的 PowerShell 特定实例上可用。

这是在 PowerShell 4.0 和资源的功能的说明中包含的 OOB 资源的列表。

> [!NOTE]
> 这是不完整列表，因为 OOB 资源数已增加每个版本的 PowerShell。

|资源  |说明  |
|---------|---------|
|**文件**|控制文件和目录的状态。 将文件从复制**源**到**目标**，然后更新它们时**源**通过比较日期、 校验和和哈希值的更改。|
|**存档**|解压缩存档和指定的位置。 验证与指定存档**校验和**。|
|**环境**|管理的环境变量。|
|**组**|管理本地组并控制组成员身份。|
|**日志**|写入到消息`Microsoft-Windows-Desired State Configuration/Analytic`事件日志。|
|**包**|安装或卸载程序包使用**自变量**， **LogPath**， **ReturnCode**，其他设置。|
|**注册表**|管理注册表项和值。|
|**脚本**|可用于设计您自己[get 测试集](../resources/get-test-set.md)脚本块。|
|**服务**|配置 Windows 服务。|
|**用户** |管理本地用户和属性。|
|**WindowsFeature**|管理角色和功能。|
|**WindowsProcess**|配置 Windows 进程。|

OOB 资源允许常见操作的良好起点。 如果 OOB 资源不能满足您的需要，可以编写您自己[自定义资源](../resources/authoringResource.md)。 编写自定义资源以解决你的问题之前，您应查找通过大量的已创建由 Microsoft 和 PowerShell 社区的 DSC 资源。

可以在这种查找 DSC 资源[PowerShell 库](https://www.powershellgallery.com/)并[GitHub](https://github.com/)。 此外可以直接从 PowerShell 控制台中使用安装 DSC 资源[PowerShellGet](/powershell/module/powershellget/)。

## <a name="installing-powershellget"></a>安装 PowerShellGet

若要确定是否已有**PowerShell**获取，或若要获取安装的帮助，请参阅以下指南：[安装 PowerShellGet](/powershell/gallery/installing-psget)。

## <a name="finding-dsc-resources-using-powershellget"></a>查找 DSC 资源使用 PowerShellGet

一次**PowerShellGet**安装在系统上，您可以找到并安装在中托管的 DSC 资源[PowerShell 库](https://www.powershellgallery.com/)。

首先，使用[Find-dscresource](/powershell/module/powershellget/find-dscresource) cmdlet 查找 DSC 资源。 当你运行`Find-DSCResource`第一次，您将看到以下提示安装"NuGet 提供程序"。

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

后按 y，在"NuGet"提供程序安装，请参阅可从 PowerShell 库安装的 DSC 资源的列表。

> [!NOTE]
> 因为它是非常大，不会显示列表。

此外可以指定`-Name`参数使用通配符，或`-Filter`不带通配符来缩小搜索的参数。 此示例尝试查找使用通配符的"时区"DSC 资源。

> [!IMPORTANT]
> 目前没有中的 bug`Find-DSCResource`可防止在这种使用通配符的 cmdlet`-Name`和`-Filter`参数。 下面的第二个示例显示了解决方法使用`Where-Object`。

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

此外可以使用`Where-Object`查找 DSC 资源使用更精细的筛选。 此方法将比使用内置的筛选参数。

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

有关筛选的详细信息，请参阅[Where-object](/powershell/module/microsoft.powershell.core/where-object)。

## <a name="installing-dsc-resources-using-powershellget"></a>使用 PowerShellGet 安装 DSC 资源

若要安装 DSC 资源，请使用[Install-module](/powershell/module/PowershellGet/Install-Module) cmdlet，指定下显示的模块的名称**模块**名称搜索结果中。

"时区"资源存在于"ComputerManagementDSC"模块，因此，它是此示例将安装该模块。

> [!NOTE]
> 如果你有不受信任的 PowerShell 库，请参阅下面要求确认，该警告，并指示如何避免后续提示上安装。

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

按 y 以继续安装模块。 安装后，可以验证使用安装的新资源[Get-dscresource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)。

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

你还可以查看其他资源在新安装的模块中，通过指定`-ModuleName`参数。

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
