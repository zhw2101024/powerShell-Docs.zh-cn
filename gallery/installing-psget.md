---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: 库,powershell,cmdlet,psget
title: 安装 PowerShellGet
ms.openlocfilehash: 6190c7caee61b43e70073ff7b30f867a901d3042
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="get-powershellget-module"></a>获取 PowerShellGet 模块

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet 是以下版本的随机模块

- [Windows 10](https://www.microsoft.com/windows/get-windows-10) 或更高版本
- [Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) 或更高版本
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) 或更高版本
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>获取适用于 PowerShell 版本 3.0 和 4.0 的 PowerShellGet 模块

- [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

## <a name="get-the-latest-version-from-powershell-gallery"></a>从 PowerShell 库获取最新版本

- 更新 PowerShellGet 前，应始终安装最新的 Nuget 提供程序。 为此，请在提升的 PowerShell 会话中运行以下命令：

```powershell
Install-PackageProvider Nuget –Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>对于使用 PowerShell 5.0（或更高版本）的系统，可以安装最新的 PowerShellGet

- 若要在 Windows 10、Windows Server 2016、任何安装了 WMF 5.0 或 5.1 的系统或任何安装了 PowerShell 6 的系统上执行此操作，请通过提升的 PowerShell 会话运行以下命令。

```powershell
Install-Module –Name PowerShellGet –Force
Exit
```

- 使用 Update-Module 获取更高版本。

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpgomicrosoftcomfwlinklinkid746217clcid0x409"></a>对于运行安装了 [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409) 的 PowerShell 3 或 PowerShell 4 的系统

- 通过提升的 PowerShell 会话运行下面的 PowerShellGet cmdlet，以将模块保存到本地目录

```powershell
Save-Module PowerShellGet -Path C:\LocalFolder
Exit
```

- 确保未在其他任何进程中加载 PowerShellGet 和 PackageManagment 模块。
- 删除 `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` 和 `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` 文件夹的内容。
- 使用提升的权限重新打开 PS 控制台，再运行以下命令。

```powershell
Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
```