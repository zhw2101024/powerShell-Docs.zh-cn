---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 导入已安装资源的指定版本
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953984"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a>导入已安装资源的指定版本

> 适用于：Windows PowerShell 5.0

在 PowerShell 5.0 中，DSC 资源的不同版本可以并行安装在计算机上。 资源模块可以将资源的不同版本存储在以版本命名的文件夹中。

## <a name="installing-separate-resource-versions-side-by-side"></a>并行安装不同的资源版本

可以使用 [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet 的 **MinimumVersion**、**MaximumVersion** 和 **RequiredVersion** 参数来指定要安装的模块版本。 调用 **Install-Module** 而不指定某个版本安装最新版本。

例如，存在多个版本的 xFailOverCluster 模块，其中每个都包含 xCluster 资源   。 调用 Install-Module  而不指定版本号安装模块的最新版本。

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

若要安装模块的特定版本，请将 RequiredVersion  指定为 1.1.0.0。 这样会与已安装版本并行安装指定版本。

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

现在，你会看到使用 `Get-DSCResource` 时列出的模块的两个版本。

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>在配置中指定资源版本

如果已在计算机上安装不同的资源版本，那么在配置中使用资源时，必须指定该资源的版本。 为此，请指定 **Import-DscResource** 关键字的 **ModuleVersion** 参数。 如果你无法指定已安装多个版本的资源模块的版本，则配置会生成错误。

下面的配置演示如何指定要调用的资源的版本：

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

>注意：Import-DscResource 的 ModuleVersion 参数在 PowerShell 4.0 中不可用。 在 PowerShell 4.0 中，你可以将模块规范对象传递到 Import-DscResource 的 ModuleName 参数，从而指定模块版本。 模块规范对象是包含 ModuleName 和 RequiredVersion 键的哈希表。 例如：

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

此操作在 PowerShell 5.0 中也有效，但建议使用 **ModuleVersion** 参数。

## <a name="see-also"></a>另请参阅

- [DSC 配置](configurations.md)
- [DSC 资源](../resources/resources.md)
