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
ms.openlocfilehash: 5957ea4c15cd3778bd09b67c4b97de0ef0cfdd2a
ms.sourcegitcommit: 0e4c69d8b5cf71431592fe41da816dec9b70f1f9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/09/2019
ms.locfileid: "74953834"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="2fe88-102">修改 PSModulePath 安装路径</span><span class="sxs-lookup"><span data-stu-id="2fe88-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="2fe88-103">`PSModulePath` 环境变量将路径存储到磁盘上安装的模块的位置。</span><span class="sxs-lookup"><span data-stu-id="2fe88-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="2fe88-104">当用户未指定模块的完整路径时，PowerShell 将使用此变量来查找模块。</span><span class="sxs-lookup"><span data-stu-id="2fe88-104">PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="2fe88-105">此变量中的路径按它们出现的顺序进行搜索。</span><span class="sxs-lookup"><span data-stu-id="2fe88-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="2fe88-106">启动 PowerShell 时，`PSModulePath` 将创建为具有以下默认值的系统环境变量： Windows PowerShell 的 `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` 或 `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules`。</span><span class="sxs-lookup"><span data-stu-id="2fe88-106">When PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` or `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` for Windows PowerShell.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="2fe88-107">查看 PSModulePath 变量</span><span class="sxs-lookup"><span data-stu-id="2fe88-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="2fe88-108">若要查看在 `PSModulePath` 变量中指定的路径，请键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="2fe88-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="2fe88-109">向 PSModulePath 变量添加位置</span><span class="sxs-lookup"><span data-stu-id="2fe88-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="2fe88-110">若要向此变量添加路径，请使用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="2fe88-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="2fe88-111">若要添加仅适用于当前会话的临时值，请在命令行中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="2fe88-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- <span data-ttu-id="2fe88-112">若要添加在会话打开时可用的永久值，请将上述命令添加到 PowerShell 配置文件（`$PROFILE`） ></span><span class="sxs-lookup"><span data-stu-id="2fe88-112">To add a persistent value that is available whenever a session is opened, add the above command to a PowerShell profile file (`$PROFILE`)></span></span>

  <span data-ttu-id="2fe88-113">有关配置文件的详细信息，请参阅 [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)。</span><span class="sxs-lookup"><span data-stu-id="2fe88-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

- <span data-ttu-id="2fe88-114">若要向注册表添加持久性变量，请在 "**系统属性**" 对话框中使用环境变量编辑器创建名为 `PSModulePath` 的新用户环境变量。</span><span class="sxs-lookup"><span data-stu-id="2fe88-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="2fe88-115">若要通过使用脚本来添加持久性变量，请在[SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable)类上使用 .net[方法。](https://docs.microsoft.com/dotnet/api/system.environment)</span><span class="sxs-lookup"><span data-stu-id="2fe88-115">To add a persistent variable by using a script, use the .Net method [SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) on the [System.Environment](https://docs.microsoft.com/dotnet/api/system.environment) class.</span></span> <span data-ttu-id="2fe88-116">例如，以下脚本将 `C:\Program Files\Fabrikam\Module` 路径添加到计算机 `PSModulePath` 环境变量的值。</span><span class="sxs-lookup"><span data-stu-id="2fe88-116">For example, the following script adds the `C:\Program Files\Fabrikam\Module` path to the value of the `PSModulePath` environment variable for the computer.</span></span> <span data-ttu-id="2fe88-117">若要将 `PSModulePath` 环境变量的路径添加到用户，请将 "目标" 设置为 "User"。</span><span class="sxs-lookup"><span data-stu-id="2fe88-117">To add the path to the user `PSModulePath` environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="2fe88-118">从 PSModulePath 删除位置</span><span class="sxs-lookup"><span data-stu-id="2fe88-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="2fe88-119">您可以使用类似的方法从变量中移除路径：例如，`$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` 将从当前会话中删除**c:\ModulePath**路径。</span><span class="sxs-lookup"><span data-stu-id="2fe88-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="2fe88-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2fe88-120">See Also</span></span>

[<span data-ttu-id="2fe88-121">编写 Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="2fe88-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
