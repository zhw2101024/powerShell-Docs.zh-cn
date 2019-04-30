---
ms.date: 06/12/2017
contributor: manikb
keywords: 库,powershell,cmdlet,psget
title: 正在启动 NuGet
ms.openlocfilehash: 6d8f106bc3b8741203e87e4c097948a843f06d6e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084379"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a>启动 NuGet 提供程序和 NuGet.exe

最新的 NuGet 提供程序不包含 NuGet.exe。 若要对模块或脚本执行发布操作，PowerShellGet 需要使用二进制可执行 NuGet.exe。 对于其他所有操作（包括查找、安装、保存和卸载），只需要使用 NuGet 提供程序。
PowerShellGet 中的逻辑可以同时启动 NuGet 提供程序和 NuGet.exe，也可以只启动 NuGet 提供程序。 无论属于上述哪种情况，都应该仅显示一条提示消息。 如果计算机未连接 Internet，用户或管理员必须将 NuGet 提供程序和/或 NuGet.exe 文件的受信任实例复制到已断开连接的计算机。

> [!NOTE]
> 自版本 6 起，NuGet 提供程序会随 PowerShell 一起安装。

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a>修复在已连接 Internet 的计算机上尚未安装 NuGet 提供程序时出现的错误

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
Find-Module : NuGet provider is required to interact with NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed.
At line:1 char:1
+ Find-Module -Repository PSGallery -Verbose -Name Contoso
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Find-Module], InvalidOperationException
   + FullyQualifiedErrorId : CouldNotInstallNuGetProvider,Find-Module
```

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     PSGallery        Contoso module
```

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>修复在已连接 Internet 的计算机上执行发布操作期间 NuGet 提供程序可用但 NuGet.exe 不可用时出现的错误

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>修复在已连接 Internet 的计算机上执行发布操作期间 NuGet 提供程序和 NuGet.exe 均不可用时出现的错误

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed and NuGet.exe is available under
one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetBinaries,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a>在未连接 Internet 的计算机上手动启动 NuGet 提供程序

上面展示的进程假设计算机已连接 Internet，且能从公共位置下载文件。 如果前提条件不成立，只能使用上面展示的进程启动计算机，再通过脱机受信任进程将提供程序手动复制到独立节点。 此方案的最常见用例是当专用库可用于支持独立环境时。

在遵循上述进程启动已连接 Internet 的计算机后，提供程序文件位于以下位置：

`C:\Program Files\PackageManagement\ProviderAssemblies\`

NuGet 提供程序的文件夹/文件结构为（版本号可能不同）：

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

使用受信任进程将这些文件夹和文件复制到脱机计算机。

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a>在未连接 Internet 的计算机上手动启动 NuGet.exe 以支持发布操作

除了手动启动 NuGet 提供程序的进程外，如果计算机将用于使用 `Publish-Module` 或 `Publish-Script` cmdlet 向专用库发布模块或脚本，则必须使用相关进程启动 NuGet.exe 二进制可执行文件。

此方案的最常见用例是当专用库可用于支持独立环境时。 可通过两种方法获取 NuGet.exe 文件。

一种方法是启动已连接 Internet 的计算机，并使用受信任进程将文件复制到脱机计算机。 启动已连接 Internet 的计算机后，NuGet.exe 二进制文件位于以下两个文件夹之一：

如果使用提升的权限（以管理员身份）执行 `Publish-Module` 或 `Publish-Script` cmdlet：

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

如果不使用提升的权限（以用户身份）执行这两个 cmdlet：

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

第二种方法是从 NuGet.Org 网站下载 NuGet.exe：[https://dist.nuget.org/index.html](https://www.nuget.org/downloads) 选择生产计算机的 NugGet 版本时，请确保版本高于 2.8.5.208，并确认版本已标记为“推荐”。 如果使用浏览器下载，请务必取消阻止文件。 为此，可以使用 `Unblock-File` cmdlet。

无论属于上述哪种情况，都可以将 NuGet.exe 文件复制到 `$env:path` 中的任意位置，但标准位置为：

若要让可执行文件可用，以便所有用户都可以使用 `Publish-Module` 和 `Publish-Script` cmdlet：

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

若要让可执行文件仅对特定用户可用，请仅将文件复制到相应用户配置文件内的位置：

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```
