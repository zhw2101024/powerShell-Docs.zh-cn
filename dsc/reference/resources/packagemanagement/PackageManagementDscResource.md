---
ms.date: 06/20/2018
keywords: dsc,powershell,配置,安装程序
title: DSC PackageManagement 资源
ms.openlocfilehash: 18cbbfe0715c82dcfdf4a5fb6ee36ee814e43d3b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077613"
---
# <a name="dsc-packagemanagement-resource"></a>DSC PackageManagement 资源

适用于：Windows PowerShell 4.0、Windows PowerShell 5.0 和 Windows PowerShell 5.1

Windows PowerShell Desired State Configuration (DSC) 中的 **PackageManagement** 资源提供了一种在目标节点上安装或卸载程序包管理包的机制。 此资源需要 [http://PowerShellGallery.com](http://PowerShellGallery.com) 中的 PackageManagement 模块。

> [!IMPORTANT]
> PackageManagement 模块应至少为版本 1.1.7.0，以下属性信息才正确。

## <a name="syntax"></a>语法

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [AdditionalParameters = [HashTable]]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [MaximumVersion = [string]]
    [MinimumVersion = [string]]
    [ProviderName = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [RequiredVersion = [string]]
    [Source = [string]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a>“属性”

| 属性 | 说明 |
| --- | --- |
| 名称| 指定要安装或卸载的包名称。|
| AdditionalParameters| 传递给 `Get-Package -AdditionalArguments` 的参数的提供程序特定哈希表。 例如，对于 NuGet 提供程序，可以传递 DestinationPath 等附加参数。|
| Ensure| 确定是要安装还是要卸载包。|
| MaximumVersion|指定要查找的包的允许的最高版本。 如果不添加此参数，资源便会查找最高版本的包。|
| MinimumVersion|指定要查找的包的允许的最低版本。 如果不添加此参数，资源便会查找最高版本的包，同时也是 MaximumVersion 参数指定的最高版本。|
| ProviderName| 指定将用作包搜索限定范围的包提供程序名称。 可运行 `Get-PackageProvider` cmdlet 来获取包提供程序名称。|
| RequiredVersion| 指定要安装的包的确切版本。 如果不指定此参数，这个 DSC 资源便会安装最新版本的包，同时也是 MaximumVersion 参数指定的最高版本。|
| 源| 指定可以在其中找到包的包源名称。 这可以是 URI，也可以是向 `Register-PackageSource` 或 PackageManagementSource DSC 资源注册的源。|
| SourceCredential | 为指定的包提供程序或源指定有权安装包的用户帐户。|

## <a name="additional-parameters"></a>附加参数

下表列出了 AdditionalParameters 属性的选项。

| 参数 | 说明 |
| --- | --- |
| DestinationPath| 供提供程序使用，如内置的 Nuget 提供程序。 指定要在其中安装包的文件位置。|
| InstallationPolicy| 供提供程序使用，如内置的 Nuget 提供程序。 确定是否信任包的源。 其中之一：`Untrusted`、`Trusted`。|

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
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2/"
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