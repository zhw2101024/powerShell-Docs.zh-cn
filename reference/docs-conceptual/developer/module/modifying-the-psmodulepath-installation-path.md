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
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360666"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="703ae-102">修改 PSModulePath 安装路径</span><span class="sxs-lookup"><span data-stu-id="703ae-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="703ae-103">@No__t-0 环境变量将路径存储到磁盘上安装的模块的位置。</span><span class="sxs-lookup"><span data-stu-id="703ae-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="703ae-104">当用户未指定模块的完整路径时，Windows PowerShell 使用此变量来查找模块。</span><span class="sxs-lookup"><span data-stu-id="703ae-104">Windows PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="703ae-105">此变量中的路径按它们出现的顺序进行搜索。</span><span class="sxs-lookup"><span data-stu-id="703ae-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="703ae-106">当 Windows PowerShell 启动时，将 `PSModulePath` 创建为具有以下默认值的系统环境变量： `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`。</span><span class="sxs-lookup"><span data-stu-id="703ae-106">When Windows PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="703ae-107">查看 PSModulePath 变量</span><span class="sxs-lookup"><span data-stu-id="703ae-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="703ae-108">若要查看在 `PSModulePath` 变量中指定的路径，请键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="703ae-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="703ae-109">向 PSModulePath 变量添加位置</span><span class="sxs-lookup"><span data-stu-id="703ae-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="703ae-110">若要向此变量添加路径，请使用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="703ae-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="703ae-111">若要添加仅适用于当前会话的临时值，请在命令行中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="703ae-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- <span data-ttu-id="703ae-112">若要添加在会话打开时可用的永久值，请将以下命令添加到 Windows PowerShell 配置文件：</span><span class="sxs-lookup"><span data-stu-id="703ae-112">To add a persistent value that is available whenever a session is opened, add the following command to a Windows PowerShell profile:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  <span data-ttu-id="703ae-113">有关配置文件的详细信息，请参阅 Microsoft TechNet 库中的[about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) 。</span><span class="sxs-lookup"><span data-stu-id="703ae-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in the Microsoft TechNet library.</span></span>

- <span data-ttu-id="703ae-114">若要向注册表添加持久性变量，请在 "**系统属性**" 对话框中使用环境变量编辑器创建名为 @no__t 的新用户环境变量。</span><span class="sxs-lookup"><span data-stu-id="703ae-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="703ae-115">若要通过使用脚本来添加持久性变量，请对环境类使用**SetEnvironmentVariable**方法。</span><span class="sxs-lookup"><span data-stu-id="703ae-115">To add a persistent variable by using a script, use the **SetEnvironmentVariable** method on the Environment class.</span></span> <span data-ttu-id="703ae-116">例如，下面的脚本将 "C:\Program Files\Fabrikam\Module 路径添加到计算机的 PSModulePath 环境变量的值。</span><span class="sxs-lookup"><span data-stu-id="703ae-116">For example, the following script adds the "C:\Program Files\Fabrikam\Module path to the value of the PSModulePath environment variable for the computer.</span></span> <span data-ttu-id="703ae-117">若要将路径添加到 user PSModulePath 环境变量，请将目标设置为 "User"。</span><span class="sxs-lookup"><span data-stu-id="703ae-117">To add the path to the user PSModulePath environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="703ae-118">从 PSModulePath 删除位置</span><span class="sxs-lookup"><span data-stu-id="703ae-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="703ae-119">您可以使用类似的方法从变量中移除路径：例如，`$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` 将从当前会话中删除**c:\ModulePath**路径。</span><span class="sxs-lookup"><span data-stu-id="703ae-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="703ae-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="703ae-120">See Also</span></span>

[<span data-ttu-id="703ae-121">编写 Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="703ae-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
