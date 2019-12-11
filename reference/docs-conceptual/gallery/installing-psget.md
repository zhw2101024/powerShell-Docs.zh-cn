---
ms.date: 09/19/2019
contributor: manikb
keywords: 库,powershell,cmdlet,psget
title: 安装 PowerShellGet
ms.openlocfilehash: 69dc851c54089b47fb19e5b32990d579d26effb9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328198"
---
# <a name="installing-powershellget"></a><span data-ttu-id="a06bd-103">安装 PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="a06bd-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="a06bd-104">PowerShellGet 是以下版本的随机模块</span><span class="sxs-lookup"><span data-stu-id="a06bd-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="a06bd-105">[Windows 10](https://www.microsoft.com/windows) 或更高版本</span><span class="sxs-lookup"><span data-stu-id="a06bd-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="a06bd-106">[Windows Server 2016](/windows-server/windows-server) 或更高版本</span><span class="sxs-lookup"><span data-stu-id="a06bd-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="a06bd-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) 或更高版本</span><span class="sxs-lookup"><span data-stu-id="a06bd-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="a06bd-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="a06bd-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="a06bd-109">从 PowerShell 库获取最新版本</span><span class="sxs-lookup"><span data-stu-id="a06bd-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="a06bd-110">更新 PowerShellGet  前，应始终安装最新的 NuGet  提供程序。</span><span class="sxs-lookup"><span data-stu-id="a06bd-110">Before updating **PowerShellGet**, you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="a06bd-111">在提升的 PowerShell 会话中运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="a06bd-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="a06bd-112">对于使用 PowerShell 5.0（或更高版本）的系统，可以安装最新的 PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="a06bd-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="a06bd-113">若要在 Windows 10、Windows Server 2016、任何安装了 WMF 5.0 或 5.1 的系统或任何安装了 PowerShell 6 的系统上安装 PowerShellGet，请通过提升的 PowerShell 会话运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="a06bd-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

<span data-ttu-id="a06bd-114">使用 `Update-Module` 获取更高版本。</span><span class="sxs-lookup"><span data-stu-id="a06bd-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a><span data-ttu-id="a06bd-115">对于运行 PowerShell 3.0 或 PowerShell 4.0 的计算机</span><span class="sxs-lookup"><span data-stu-id="a06bd-115">For computers running PowerShell 3.0 or PowerShell 4.0</span></span>

<span data-ttu-id="a06bd-116">这些说明适用于已安装 **PackageManagement 预览版**或未安装任何版本的 **PowerShellGet** 的计算机。</span><span class="sxs-lookup"><span data-stu-id="a06bd-116">These instructions apply to computers that have the **PackageManagement Preview** installed or don't have any version of **PowerShellGet** installed.</span></span>

<span data-ttu-id="a06bd-117">两组指令都使用 `Save-Module` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a06bd-117">The `Save-Module` cmdlet is used in both sets of instructions.</span></span> <span data-ttu-id="a06bd-118">`Save-Module` 从已注册的存储库下载并保存模块和所有依赖项。</span><span class="sxs-lookup"><span data-stu-id="a06bd-118">`Save-Module` downloads and saves a module and any dependencies from a registered repository.</span></span> <span data-ttu-id="a06bd-119">模块的最新版本已保存到本地计算机上的指定路径，但尚未安装。</span><span class="sxs-lookup"><span data-stu-id="a06bd-119">The module's most current version is saved to a specified path on the local computer, but isn't installed.</span></span> <span data-ttu-id="a06bd-120">有关详细信息，请参阅 [Save-Module](/powershell/module/PowershellGet/Save-Module)。</span><span class="sxs-lookup"><span data-stu-id="a06bd-120">For more information, see [Save-Module](/powershell/module/PowershellGet/Save-Module).</span></span>

#### <a name="computers-with-the-packagemanagement-preview-installed"></a><span data-ttu-id="a06bd-121">安装了 PackageManagement 预览版的计算机</span><span class="sxs-lookup"><span data-stu-id="a06bd-121">Computers with the PackageManagement Preview installed</span></span>

1. <span data-ttu-id="a06bd-122">在 PowerShell 会话中，使用 `Save-Module` 将模块保存到本地目录。</span><span class="sxs-lookup"><span data-stu-id="a06bd-122">From a PowerShell session, use `Save-Module` to save the modules to a local directory.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="a06bd-123">确保未在其他任何进程中加载 PowerShellGet 和 PackageManagement 模块   。</span><span class="sxs-lookup"><span data-stu-id="a06bd-123">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>
1. <span data-ttu-id="a06bd-124">删除文件夹的内容：`$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` 和 `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`。</span><span class="sxs-lookup"><span data-stu-id="a06bd-124">Delete the contents of the folders: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span></span>
1. <span data-ttu-id="a06bd-125">使用提升的权限重新打开 PowerShell 控制台，并运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="a06bd-125">Reopen the PowerShell console with elevated permissions and run the following commands.</span></span>

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```

#### <a name="computers-without-powershellget"></a><span data-ttu-id="a06bd-126">没有 PowerShellGet 的计算机</span><span class="sxs-lookup"><span data-stu-id="a06bd-126">Computers without PowerShellGet</span></span>

<span data-ttu-id="a06bd-127">对于未安装任何版本的 **PowerShellGet** 的计算机，需要使用安装了 **PowerShellGet** 的计算机来下载模块。</span><span class="sxs-lookup"><span data-stu-id="a06bd-127">For computer's without any version of **PowerShellGet** installed, a computer with **PowerShellGet** installed is needed to download the modules.</span></span>

1. <span data-ttu-id="a06bd-128">在安装了 **PowerShellGet** 的计算机上，使用 `Save-Module` 下载 **PowerShellGet** 的最新版本。</span><span class="sxs-lookup"><span data-stu-id="a06bd-128">From the computer that has **PowerShellGet** installed, use `Save-Module` to download the current version of **PowerShellGet**.</span></span> <span data-ttu-id="a06bd-129">已下载两个文件夹：**PowerShellGet** 和 **PackageManagement**。</span><span class="sxs-lookup"><span data-stu-id="a06bd-129">Two folders are downloaded: **PowerShellGet** and **PackageManagement**.</span></span> <span data-ttu-id="a06bd-130">每个文件夹包含一个带有版本号的子文件夹。</span><span class="sxs-lookup"><span data-stu-id="a06bd-130">Each folder contains a subfolder with a version number.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="a06bd-131">将 **PowerShellGet** 和 **PackageManagement** 文件夹复制到未安装 **PowerShellGet** 的计算机上。</span><span class="sxs-lookup"><span data-stu-id="a06bd-131">Copy the **PowerShellGet** and **PackageManagement** folders to the computer that doesn't have **PowerShellGet** installed.</span></span>

   <span data-ttu-id="a06bd-132">目标目录为：`$env:ProgramFiles\WindowsPowerShell\Modules`</span><span class="sxs-lookup"><span data-stu-id="a06bd-132">The destination directory is: `$env:ProgramFiles\WindowsPowerShell\Modules`</span></span>
