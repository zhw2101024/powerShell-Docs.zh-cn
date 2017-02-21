---
title: "DSC PackageManagementSource 资源"
ms.date: 
keywords: powershell,DSC
description: 
ms.topic: article
author: brywang-msft
manager: kriscv
ms.prod: powershell
ms.openlocfilehash: 22e61490e7b3f98335334a2703ec9639cbdaa87e
ms.sourcegitcommit: 89e7ae30faff5f96641fc72764bdc76e0e257bc2
translationtype: HT
---
# <a name="dsc-packagemanagementsource-resource"></a>DSC PackageManagementSource 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) 中的 **PackageManagementSource** 资源提供了一种在目标节点上注册或取消注册程序包管理源的机制。 **以这种方式注册的程序包管理源在系统上下文中注册，可供系统帐户或 DSC 引擎使用。** 此资源需要 http://PowerShellGallery.com 中的 **PackageManagement** 模块。

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

此示例使用 **PackageManagementSource** DSC 资源注册 http://nuget.org 包源。

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
