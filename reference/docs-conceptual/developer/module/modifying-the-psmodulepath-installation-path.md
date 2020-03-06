---
title: 修改 PSModulePath 安装路径 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: b176d8439025ac132962859f79e72ae6f9703e82
ms.sourcegitcommit: 4a26c05f162c4fa347a9d67e339f8a33e230b9ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78405048"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="3aae7-102">修改 PSModulePath 安装路径</span><span class="sxs-lookup"><span data-stu-id="3aae7-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="3aae7-103">`PSModulePath` 环境变量将路径存储到磁盘上安装的模块的位置。</span><span class="sxs-lookup"><span data-stu-id="3aae7-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="3aae7-104">当用户未指定模块的完整路径时，PowerShell 将使用此变量来查找模块。</span><span class="sxs-lookup"><span data-stu-id="3aae7-104">PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="3aae7-105">此变量中的路径按它们出现的顺序进行搜索。</span><span class="sxs-lookup"><span data-stu-id="3aae7-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="3aae7-106">当 PowerShell 启动时，`PSModulePath` 将创建为系统环境变量，其默认值为： `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` 在 Windows 上，在 Linux 或 Mac 上的 `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules`，以及 Windows PowerShell 的 `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules`。</span><span class="sxs-lookup"><span data-stu-id="3aae7-106">When PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` on Windows and `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` on Linux or Mac, and `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` for Windows PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="3aae7-107">用户特定的**CurrentUser**位置是位于用户配置文件中**文档**位置的 `WindowsPowerShell\Modules` 文件夹。</span><span class="sxs-lookup"><span data-stu-id="3aae7-107">The user-specific **CurrentUser** location is the `WindowsPowerShell\Modules` folder located in the **Documents** location in your user profile.</span></span> <span data-ttu-id="3aae7-108">该位置的特定路径因 Windows 版本而异，无论是否正在使用文件夹重定向。</span><span class="sxs-lookup"><span data-stu-id="3aae7-108">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="3aae7-109">默认情况下，在 Windows 10 上，该位置是 `$HOME\Documents\WindowsPowerShell\Modules`。</span><span class="sxs-lookup"><span data-stu-id="3aae7-109">By default, on Windows 10, that location is `$HOME\Documents\WindowsPowerShell\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="3aae7-110">查看 PSModulePath 变量</span><span class="sxs-lookup"><span data-stu-id="3aae7-110">To view the PSModulePath variable</span></span>

<span data-ttu-id="3aae7-111">若要查看在 `PSModulePath` 变量中指定的路径，请键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="3aae7-111">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="3aae7-112">向 PSModulePath 变量添加位置</span><span class="sxs-lookup"><span data-stu-id="3aae7-112">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="3aae7-113">若要向此变量添加路径，请使用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="3aae7-113">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="3aae7-114">若要添加仅适用于当前会话的临时值，请在命令行中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="3aae7-114">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- <span data-ttu-id="3aae7-115">若要添加在会话打开时可用的永久值，请将上述命令添加到 PowerShell 配置文件（`$PROFILE`） ></span><span class="sxs-lookup"><span data-stu-id="3aae7-115">To add a persistent value that is available whenever a session is opened, add the above command to a PowerShell profile file (`$PROFILE`)></span></span>

  <span data-ttu-id="3aae7-116">有关配置文件的详细信息，请参阅 [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)。</span><span class="sxs-lookup"><span data-stu-id="3aae7-116">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

- <span data-ttu-id="3aae7-117">若要向注册表添加持久性变量，请在 "**系统属性**" 对话框中使用环境变量编辑器创建名为 `PSModulePath` 的新用户环境变量。</span><span class="sxs-lookup"><span data-stu-id="3aae7-117">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="3aae7-118">若要通过使用脚本来添加持久性变量，请在[SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable)类上使用 .net[方法。](https://docs.microsoft.com/dotnet/api/system.environment)</span><span class="sxs-lookup"><span data-stu-id="3aae7-118">To add a persistent variable by using a script, use the .Net method [SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) on the [System.Environment](https://docs.microsoft.com/dotnet/api/system.environment) class.</span></span> <span data-ttu-id="3aae7-119">例如，以下脚本将 `C:\Program Files\Fabrikam\Module` 路径添加到计算机 `PSModulePath` 环境变量的值。</span><span class="sxs-lookup"><span data-stu-id="3aae7-119">For example, the following script adds the `C:\Program Files\Fabrikam\Module` path to the value of the `PSModulePath` environment variable for the computer.</span></span> <span data-ttu-id="3aae7-120">若要将 `PSModulePath` 环境变量的路径添加到用户，请将 "目标" 设置为 "User"。</span><span class="sxs-lookup"><span data-stu-id="3aae7-120">To add the path to the user `PSModulePath` environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="3aae7-121">从 PSModulePath 删除位置</span><span class="sxs-lookup"><span data-stu-id="3aae7-121">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="3aae7-122">您可以使用类似的方法从变量中移除路径：例如，`$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` 将从当前会话中删除**c:\ModulePath**路径。</span><span class="sxs-lookup"><span data-stu-id="3aae7-122">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="3aae7-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3aae7-123">See Also</span></span>

[<span data-ttu-id="3aae7-124">编写 Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="3aae7-124">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="3aae7-125">about_Modules</span><span class="sxs-lookup"><span data-stu-id="3aae7-125">about_Modules</span></span>](/powershell/module/microsoft.powershell.core/about/about_modules)
