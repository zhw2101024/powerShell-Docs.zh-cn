---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC PackageManagementSource 资源
ms.openlocfilehash: 3e67cec9058ecb0e43f882f98f5ec8b92e261a09
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-packagemanagementsource-resource"></a>DSC PackageManagementSource 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) 中的 **PackageManagementSource** 资源提供了一种在目标节点上注册或取消注册程序包管理源的机制。 **以这种方式注册的程序包管理源在系统上下文中注册，可供系统帐户或 DSC 引擎使用。** 此资源需要 http://PowerShellGallery.com 中的 PackageManagement 模块。

## <a name="syntax"></a>语法

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a>“属性”
|  属性  |  说明   |
|---|---|
| 名称| 指定要在系统上注册或取消注册的包源名称。|
| Ensure| 确定是要注册还是要取消注册包源。|
| InstallationPolicy| 确定是否信任包源。 可取值为“Untrusted”或“Trusted”。|
| ProviderName| 指定 OneGet 提供程序的名称，借此可以与包源进行互操作。|
| SourceUri| 指定包源的 URI。|
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
        SourceUri   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```