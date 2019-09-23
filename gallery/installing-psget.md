---
ms.date: 06/12/2017
contributor: manikb
keywords: 库,powershell,cmdlet,psget
title: 安装 PowerShellGet
ms.openlocfilehash: a0ef46a9ee4bbf668a58067256d098967bde48c5
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143594"
---
# <a name="installing-powershellget"></a>安装 PowerShellGet

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet 是以下版本的随机模块

- [Windows 10](https://www.microsoft.com/windows) 或更高版本
- [Windows Server 2016](/windows-server/windows-server) 或更高版本
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) 或更高版本
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a>从 PowerShell 库获取最新版本

更新 PowerShellGet  前，应始终安装最新的 NuGet  提供程序。 在提升的 PowerShell 会话中运行以下命令。

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>对于使用 PowerShell 5.0（或更高版本）的系统，可以安装最新的 PowerShellGet

若要在 Windows 10、Windows Server 2016、任何安装了 WMF 5.0 或 5.1 的系统或任何安装了 PowerShell 6 的系统上安装 PowerShellGet，请通过提升的 PowerShell 会话运行以下命令。

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

使用 `Update-Module` 获取更高版本。

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-preview"></a>对于运行安装了 PackageManagement 预览版的 PowerShell 3 或 PowerShell 4 的系统

1. 在提升的 PowerShell 会话中，使用 `Save-Module` 将模块保存到本地目录。

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder
   Exit
   ```

1. 确保未在其他任何进程中加载 PowerShellGet 和 PackageManagement 模块   。
1. 删除文件夹的内容：`$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` 和 `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`。
1. 使用提升的权限重新打开 PowerShell 控制台，并运行以下命令。

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```
