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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855563"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="0ba19-102">修改 PSModulePath 安装路径</span><span class="sxs-lookup"><span data-stu-id="0ba19-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="0ba19-103">`PSModulePath`环境变量存储在磁盘上安装的模块的位置的路径。</span><span class="sxs-lookup"><span data-stu-id="0ba19-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="0ba19-104">Windows PowerShell 使用此变量来查找模块时用户未指定模块的完整路径。</span><span class="sxs-lookup"><span data-stu-id="0ba19-104">Windows PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="0ba19-105">按它们的显示的顺序搜索此变量中的路径。</span><span class="sxs-lookup"><span data-stu-id="0ba19-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="0ba19-106">Windows PowerShell 启动时，`PSModulePath`创建为具有以下默认值的系统环境变量： `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`。</span><span class="sxs-lookup"><span data-stu-id="0ba19-106">When Windows PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="0ba19-107">若要查看 PSModulePath 变量</span><span class="sxs-lookup"><span data-stu-id="0ba19-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="0ba19-108">若要查看中指定的路径`PSModulePath`变量中，键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="0ba19-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="0ba19-109">若要将位置添加到 PSModulePath 变量</span><span class="sxs-lookup"><span data-stu-id="0ba19-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="0ba19-110">若要将路径添加到此变量，使用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="0ba19-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="0ba19-111">若要添加仅用于当前会话的临时值，请在命令行运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="0ba19-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- <span data-ttu-id="0ba19-112">若要添加可用的持久值每次打开会话，Windows PowerShell 配置文件中添加以下命令：</span><span class="sxs-lookup"><span data-stu-id="0ba19-112">To add a persistent value that is available whenever a session is opened, add the following command to a Windows PowerShell profile:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  <span data-ttu-id="0ba19-113">有关配置文件的详细信息，请参阅[about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) Microsoft TechNet 库中。</span><span class="sxs-lookup"><span data-stu-id="0ba19-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in the Microsoft TechNet library.</span></span>

- <span data-ttu-id="0ba19-114">若要永久性变量添加到注册表，创建名为的新用户环境变量`PSModulePath`使用中的环境变量编辑器**系统属性**对话框。</span><span class="sxs-lookup"><span data-stu-id="0ba19-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="0ba19-115">若要使用脚本添加持久性的变量，请使用**SetEnvironmentVariable**环境类上的方法。</span><span class="sxs-lookup"><span data-stu-id="0ba19-115">To add a persistent variable by using a script, use the **SetEnvironmentVariable** method on the Environment class.</span></span> <span data-ttu-id="0ba19-116">例如，以下脚本将添加"C:\Program Files\Fabrikam\Module 路径的计算机的 PSModulePath 环境变量的值。</span><span class="sxs-lookup"><span data-stu-id="0ba19-116">For example, the following script adds the "C:\Program Files\Fabrikam\Module path to the value of the PSModulePath environment variable for the computer.</span></span> <span data-ttu-id="0ba19-117">将该路径添加到用户 PSModulePath 环境变量，请将目标设置为"User"。</span><span class="sxs-lookup"><span data-stu-id="0ba19-117">To add the path to the user PSModulePath environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="0ba19-118">若要从 PSModulePath 删除位置</span><span class="sxs-lookup"><span data-stu-id="0ba19-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="0ba19-119">您可以从使用类似的方法的变量中删除路径： 例如，`$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"`将删除**c:\ModulePath**从当前会话的路径。</span><span class="sxs-lookup"><span data-stu-id="0ba19-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ba19-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0ba19-120">See Also</span></span>

[<span data-ttu-id="0ba19-121">编写 Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="0ba19-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
