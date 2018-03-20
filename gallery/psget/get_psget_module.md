---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "库,powershell,cmdlet,psget"
title: "获取 PowerShellGet 模块"
ms.openlocfilehash: 7224cf5d71b98d51ca22c47a00ca382d34864bfb
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/15/2018
---
<a name="get-powershellget-module"></a><span data-ttu-id="958ba-103">获取 PowerShellGet 模块</span><span class="sxs-lookup"><span data-stu-id="958ba-103">Get PowerShellGet Module</span></span>
========================

### <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="958ba-104">PowerShellGet 是以下版本的随机模块</span><span class="sxs-lookup"><span data-stu-id="958ba-104">PowerShellGet is an in-box module in the following releases</span></span>
- <span data-ttu-id="958ba-105">[Windows 10](https://www.microsoft.com/windows/get-windows-10) 或更高版本</span><span class="sxs-lookup"><span data-stu-id="958ba-105">[Windows 10](https://www.microsoft.com/windows/get-windows-10) or newer</span></span>
- <span data-ttu-id="958ba-106">[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) 或更高版本</span><span class="sxs-lookup"><span data-stu-id="958ba-106">[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) or newer</span></span>
- <span data-ttu-id="958ba-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) 或更高版本</span><span class="sxs-lookup"><span data-stu-id="958ba-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="958ba-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="958ba-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

### <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="958ba-109">获取适用于 PowerShell 版本 3.0 和 4.0 的 PowerShellGet 模块</span><span class="sxs-lookup"><span data-stu-id="958ba-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>
- [<span data-ttu-id="958ba-110">PackageManagement MSI</span><span class="sxs-lookup"><span data-stu-id="958ba-110">PackageManagement MSI</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409) 

### <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="958ba-111">从 PowerShell 库获取最新版本</span><span class="sxs-lookup"><span data-stu-id="958ba-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="958ba-112">更新 PowerShellGet 前，应始终安装最新的 Nuget 提供程序。</span><span class="sxs-lookup"><span data-stu-id="958ba-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="958ba-113">为此，请在提升的 PowerShell 会话中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="958ba-113">To do that, run the following in an elevated PowerShell session.</span></span>
```powershell
Install-PackageProvider Nuget –Force
Exit
```

#### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="958ba-114">对于使用 PowerShell 5.0（或更高版本）的系统，可以安装最新的 PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="958ba-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span> 
- <span data-ttu-id="958ba-115">若要在 Windows 10、Windows Server 2016、任何安装了 WMF 5.0 或 5.1 的系统或任何安装了 PowerShell 6 的系统上执行此操作，请通过提升的 PowerShell 会话运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="958ba-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>
```powershell
Install-Module –Name PowerShellGet –Force
Exit
```

- <span data-ttu-id="958ba-116">使用 Update-Module 获取更高版本。</span><span class="sxs-lookup"><span data-stu-id="958ba-116">Use Update-Module to get newer versions.</span></span>
```powershell
Update-Module -Name PowerShellGet
Exit
```

#### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpgomicrosoftcomfwlinklinkid746217clcid0x409"></a><span data-ttu-id="958ba-117">对于运行安装了 [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409) 的 PowerShell 3 或 PowerShell 4 的系统</span><span class="sxs-lookup"><span data-stu-id="958ba-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)</span></span>

- <span data-ttu-id="958ba-118">通过提升的 PowerShell 会话运行下面的 PowerShellGet cmdlet，以将模块保存到本地目录</span><span class="sxs-lookup"><span data-stu-id="958ba-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

```powershell
Save-Module PowerShellGet -Path C:\LocalFolder
Exit
```

- <span data-ttu-id="958ba-119">确保未在其他任何进程中加载 PowerShellGet 和 PackageManagment 模块。</span><span class="sxs-lookup"><span data-stu-id="958ba-119">Ensure that PowerShellGet and PackageManagment modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="958ba-120">删除 `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` 和 `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` 文件夹的内容。</span><span class="sxs-lookup"><span data-stu-id="958ba-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="958ba-121">使用提升的权限重新打开 PS 控制台，再运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="958ba-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

```powershell
Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force