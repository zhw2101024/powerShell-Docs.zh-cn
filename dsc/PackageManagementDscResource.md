---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,配置,安装程序
title: DSC PackageManagement 资源
ms.openlocfilehash: e6eea9f0bae42e131976dacb9813da759ff31239
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-packagemanagement-resource"></a>DSC PackageManagement 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) 中的 **PackageManagement** 资源提供了一种在目标节点上安装或卸载程序包管理包的机制。 此资源需要 http://PowerShellGallery.com 中的 PackageManagement 模块。

## <a name="syntax"></a>语法

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ Source = [string] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ RequiredVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ MaximumVersion = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ ProviderName = [string] ]
    [ AdditionalParameters = [Microsoft.Management.Infrastructure.CimInstance[]] ]
}
```

## <a name="properties"></a>“属性”
|  属性  |  说明   |
|---|---|
| 名称| 指定要安装或卸载的包名称。|
| 源| 指定可以在其中找到包的包源名称。 这可以是 URI，也可以是使用 Register-PackageSource 或 PackageManagementSource DSC 资源注册的源。 也可以使用 DSC 资源 MSFT_PackageManagementSource 注册包源。|
| Ensure| 确定是要安装还是要卸载包。|
| RequiredVersion| 指定要安装的包的确切版本。 如果不指定这个参数，此 DSC 资源将安装包的最新版本，同时符合 MaximumVersion 参数指定的任何最高版本要求。|
| MinimumVersion| 指定要安装的包的最低允许版本。 如果不添加这个参数，此 DSC 资源将安装包的最高版本，同时符合 MaximumVersion 参数指定的任何最高版本要求。|
| MaximumVersion| 指定要安装的包的最高允许版本。 如果不指定这个参数，此 DSC 资源将安装包的最高版本。|
| SourceCredential | 为指定的包提供程序或源指定有权安装包的用户帐户。|
| ProviderName| 指定将用作包搜索限定范围的包提供程序名称。 可通过运行 Get-PackageProvider cmdlet 获取包提供程序名称。|
| AdditionalParameters| 以哈希表的形式传递的提供程序特定参数。 例如，对于 NuGet 提供程序，可以传递 DestinationPath 等附加参数。|

## <a name="additional-parameters"></a>附加参数
下表列出了 AdditionalParameters 属性的选项。
|  参数  | 说明   |
|---|---|
| DestinationPath| 供提供程序使用，如内置的 Nuget 提供程序。 指定要在其中安装包的文件位置。|
| InstallationPolicy| 供提供程序使用，如内置的 Nuget 提供程序。 确定是否信任包的源。 可取值为“Untrusted”或“Trusted”。|

## <a name="example"></a>示例

此示例使用 **PackageManagement** DSC 资源安装 **JQuery** NuGet 包和 **GistProvider** PowerShell 模块。 此示例先确保已指定相应的包源，然后定义 **JQuery** 和 **GistProvider** 包的预期状态（分别为 NuGet 和 PowerShell）。

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceUri   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceUri   = "https://www.powershellgallery.com/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagement NugetPackage
    {
        Ensure               = "Present"
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1"
        DependsOn            = "[PackageManagementSource]SourceRepository"
    }

    PackageManagement PSModule
    {
        Ensure               = "Present"
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery"
    }
}
```