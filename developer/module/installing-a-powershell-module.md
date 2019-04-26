---
title: 安装 PowerShell 模块 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: 7c2bfca50de4645676eafc01bbf23d9797e8b758
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082175"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="c8b71-102">安装 PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="c8b71-102">Installing a PowerShell Module</span></span>

<span data-ttu-id="c8b71-103">创建 PowerShell 模块后，将可能想要在系统上，安装该模块，以便你或其他人可能会使用它。</span><span class="sxs-lookup"><span data-stu-id="c8b71-103">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="c8b71-104">通常情况下，这只需包括将复制的模块文件 （即.psm1，或二进制程序集、 模块清单和相关联的任何其他文件） 到一个目录上该计算机上。</span><span class="sxs-lookup"><span data-stu-id="c8b71-104">Generally speaking, this simply consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="c8b71-105">对于非常小的项目，这可能是简单复制并粘贴到一台远程计算机; 上的使用 Windows 资源管理器文件但是，对于大型解决方案可能会想要使用更复杂的安装过程。</span><span class="sxs-lookup"><span data-stu-id="c8b71-105">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="c8b71-106">不管如何获取您到系统上的模块，PowerShell 可以使用技巧，以将帮助用户查找并使用你的模块的数。</span><span class="sxs-lookup"><span data-stu-id="c8b71-106">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="c8b71-107">(有关详细信息，请参阅[导入 PowerShell 模块](./importing-a-powershell-module.md)。)因此，安装的主要问题确保 PowerShell 将能够找到你的模块。</span><span class="sxs-lookup"><span data-stu-id="c8b71-107">(For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).) Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span>

<span data-ttu-id="c8b71-108">本主题包含以下各节：</span><span class="sxs-lookup"><span data-stu-id="c8b71-108">This topic contains the following sections:</span></span>

- <span data-ttu-id="c8b71-109">安装模块的规则</span><span class="sxs-lookup"><span data-stu-id="c8b71-109">Rules for Installing Modules</span></span>

- <span data-ttu-id="c8b71-110">安装模块的位置</span><span class="sxs-lookup"><span data-stu-id="c8b71-110">Where to Install Modules</span></span>

- <span data-ttu-id="c8b71-111">安装模块的多个版本</span><span class="sxs-lookup"><span data-stu-id="c8b71-111">Installing Multiple Versions of a Module</span></span>

- <span data-ttu-id="c8b71-112">处理命令名发生冲突</span><span class="sxs-lookup"><span data-stu-id="c8b71-112">Handling Command Name Conflicts</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="c8b71-113">安装模块的规则</span><span class="sxs-lookup"><span data-stu-id="c8b71-113">Rules for Installing Modules</span></span>

<span data-ttu-id="c8b71-114">以下信息与有关所有模块，其中包括使用、 从其他参与方，获取的模块和模块分发给其他人创建的模块。</span><span class="sxs-lookup"><span data-stu-id="c8b71-114">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="c8b71-115">在 PSModulePath 中安装模块</span><span class="sxs-lookup"><span data-stu-id="c8b71-115">Install Modules in PSModulePath</span></span>

<span data-ttu-id="c8b71-116">只要有可能，在中列出的路径中安装的所有模块**PSModulePath**环境变量或添加的模块路径**PSModulePath**环境变量值。</span><span class="sxs-lookup"><span data-stu-id="c8b71-116">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="c8b71-117">**PSModulePath**环境变量 ($Env: PSModulePath) 包含 Windows PowerShell 模块的位置。</span><span class="sxs-lookup"><span data-stu-id="c8b71-117">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="c8b71-118">若要查找模块此环境变量的值依赖于 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c8b71-118">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="c8b71-119">默认情况下**PSModulePath**环境变量值包含以下系统和用户模块目录，但可以为添加和编辑值。</span><span class="sxs-lookup"><span data-stu-id="c8b71-119">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="c8b71-120">$PSHome\Modules (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span><span class="sxs-lookup"><span data-stu-id="c8b71-120">$PSHome\Modules (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="c8b71-121">此位置保留供 Windows 附带的模块。</span><span class="sxs-lookup"><span data-stu-id="c8b71-121">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="c8b71-122">不要对此位置安装模块。</span><span class="sxs-lookup"><span data-stu-id="c8b71-122">Do not install modules to this location.</span></span>

- <span data-ttu-id="c8b71-123">$ Home\Documents\WindowsPowerShell\Modules (%userprofile%\documents\windowspowershell\modules)</span><span class="sxs-lookup"><span data-stu-id="c8b71-123">$Home\Documents\WindowsPowerShell\Modules (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="c8b71-124">$Env: ProgramFiles\WindowsPowerShell\Modules (%programfiles%\windowspowershell\modules)</span><span class="sxs-lookup"><span data-stu-id="c8b71-124">$Env:ProgramFiles\WindowsPowerShell\Modules (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="c8b71-125">若要获取的值**PSModulePath**环境变量，使用以下命令之一。</span><span class="sxs-lookup"><span data-stu-id="c8b71-125">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="c8b71-126">若要添加的模块路径的值**PSModulePath**环境变量值，请使用以下命令格式。</span><span class="sxs-lookup"><span data-stu-id="c8b71-126">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="c8b71-127">此格式使用**SetEnvironmentVariable**方法**System.Environment**类，以使对独立于会话的更改**PSModulePath**环境变量。</span><span class="sxs-lookup"><span data-stu-id="c8b71-127">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell

  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="c8b71-128">已添加到路径后**PSModulePath**，应广播有关更改的环境消息。</span><span class="sxs-lookup"><span data-stu-id="c8b71-128">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="c8b71-129">广播更改允许其他应用程序，如 shell 中，若要选取更改。</span><span class="sxs-lookup"><span data-stu-id="c8b71-129">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="c8b71-130">若要广播进行的更改，具有产品安装代码发送**WM_SETTINGCHANGE**消息`lParam`设置为字符串"环境"。</span><span class="sxs-lookup"><span data-stu-id="c8b71-130">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="c8b71-131">请务必将消息发送后已更新您的模块安装代码**PSModulePath**。</span><span class="sxs-lookup"><span data-stu-id="c8b71-131">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="c8b71-132">使用正确的模块目录名称</span><span class="sxs-lookup"><span data-stu-id="c8b71-132">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="c8b71-133">"良好"模块是存储在模块目录中的至少一个文件的基名称与同名的目录中的模块。</span><span class="sxs-lookup"><span data-stu-id="c8b71-133">A "well-formed" module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="c8b71-134">如果模块不是格式正确的 Windows PowerShell 无法识别它作为一个模块。</span><span class="sxs-lookup"><span data-stu-id="c8b71-134">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="c8b71-135">文件的"基名称"是不带文件扩展名的名称。</span><span class="sxs-lookup"><span data-stu-id="c8b71-135">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="c8b71-136">在格式正确的模块中包含的模块文件的目录的名称必须与匹配模块中的至少一个文件的基名称。</span><span class="sxs-lookup"><span data-stu-id="c8b71-136">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="c8b71-137">例如，在示例 Fabrikam 模块中包含的模块文件的目录名为"Fabrikam"和至少一个文件具有"Fabrikam"的基名称。</span><span class="sxs-lookup"><span data-stu-id="c8b71-137">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="c8b71-138">在这种情况下，Fabrikam.psd1 和 Fabrikam.dll 具有"Fabrikam"的基名称。</span><span class="sxs-lookup"><span data-stu-id="c8b71-138">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="c8b71-139">安装不正确的效果</span><span class="sxs-lookup"><span data-stu-id="c8b71-139">Effect of Incorrect Installation</span></span>

<span data-ttu-id="c8b71-140">如果该模块不是格式良好，并且其位置中的值不包括**PSModulePath**环境变量，如下所示的 Windows PowerShell 中，基本发现功能不起作用。</span><span class="sxs-lookup"><span data-stu-id="c8b71-140">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="c8b71-141">模块自动加载功能不能自动导入模块。</span><span class="sxs-lookup"><span data-stu-id="c8b71-141">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="c8b71-142">`ListAvailable`的参数[Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 找不到该模块。</span><span class="sxs-lookup"><span data-stu-id="c8b71-142">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="c8b71-143">[导入模块](/powershell/module/Microsoft.PowerShell.Core/Import-Module)cmdlet 找不到该模块。</span><span class="sxs-lookup"><span data-stu-id="c8b71-143">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="c8b71-144">若要导入模块，必须提供根模块文件或模块清单文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="c8b71-144">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="c8b71-145">其他功能，如以下内容，除非模块已导入会话不起作用。</span><span class="sxs-lookup"><span data-stu-id="c8b71-145">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="c8b71-146">格式正确的模块中**PSModulePath**环境变量，这些功能可用，即使该模块未导入会话。</span><span class="sxs-lookup"><span data-stu-id="c8b71-146">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="c8b71-147">[Get-command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet 找不到模块中的命令。</span><span class="sxs-lookup"><span data-stu-id="c8b71-147">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="c8b71-148">[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)并[Save-help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet 无法更新或模块保存帮助。</span><span class="sxs-lookup"><span data-stu-id="c8b71-148">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="c8b71-149">[Show-command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet 不能查找和显示模块中的命令。</span><span class="sxs-lookup"><span data-stu-id="c8b71-149">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="c8b71-150">模块中的命令是缺少`Show-Command`窗口在 Windows PowerShell 集成脚本环境 (ISE)。</span><span class="sxs-lookup"><span data-stu-id="c8b71-150">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="c8b71-151">安装模块的位置</span><span class="sxs-lookup"><span data-stu-id="c8b71-151">Where to Install Modules</span></span>

<span data-ttu-id="c8b71-152">本部分介绍在文件系统中安装 Windows PowerShell 模块的位置。</span><span class="sxs-lookup"><span data-stu-id="c8b71-152">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="c8b71-153">位置取决于如何使用模块。</span><span class="sxs-lookup"><span data-stu-id="c8b71-153">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="c8b71-154">为特定用户安装模块</span><span class="sxs-lookup"><span data-stu-id="c8b71-154">Installing Modules for a Specific User</span></span>

<span data-ttu-id="c8b71-155">如果创建你自己的模块或获取模块从其他参与方，如 Windows PowerShell 社区网站，并且您希望模块可用于仅你的用户帐户，请在特定于用户的模块目录中安装模块。</span><span class="sxs-lookup"><span data-stu-id="c8b71-155">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

```
$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

<span data-ttu-id="c8b71-156">特定于用户的 Modules 目录添加到的值**PSModulePath**默认情况下的环境变量。</span><span class="sxs-lookup"><span data-stu-id="c8b71-156">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="c8b71-157">程序文件中的所有用户安装模块</span><span class="sxs-lookup"><span data-stu-id="c8b71-157">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="c8b71-158">如果你想要可供所有用户帐户的计算机上的模块，模块安装在 Program Files 位置。</span><span class="sxs-lookup"><span data-stu-id="c8b71-158">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

```
$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

> [!NOTE]
> <span data-ttu-id="c8b71-159">默认情况下，Windows PowerShell 4.0 及更高版本情况下，程序文件位置添加到 PSModulePath 环境变量的值。</span><span class="sxs-lookup"><span data-stu-id="c8b71-159">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="c8b71-160">对于早期版本的 Windows PowerShell，您可以手动创建 Program Files 位置 ((%ProgramFiles%\WindowsPowerShell\Modules) 和将此路径添加到 PSModulePath 环境变量，如上文所述。</span><span class="sxs-lookup"><span data-stu-id="c8b71-160">For earlier versions of Windows PowerShell, you can manually create the Program Files location ((%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="c8b71-161">在产品目录中安装模块</span><span class="sxs-lookup"><span data-stu-id="c8b71-161">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="c8b71-162">如果将分发给第三方模块，使用上文所述的默认程序文件位置或创建你自己特定于公司的或特定于产品的子目录，%programfiles%目录。</span><span class="sxs-lookup"><span data-stu-id="c8b71-162">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="c8b71-163">例如，Fabrikam 技术，虚构公司，将发布其 Fabrikam Manager 产品的 Windows PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="c8b71-163">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="c8b71-164">其模块安装程序会创建 Fabrikam Manager 产品子目录中的模块子目录。</span><span class="sxs-lookup"><span data-stu-id="c8b71-164">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="c8b71-165">若要启用 Windows PowerShell 模块发现功能，以查找 Fabrikam 模块，Fabrikam 模块安装程序将添加的模块位置的值**PSModulePath**环境变量。</span><span class="sxs-lookup"><span data-stu-id="c8b71-165">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += "C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="c8b71-166">在常见的文件目录中安装模块</span><span class="sxs-lookup"><span data-stu-id="c8b71-166">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="c8b71-167">如果产品的多个组件或产品的多个版本使用模块，则特定于模块的 %ProgramFiles%\Common Files\Modules 子目录的子目录中安装模块。</span><span class="sxs-lookup"><span data-stu-id="c8b71-167">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="c8b71-168">在以下示例中，Fabrikam 模块安装 Fabrikam %ProgramFiles%\Common Files\Modules 子目录的子目录中。</span><span class="sxs-lookup"><span data-stu-id="c8b71-168">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span> <span data-ttu-id="c8b71-169">请注意每个模块驻留在其自身中的模块子目录的子目录中。</span><span class="sxs-lookup"><span data-stu-id="c8b71-169">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)

```

<span data-ttu-id="c8b71-170">然后，安装程序可确保的值**PSModulePath**环境变量包含常见的文件的模块子目录的路径。</span><span class="sxs-lookup"><span data-stu-id="c8b71-170">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="c8b71-171">安装模块的多个版本</span><span class="sxs-lookup"><span data-stu-id="c8b71-171">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="c8b71-172">若要安装的相同模块的多个版本，请使用以下过程。</span><span class="sxs-lookup"><span data-stu-id="c8b71-172">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="c8b71-173">创建模块的每个版本的目录。</span><span class="sxs-lookup"><span data-stu-id="c8b71-173">Create a directory for each version of the module.</span></span> <span data-ttu-id="c8b71-174">目录名称中包含的版本号。</span><span class="sxs-lookup"><span data-stu-id="c8b71-174">Include the version number in the directory name.</span></span>

2. <span data-ttu-id="c8b71-175">创建每个版本的模块的模块清单。</span><span class="sxs-lookup"><span data-stu-id="c8b71-175">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="c8b71-176">中的值**ModuleVersion**密钥在清单中，输入模块版本号。</span><span class="sxs-lookup"><span data-stu-id="c8b71-176">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="c8b71-177">模块的特定于版本的目录中将清单文件 (.psd1)。</span><span class="sxs-lookup"><span data-stu-id="c8b71-177">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>

3. <span data-ttu-id="c8b71-178">将模块的根文件夹路径添加到的值**PSModulePath**环境变量，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="c8b71-178">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="c8b71-179">若要导入特定版本的模块，最终用户可以使用`MinimumVersion`或`RequiredVersion`的参数[导入模块](/powershell/module/Microsoft.PowerShell.Core/Import-Module)cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c8b71-179">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="c8b71-180">例如，如果 Fabrikam 模块版本 8.0 和 9.0 中，Fabrikam 模块目录结构可能如下所示。</span><span class="sxs-lookup"><span data-stu-id="c8b71-180">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

<span data-ttu-id="c8b71-181">安装程序将添加这两个模块的路径**PSModulePath**环境变量值。</span><span class="sxs-lookup"><span data-stu-id="c8b71-181">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="c8b71-182">完成，这些步骤后**ListAvailable**的参数[Get-module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 将获取这两个 Fabrikam 模块。</span><span class="sxs-lookup"><span data-stu-id="c8b71-182">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="c8b71-183">若要导入特定的模块，请使用`MinimumVersion`或`RequiredVersion`的参数[导入模块](/powershell/module/Microsoft.PowerShell.Core/Import-Module)cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c8b71-183">To import a particular module, use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="c8b71-184">如果这两个模块导入到同一会话中，并且模块包含具有相同名称的 cmdlet，最后一个导入的 cmdlet 是在会话中有效。</span><span class="sxs-lookup"><span data-stu-id="c8b71-184">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="c8b71-185">处理命令名发生冲突</span><span class="sxs-lookup"><span data-stu-id="c8b71-185">Handling Command Name Conflicts</span></span>

<span data-ttu-id="c8b71-186">当模块可导出的命令与命令相同的名称的用户的会话中时，可以发生命令名发生冲突。</span><span class="sxs-lookup"><span data-stu-id="c8b71-186">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="c8b71-187">当一个会话中包含两个具有相同名称的命令时，Windows PowerShell 运行优先的命令类型。</span><span class="sxs-lookup"><span data-stu-id="c8b71-187">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="c8b71-188">当会话中包含具有相同名称和相同类型的两个命令时，Windows PowerShell 将运行已添加到最新会话的命令。</span><span class="sxs-lookup"><span data-stu-id="c8b71-188">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="c8b71-189">若要运行不默认情况下运行的命令，用户可以限定命令名称与模块名称。</span><span class="sxs-lookup"><span data-stu-id="c8b71-189">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="c8b71-190">例如，如果此会话包含`Get-Date`函数和`Get-Date`cmdlet，Windows PowerShell 默认情况下运行该函数。</span><span class="sxs-lookup"><span data-stu-id="c8b71-190">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="c8b71-191">若要运行该 cmdlet，作为命令的开头使用模块名称，例如：</span><span class="sxs-lookup"><span data-stu-id="c8b71-191">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="c8b71-192">若要防止名称冲突，模块作者可以使用**DefaultCommandPrefix**指定名词前缀的所有命令在模块清单中的密钥从模块中导出。</span><span class="sxs-lookup"><span data-stu-id="c8b71-192">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="c8b71-193">用户可以使用**前缀**参数的`Import-Module`cmdlet 来使用备用前缀。</span><span class="sxs-lookup"><span data-stu-id="c8b71-193">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="c8b71-194">值**前缀**参数将优先于的值**DefaultCommandPrefix**密钥。</span><span class="sxs-lookup"><span data-stu-id="c8b71-194">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8b71-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c8b71-195">See Also</span></span>

[<span data-ttu-id="c8b71-196">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="c8b71-196">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="c8b71-197">编写 Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="c8b71-197">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
