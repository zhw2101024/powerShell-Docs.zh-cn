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
ms.openlocfilehash: 60ac4bf9089232a9fa879e835e32da53422489fd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367066"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="92b9c-102">安装 PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="92b9c-102">Installing a PowerShell Module</span></span>

<span data-ttu-id="92b9c-103">创建 PowerShell 模块后，你可能需要在系统上安装该模块，以便你或其他人可以使用它。</span><span class="sxs-lookup"><span data-stu-id="92b9c-103">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="92b9c-104">一般而言，这包括将模块文件（即 hbase-runner.psm1 或二进制程序集、模块清单以及任何其他相关文件）复制到该计算机上的目录中。</span><span class="sxs-lookup"><span data-stu-id="92b9c-104">Generally speaking, this consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="92b9c-105">对于非常小的项目，这种情况很简单，只需要使用 Windows 资源管理器将文件复制并粘贴到单台远程计算机上即可。但是，对于较大的解决方案，你可能希望使用更复杂的安装过程。</span><span class="sxs-lookup"><span data-stu-id="92b9c-105">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="92b9c-106">无论您将模块进入系统的方式如何，PowerShell 都可以使用多种技术，使用户能够查找和使用您的模块。</span><span class="sxs-lookup"><span data-stu-id="92b9c-106">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="92b9c-107">因此，安装的主要问题是确保 PowerShell 能够找到模块。</span><span class="sxs-lookup"><span data-stu-id="92b9c-107">Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span> <span data-ttu-id="92b9c-108">有关详细信息，请参阅[导入 PowerShell 模块](./importing-a-powershell-module.md)。</span><span class="sxs-lookup"><span data-stu-id="92b9c-108">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="92b9c-109">模块安装规则</span><span class="sxs-lookup"><span data-stu-id="92b9c-109">Rules for Installing Modules</span></span>

<span data-ttu-id="92b9c-110">以下信息适用于所有模块，包括你为自己使用而创建的模块、从其他参与方获取的模块以及分发给其他人的模块。</span><span class="sxs-lookup"><span data-stu-id="92b9c-110">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="92b9c-111">在 PSModulePath 中安装模块</span><span class="sxs-lookup"><span data-stu-id="92b9c-111">Install Modules in PSModulePath</span></span>

<span data-ttu-id="92b9c-112">尽可能将所有模块安装在**PSModulePath**环境变量中列出的路径中，或将模块路径添加到**PSModulePath**环境变量值。</span><span class="sxs-lookup"><span data-stu-id="92b9c-112">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="92b9c-113">**PSModulePath**环境变量（$Env:P smodulepath）包含 Windows PowerShell 模块的位置。</span><span class="sxs-lookup"><span data-stu-id="92b9c-113">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="92b9c-114">Cmdlet 依赖于此环境变量的值来查找模块。</span><span class="sxs-lookup"><span data-stu-id="92b9c-114">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="92b9c-115">默认情况下， **PSModulePath**环境变量值包含以下系统和用户模块目录，但您可以添加和编辑值。</span><span class="sxs-lookup"><span data-stu-id="92b9c-115">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="92b9c-116">`$PSHome\Modules` （%Windir%\System32\WindowsPowerShell\v1.0\Modules）</span><span class="sxs-lookup"><span data-stu-id="92b9c-116">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="92b9c-117">此位置是为随 Windows 提供的模块而保留的。</span><span class="sxs-lookup"><span data-stu-id="92b9c-117">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="92b9c-118">不要将模块安装到此位置。</span><span class="sxs-lookup"><span data-stu-id="92b9c-118">Do not install modules to this location.</span></span>

- <span data-ttu-id="92b9c-119">`$Home\Documents\WindowsPowerShell\Modules` （%UserProfile%\Documents\WindowsPowerShell\Modules）</span><span class="sxs-lookup"><span data-stu-id="92b9c-119">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="92b9c-120">`$Env:ProgramFiles\WindowsPowerShell\Modules` （%ProgramFiles%\WindowsPowerShell\Modules）</span><span class="sxs-lookup"><span data-stu-id="92b9c-120">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="92b9c-121">若要获取**PSModulePath**环境变量的值，请使用以下命令之一。</span><span class="sxs-lookup"><span data-stu-id="92b9c-121">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="92b9c-122">若要将模块路径添加到**PSModulePath**环境变量值的值中，请使用以下命令格式。</span><span class="sxs-lookup"><span data-stu-id="92b9c-122">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="92b9c-123">此格式使用 SetEnvironmentVariable**类的**方法对**PSModulePath**环境变量进行与会话无关的更改。</span><span class="sxs-lookup"><span data-stu-id="92b9c-123">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="92b9c-124">将路径添加到**PSModulePath**后，应广播与更改相关的环境消息。</span><span class="sxs-lookup"><span data-stu-id="92b9c-124">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="92b9c-125">广播更改后，其他应用程序（如 shell）可以选取更改。</span><span class="sxs-lookup"><span data-stu-id="92b9c-125">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="92b9c-126">若要广播此更改，请让你的产品安装代码发送**WM_SETTINGCHANGE**消息，并将 `lParam` 设置为字符串 "环境"。</span><span class="sxs-lookup"><span data-stu-id="92b9c-126">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="92b9c-127">请确保在模块安装代码更新后发送消息**PSModulePath**。</span><span class="sxs-lookup"><span data-stu-id="92b9c-127">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="92b9c-128">使用正确的模块目录名称</span><span class="sxs-lookup"><span data-stu-id="92b9c-128">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="92b9c-129">格式正确的模块是存储在目录中的模块，其名称与模块目录中至少一个文件的基名称相同。</span><span class="sxs-lookup"><span data-stu-id="92b9c-129">A well-formed module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="92b9c-130">如果模块的格式不正确，则 Windows PowerShell 无法将其识别为模块。</span><span class="sxs-lookup"><span data-stu-id="92b9c-130">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="92b9c-131">文件的 "基名称" 为不带文件扩展名的名称。</span><span class="sxs-lookup"><span data-stu-id="92b9c-131">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="92b9c-132">在格式正确的模块中，包含模块文件的目录的名称必须与模块中至少一个文件的基名称匹配。</span><span class="sxs-lookup"><span data-stu-id="92b9c-132">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="92b9c-133">例如，在示例 Fabrikam 模块中，包含模块文件的目录命名为 "Fabrikam"，并且至少有一个文件具有 "Fabrikam" 基名称。</span><span class="sxs-lookup"><span data-stu-id="92b9c-133">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="92b9c-134">在这种情况下，psd1 和 Fabrikam 都具有 "Fabrikam" 基名称。</span><span class="sxs-lookup"><span data-stu-id="92b9c-134">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="92b9c-135">错误安装的效果</span><span class="sxs-lookup"><span data-stu-id="92b9c-135">Effect of Incorrect Installation</span></span>

<span data-ttu-id="92b9c-136">如果该模块的格式不正确，并且其位置未包含在**PSModulePath**环境变量的值中，则 Windows PowerShell 的基本发现功能（如下所示）不起作用。</span><span class="sxs-lookup"><span data-stu-id="92b9c-136">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="92b9c-137">模块自动加载功能无法自动导入模块。</span><span class="sxs-lookup"><span data-stu-id="92b9c-137">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="92b9c-138">[Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet 的 `ListAvailable` 参数找不到该模块。</span><span class="sxs-lookup"><span data-stu-id="92b9c-138">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="92b9c-139">[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 找不到该模块。</span><span class="sxs-lookup"><span data-stu-id="92b9c-139">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="92b9c-140">若要导入模块，必须提供根模块文件或模块清单文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="92b9c-140">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="92b9c-141">除非将模块导入到会话中，否则其他功能（如以下）将不起作用。</span><span class="sxs-lookup"><span data-stu-id="92b9c-141">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="92b9c-142">在**PSModulePath**环境变量中的格式正确的模块中，即使模块未导入到会话中，这些功能也起作用。</span><span class="sxs-lookup"><span data-stu-id="92b9c-142">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="92b9c-143">[Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet 无法在模块中找到命令。</span><span class="sxs-lookup"><span data-stu-id="92b9c-143">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="92b9c-144">[Update-help](/powershell/module/Microsoft.PowerShell.Core/Update-Help)和 get-help cmdlet 无法更新[或保存模块](/powershell/module/Microsoft.PowerShell.Core/Save-Help)的帮助。</span><span class="sxs-lookup"><span data-stu-id="92b9c-144">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="92b9c-145">[Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet 无法在模块中找到并显示命令。</span><span class="sxs-lookup"><span data-stu-id="92b9c-145">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="92b9c-146">Windows PowerShell 集成脚本环境（ISE）中的 "`Show-Command`" 窗口缺少模块中的命令。</span><span class="sxs-lookup"><span data-stu-id="92b9c-146">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="92b9c-147">模块的安装位置</span><span class="sxs-lookup"><span data-stu-id="92b9c-147">Where to Install Modules</span></span>

<span data-ttu-id="92b9c-148">本部分介绍在文件系统中安装 Windows PowerShell 模块的位置。</span><span class="sxs-lookup"><span data-stu-id="92b9c-148">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="92b9c-149">位置取决于模块的使用方式。</span><span class="sxs-lookup"><span data-stu-id="92b9c-149">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="92b9c-150">为特定用户安装模块</span><span class="sxs-lookup"><span data-stu-id="92b9c-150">Installing Modules for a Specific User</span></span>

<span data-ttu-id="92b9c-151">如果创建自己的模块或从另一方获取模块（如 Windows PowerShell 社区网站），并且希望该模块仅适用于用户帐户，请在用户特定的模块目录中安装该模块。</span><span class="sxs-lookup"><span data-stu-id="92b9c-151">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

<span data-ttu-id="92b9c-152">默认情况下，用户特定的模块目录将添加到**PSModulePath**环境变量的值。</span><span class="sxs-lookup"><span data-stu-id="92b9c-152">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="92b9c-153">为程序文件中的所有用户安装模块</span><span class="sxs-lookup"><span data-stu-id="92b9c-153">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="92b9c-154">如果希望模块可用于计算机上的所有用户帐户，请在 "程序文件" 位置中安装该模块。</span><span class="sxs-lookup"><span data-stu-id="92b9c-154">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> <span data-ttu-id="92b9c-155">默认情况下，在 Windows PowerShell 4.0 和更高版本中，将程序文件位置添加到 PSModulePath 环境变量的值。</span><span class="sxs-lookup"><span data-stu-id="92b9c-155">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="92b9c-156">对于早期版本的 Windows PowerShell，可以手动创建程序文件位置（（%ProgramFiles%\WindowsPowerShell\Modules）并将此路径添加到 PSModulePath 环境变量，如上所述。</span><span class="sxs-lookup"><span data-stu-id="92b9c-156">For earlier versions of Windows PowerShell, you can manually create the Program Files location ((%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="92b9c-157">在产品目录中安装模块</span><span class="sxs-lookup"><span data-stu-id="92b9c-157">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="92b9c-158">如果要将模块分发给其他参与方，请使用上面所述的默认程序文件位置，或创建自己的特定于公司的或特定于产品的% ProgramFiles% 目录。</span><span class="sxs-lookup"><span data-stu-id="92b9c-158">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="92b9c-159">例如，一家虚构的公司是一家虚构的公司，为其 Fabrikam 经理产品发运了一个 Windows PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="92b9c-159">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="92b9c-160">它们的模块安装程序会在 Fabrikam 管理器产品子目录中创建模块子目录。</span><span class="sxs-lookup"><span data-stu-id="92b9c-160">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="92b9c-161">为了使 Windows PowerShell 模块发现功能能够查找 Fabrikam 模块，Fabrikam 模块安装程序将模块位置添加到**PSModulePath**环境变量的值。</span><span class="sxs-lookup"><span data-stu-id="92b9c-161">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="92b9c-162">在公共文件目录中安装模块</span><span class="sxs-lookup"><span data-stu-id="92b9c-162">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="92b9c-163">如果某个模块由产品的多个组件或产品的多个版本使用，请在%ProgramFiles%\Common Files\Modules 子目录的模块特定子目录中安装该模块。</span><span class="sxs-lookup"><span data-stu-id="92b9c-163">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="92b9c-164">在下面的示例中，Fabrikam 模块安装在 `%ProgramFiles%\Common Files\Modules` 子目录的 Fabrikam 子目录中。</span><span class="sxs-lookup"><span data-stu-id="92b9c-164">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the `%ProgramFiles%\Common Files\Modules` subdirectory.</span></span> <span data-ttu-id="92b9c-165">请注意，每个模块都位于模块子目录中各自的子目录中。</span><span class="sxs-lookup"><span data-stu-id="92b9c-165">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

<span data-ttu-id="92b9c-166">然后，安装程序确保**PSModulePath**环境变量的值包含公共文件模块子目录的路径。</span><span class="sxs-lookup"><span data-stu-id="92b9c-166">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

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

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="92b9c-167">安装模块的多个版本</span><span class="sxs-lookup"><span data-stu-id="92b9c-167">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="92b9c-168">若要安装相同模块的多个版本，请使用以下过程。</span><span class="sxs-lookup"><span data-stu-id="92b9c-168">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="92b9c-169">为模块的每个版本创建一个目录。</span><span class="sxs-lookup"><span data-stu-id="92b9c-169">Create a directory for each version of the module.</span></span> <span data-ttu-id="92b9c-170">在目录名称中包含版本号。</span><span class="sxs-lookup"><span data-stu-id="92b9c-170">Include the version number in the directory name.</span></span>
2. <span data-ttu-id="92b9c-171">为每个版本的模块创建一个模块清单。</span><span class="sxs-lookup"><span data-stu-id="92b9c-171">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="92b9c-172">在清单中**ModuleVersion**键的值中，输入模块版本号。</span><span class="sxs-lookup"><span data-stu-id="92b9c-172">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="92b9c-173">将清单文件（. psd1）保存在模块的特定于版本的目录中。</span><span class="sxs-lookup"><span data-stu-id="92b9c-173">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>
3. <span data-ttu-id="92b9c-174">将模块根文件夹路径添加到**PSModulePath**环境变量的值，如以下示例中所示。</span><span class="sxs-lookup"><span data-stu-id="92b9c-174">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="92b9c-175">若要导入特定版本的模块，最终用户可以使用[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 的 `MinimumVersion` 或 `RequiredVersion` 参数。</span><span class="sxs-lookup"><span data-stu-id="92b9c-175">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="92b9c-176">例如，如果 Fabrikam 模块在版本8.0 和9.0 中可用，则 Fabrikam 模块目录结构可能类似于以下内容。</span><span class="sxs-lookup"><span data-stu-id="92b9c-176">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

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

<span data-ttu-id="92b9c-177">安装程序会将这两个模块路径添加到**PSModulePath**环境变量值。</span><span class="sxs-lookup"><span data-stu-id="92b9c-177">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="92b9c-178">完成这些步骤后， [get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet 的**ListAvailable**参数将获取 Fabrikam 模块。</span><span class="sxs-lookup"><span data-stu-id="92b9c-178">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="92b9c-179">若要导入特定模块，请使用[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 的 `MinimumVersion` 或 `RequiredVersion` 参数。</span><span class="sxs-lookup"><span data-stu-id="92b9c-179">To import a particular module, use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="92b9c-180">如果两个模块都导入到同一会话中，并且模块包含具有相同名称的 cmdlet，则最后导入的 cmdlet 在会话中有效。</span><span class="sxs-lookup"><span data-stu-id="92b9c-180">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="92b9c-181">处理命令名称冲突</span><span class="sxs-lookup"><span data-stu-id="92b9c-181">Handling Command Name Conflicts</span></span>

<span data-ttu-id="92b9c-182">当模块导出的命令与用户会话中的命令具有相同的名称时，可能会发生命令名称冲突。</span><span class="sxs-lookup"><span data-stu-id="92b9c-182">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="92b9c-183">当会话中包含两个具有相同名称的命令时，Windows PowerShell 将运行优先的命令类型。</span><span class="sxs-lookup"><span data-stu-id="92b9c-183">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="92b9c-184">如果会话中包含两个具有相同名称和相同类型的命令，则 Windows PowerShell 将运行最近添加到会话中的命令。</span><span class="sxs-lookup"><span data-stu-id="92b9c-184">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="92b9c-185">若要运行默认情况下不运行的命令，用户可以使用模块名称限定命令名称。</span><span class="sxs-lookup"><span data-stu-id="92b9c-185">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="92b9c-186">例如，如果会话包含 `Get-Date` 函数和 `Get-Date` cmdlet，则默认情况下，Windows PowerShell 将运行该函数。</span><span class="sxs-lookup"><span data-stu-id="92b9c-186">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="92b9c-187">若要运行 cmdlet，请在命令前面加上模块名称，例如：</span><span class="sxs-lookup"><span data-stu-id="92b9c-187">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="92b9c-188">若要防止名称冲突，模块作者可以使用模块清单中的**DefaultCommandPrefix**键为从该模块导出的所有命令指定名词前缀。</span><span class="sxs-lookup"><span data-stu-id="92b9c-188">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="92b9c-189">用户可以使用 `Import-Module` cmdlet 的**prefix**参数来使用替代前缀。</span><span class="sxs-lookup"><span data-stu-id="92b9c-189">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="92b9c-190">**Prefix**参数的值优先于**DefaultCommandPrefix**键的值。</span><span class="sxs-lookup"><span data-stu-id="92b9c-190">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="92b9c-191">另请参阅</span><span class="sxs-lookup"><span data-stu-id="92b9c-191">See Also</span></span>

[<span data-ttu-id="92b9c-192">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="92b9c-192">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="92b9c-193">编写 Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="92b9c-193">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
