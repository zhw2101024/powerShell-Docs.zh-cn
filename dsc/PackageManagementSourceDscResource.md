---
ms.date: 06/20/2018
keywords: dsc,powershell,配置,安装程序
title: DSC PackageManagementSource 资源
ms.openlocfilehash: 5d049b05c387cafe27edb202d569852b10852dce
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753764"
---
# <a name="dsc-packagemanagementsource-resource"></a>DSC PackageManagementSource 资源

> 适用于：Windows PowerShell 4.0、Windows PowerShell 5.0 和 Windows PowerShell 5.1

Windows PowerShell Desired State Configuration (DSC) 中的 **PackageManagementSource** 资源提供了一种在目标节点上注册或取消注册程序包管理源的机制。 **以这种方式注册的程序包管理源在系统上下文中注册，可供系统帐户或 DSC 引擎使用。** 此资源需要 http://PowerShellGallery.com 中的 PackageManagement 模块。

> [!IMPORTANT]
> PackageManagement 模块应至少为版本 1.1.7.0，以下属性信息才正确。

## <a name="syntax"></a>语法

```
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [InstallationPolicy = [string]{ Trusted | Untrusted }]
    [PsDscRunAsCredential = [PSCredential]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a>“属性”

|  属性  |  说明   |
|---|---|
| 名称| 指定要在系统上注册或取消注册的包源名称。|
| ProviderName| 指定 OneGet 提供程序的名称，借此可以与包源进行互操作。|
| SourceLocation| 指定包源的 URI。|
| Ensure| 确定是要注册还是要取消注册包源。|
| InstallationPolicy| 供提供程序使用，如内置的 Nuget 提供程序。 确定是否信任包的源。 可取值为“Untrusted”或“Trusted”。|
| SourceCredential| 提供远程源上程序包的访问权限。|

## <a name="example"></a>示例

此示例使用 PackageManagementSource DSC 资源注册 http://nuget.org 包源。

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```