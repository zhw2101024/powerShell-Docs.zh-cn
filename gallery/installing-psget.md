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
# <a name="installing-powershellget"></a><span data-ttu-id="70f50-103">安装 PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="70f50-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="70f50-104">PowerShellGet 是以下版本的随机模块</span><span class="sxs-lookup"><span data-stu-id="70f50-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="70f50-105">[Windows 10](https://www.microsoft.com/windows) 或更高版本</span><span class="sxs-lookup"><span data-stu-id="70f50-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="70f50-106">[Windows Server 2016](/windows-server/windows-server) 或更高版本</span><span class="sxs-lookup"><span data-stu-id="70f50-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="70f50-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) 或更高版本</span><span class="sxs-lookup"><span data-stu-id="70f50-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="70f50-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="70f50-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="70f50-109">从 PowerShell 库获取最新版本</span><span class="sxs-lookup"><span data-stu-id="70f50-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="70f50-110">更新 PowerShellGet  前，应始终安装最新的 NuGet  提供程序。</span><span class="sxs-lookup"><span data-stu-id="70f50-110">Before updating **PowerShellGet**, you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="70f50-111">在提升的 PowerShell 会话中运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="70f50-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="70f50-112">对于使用 PowerShell 5.0（或更高版本）的系统，可以安装最新的 PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="70f50-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="70f50-113">若要在 Windows 10、Windows Server 2016、任何安装了 WMF 5.0 或 5.1 的系统或任何安装了 PowerShell 6 的系统上安装 PowerShellGet，请通过提升的 PowerShell 会话运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="70f50-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

<span data-ttu-id="70f50-114">使用 `Update-Module` 获取更高版本。</span><span class="sxs-lookup"><span data-stu-id="70f50-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-preview"></a><span data-ttu-id="70f50-115">对于运行安装了 PackageManagement 预览版的 PowerShell 3 或 PowerShell 4 的系统</span><span class="sxs-lookup"><span data-stu-id="70f50-115">For systems running PowerShell 3 or PowerShell 4, that have installed the PackageManagement Preview</span></span>

1. <span data-ttu-id="70f50-116">在提升的 PowerShell 会话中，使用 `Save-Module` 将模块保存到本地目录。</span><span class="sxs-lookup"><span data-stu-id="70f50-116">From an elevated PowerShell session, use `Save-Module` to save the modules to a local directory.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder
   Exit
   ```

1. <span data-ttu-id="70f50-117">确保未在其他任何进程中加载 PowerShellGet 和 PackageManagement 模块   。</span><span class="sxs-lookup"><span data-stu-id="70f50-117">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>
1. <span data-ttu-id="70f50-118">删除文件夹的内容：`$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` 和 `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`。</span><span class="sxs-lookup"><span data-stu-id="70f50-118">Delete the contents of the folders: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span></span>
1. <span data-ttu-id="70f50-119">使用提升的权限重新打开 PowerShell 控制台，并运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="70f50-119">Reopen the PowerShell console with elevated permissions and run the following commands.</span></span>

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```
