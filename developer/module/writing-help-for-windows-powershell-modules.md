---
title: 为 Windows PowerShell 模块编写帮助 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854063"
---
# <a name="writing-help-for-windows-powershell-modules"></a><span data-ttu-id="0b6e8-102">编写针对 Windows PowerShell 模块的帮助</span><span class="sxs-lookup"><span data-stu-id="0b6e8-102">Writing Help for Windows PowerShell Modules</span></span>

<span data-ttu-id="0b6e8-103">Windows PowerShell 模块可以包含有关该模块以及模块成员，如 cmdlet、 提供程序、 函数和脚本帮助主题。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-103">Windows PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="0b6e8-104">`Get-Help` Cmdlet 显示模块的帮助主题中的相同的格式为它的其他 Windows PowerShell 项，显示的帮助，而用户使用标准`Get-Help`命令以获取帮助主题。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-104">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other Windows PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="0b6e8-105">本文档介绍的格式和模块帮助主题的正确位置并建议模块的帮助内容的指导原则。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-105">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="0b6e8-106">类型的模块的帮助</span><span class="sxs-lookup"><span data-stu-id="0b6e8-106">Types of Module Help</span></span>

<span data-ttu-id="0b6e8-107">模块可以包含以下类型的帮助。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-107">A module can include the following types of Help.</span></span>

- <span data-ttu-id="0b6e8-108">**Cmdlet 帮助**。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-108">**Cmdlet Help**.</span></span> <span data-ttu-id="0b6e8-109">介绍在模块中的 cmdlet 的帮助主题是使用命令的 XML 文件可帮助架构</span><span class="sxs-lookup"><span data-stu-id="0b6e8-109">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="0b6e8-110">**提供程序帮助**。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-110">**Provider Help**.</span></span> <span data-ttu-id="0b6e8-111">描述在模块中的提供程序的帮助主题是使用提供程序的 XML 文件可帮助架构。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-111">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="0b6e8-112">**函数帮助**。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-112">**Function Help**.</span></span> <span data-ttu-id="0b6e8-113">可以使用命令的 XML 文件可帮助架构或函数，或在脚本或脚本模块中基于注释的帮助主题介绍在模块中的函数的帮助主题</span><span class="sxs-lookup"><span data-stu-id="0b6e8-113">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="0b6e8-114">**脚本帮助**。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-114">**Script Help**.</span></span> <span data-ttu-id="0b6e8-115">可以使用命令的 XML 文件可帮助架构或在脚本或脚本模块中基于注释的帮助主题介绍在模块中的脚本的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-115">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="0b6e8-116">**（"关于"） 帮助**。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-116">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="0b6e8-117">描述的模块，并且其成员还将说明如何成员可以共同用于执行任务，您可以使用概念 （"关于"） 帮助主题。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-117">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span> <span data-ttu-id="0b6e8-118">概念帮助主题是使用 Unicode (utf-8) 编码的文本文件。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-118">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="0b6e8-119">文件名称必须使用`about_<name>.help.txt`格式，如 about_MyModule.help.txt。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-119">The file name must use the `about_<name>.help.txt` format, such as about_MyModule.help.txt.</span></span> <span data-ttu-id="0b6e8-120">默认情况下，Windows PowerShell 包括超过 100 个概念有关帮助主题，并且它们的格式如下例所示。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-120">By default, Windows PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

  ```
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a><span data-ttu-id="0b6e8-121">模块的帮助的位置</span><span class="sxs-lookup"><span data-stu-id="0b6e8-121">Placement of Module Help</span></span>

<span data-ttu-id="0b6e8-122">`Get-Help` Cmdlet 查找模块在模块目录的特定于语言的子目录中的帮助主题文件。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-122">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="0b6e8-123">例如，以下目录结构关系图显示了有关 SampleModule 模块的帮助主题的位置。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-123">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> <span data-ttu-id="0b6e8-124">在示例中，  *\<ModulePath >* 占位符表示中的路径之一`PSModulePath`环境变量，如 $home\Documents\Modules、 $pshome\Modules 或用户指定的自定义路径。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-124">In the example, the *\<ModulePath>* placeholder represents one of the paths in the `PSModulePath` environment variable, such as $home\Documents\Modules, $pshome\Modules, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="0b6e8-125">获取模块的帮助</span><span class="sxs-lookup"><span data-stu-id="0b6e8-125">Getting Module Help</span></span>

<span data-ttu-id="0b6e8-126">当用户将模块导入到会话时，该模块的帮助主题是导入到连同该模块的会话。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-126">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="0b6e8-127">可以列出在模块清单中，文件列表项的值中的帮助主题文件，但不是受影响的帮助主题`Export-ModuleMember`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-127">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="0b6e8-128">你可以提供不同的语言中的模块的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-128">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="0b6e8-129">`Get-Help` Cmdlet 会自动显示为控制面板中的区域和语言选项项中的当前用户指定的语言中的模块的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-129">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="0b6e8-130">在 Windows Vista 和更高版本的 Windows，`Get-Help`搜索根据建立 Windows 语言回退标准在模块目录的特定于语言的子目录中的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-130">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="0b6e8-131">从运行的 Windows PowerShell 3.0 开始`Get-Help`cmdlet 或函数的命令触发自动导入的模块。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-131">Beginning in Windows PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="0b6e8-132">`Get-Help` Cmdlet 模块中将立即显示帮助主题的内容。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-132">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="0b6e8-133">如果该模块不包含帮助主题，并且不会有帮助主题中用户的计算机上的模块命令`Get-Help`显示自动生成的帮助。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-133">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="0b6e8-134">自动生成的帮助命令语法、 参数和输入和输出类型，包括但不包括任何说明。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-134">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="0b6e8-135">自动生成帮助中包含文本，引导用户尝试使用`Update-Help`cmdlet 以从 Internet 或文件共享下载有关命令的帮助。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-135">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the Internet or a file share.</span></span> <span data-ttu-id="0b6e8-136">它还建议使用**联机**参数的`Get-Help`cmdlet 来获取帮助主题的联机版本。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-136">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="0b6e8-137">支持可更新的帮助</span><span class="sxs-lookup"><span data-stu-id="0b6e8-137">Supporting Updatable Help</span></span>

<span data-ttu-id="0b6e8-138">用户的 Windows PowerShell 3.0 和更高版本的 Windows PowerShell 可以下载并安装的模块更新的帮助文件，从 Internet 还是从本地文件共享。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-138">Users of Windows PowerShell 3.0 and later versions of Windows PowerShell can download and install updated help files for a module from the Internet or from a local file share.</span></span> <span data-ttu-id="0b6e8-139">`Update-Help`和`Save-Help`cmdlet 隐藏用户的管理详细信息。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-139">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="0b6e8-140">用户在运行`Update-Help`cmdlet，然后使用`Get-Help`cmdlet 来读取在 Windows PowerShell 命令提示符下的模块的最新帮助文件。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-140">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the Windows PowerShell command prompt.</span></span> <span data-ttu-id="0b6e8-141">用户不需要重新启动 Windows 或 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-141">Users do not need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="0b6e8-142">防火墙以及那些没有 Internet 访问权限的用户可以使用可更新帮助。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-142">Users behind firewalls and those without Internet access can use Updatable Help, as well.</span></span> <span data-ttu-id="0b6e8-143">管理员具有 Internet 访问，请使用`Save-Help`cmdlet 来下载并安装到文件共享的最新帮助文件。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-143">Administrators with Internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="0b6e8-144">然后，用户使用**路径**参数的`Update-Help`cmdlet 来获取最新帮助文件从文件共享。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-144">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="0b6e8-145">模块作者可以在模块中包含帮助文件，并使用可更新帮助以更新的帮助文件，或忽略模块的帮助文件并使用可更新的帮助来安装并更新它们。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-145">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="0b6e8-146">有关可更新帮助的详细信息，请参阅[支持可更新帮助](./supporting-updatable-help.md)。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-146">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="0b6e8-147">支持联机帮助</span><span class="sxs-lookup"><span data-stu-id="0b6e8-147">Supporting Online Help</span></span>

<span data-ttu-id="0b6e8-148">不能或不安装的用户更新其计算机上的文件通常依赖于模块的帮助主题的联机版本的帮助。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-148">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="0b6e8-149">**联机**参数的`Get-Help`cmdlet 及其默认 Internet 浏览器中打开 cmdlet 或用户的高级的函数帮助主题的联机版本。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-149">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default Internet browser.</span></span>

<span data-ttu-id="0b6e8-150">`Get-Help` Cmdlet 使用的值**HelpUri** cmdlet 或函数，以便查找帮助主题的联机版本的属性。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-150">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="0b6e8-151">从 Windows PowerShell 3.0 开始，可帮助用户通过在 cmdlet 类上定义的 HelpUri 属性中查找 cmdlet 和函数的帮助主题的联机版本或**HelpUri**属性的**CmdletBinding**属性。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-151">Beginning in Windows PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="0b6e8-152">属性的值为的值**HelpUri** cmdlet 或函数的属性。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-152">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="0b6e8-153">有关详细信息，请参阅[支持联机帮助](./supporting-online-help.md)。</span><span class="sxs-lookup"><span data-stu-id="0b6e8-153">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0b6e8-154">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0b6e8-154">See Also</span></span>

[<span data-ttu-id="0b6e8-155">编写 Windows PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="0b6e8-155">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="0b6e8-156">支持可更新帮助</span><span class="sxs-lookup"><span data-stu-id="0b6e8-156">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="0b6e8-157">支持联机帮助</span><span class="sxs-lookup"><span data-stu-id="0b6e8-157">Supporting Online Help</span></span>](./supporting-online-help.md)