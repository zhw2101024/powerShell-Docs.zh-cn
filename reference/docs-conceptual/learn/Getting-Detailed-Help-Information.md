---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 获取详细的帮助信息
ms.openlocfilehash: e722eb8a0ca13e3d2de864314775a0a9fa578390
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417658"
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="3694e-103">获取详细的帮助信息</span><span class="sxs-lookup"><span data-stu-id="3694e-103">Getting detailed help information</span></span>

<span data-ttu-id="3694e-104">PowerShell 包含了详细的帮助文章，其中解释了 PowerShell 概念和 PowerShell 语言。</span><span class="sxs-lookup"><span data-stu-id="3694e-104">PowerShell includes detailed Help articles that explain PowerShell concepts and the PowerShell language.</span></span> <span data-ttu-id="3694e-105">还有针对每个 cmdlet 和提供程序的帮助文章，以及针对许多函数和脚本的帮助文章。</span><span class="sxs-lookup"><span data-stu-id="3694e-105">There are also Help articles for each cmdlet and provider and for many functions and scripts.</span></span>

<span data-ttu-id="3694e-106">可以在命令提示符下显示这些帮助文章，或在 [PowerShell](/powershell/scripting/overview) 文档中在线查看这些文章的最近更新版本。</span><span class="sxs-lookup"><span data-stu-id="3694e-106">You can display these Help articles at the command prompt or view the most recently updated versions of these articles in the [PowerShell](/powershell/scripting/overview) documentation online.</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="3694e-107">获取有关 cmdlet 的帮助</span><span class="sxs-lookup"><span data-stu-id="3694e-107">Getting help for cmdlets</span></span>

<span data-ttu-id="3694e-108">若要获取有关 PowerShell cmdlet 的帮助，请使用 [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3694e-108">To get Help about PowerShell cmdlets, use the [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet.</span></span> <span data-ttu-id="3694e-109">例如，若要获取 `Get-ChildItem` cmdlet 的帮助，请键入：</span><span class="sxs-lookup"><span data-stu-id="3694e-109">For example, to get Help for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="3694e-110">或</span><span class="sxs-lookup"><span data-stu-id="3694e-110">or</span></span>

```powershell
Get-ChildItem -?
```

<span data-ttu-id="3694e-111">甚至可以获取有关 Get-Help cmdlet 的帮助。</span><span class="sxs-lookup"><span data-stu-id="3694e-111">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="3694e-112">例如：</span><span class="sxs-lookup"><span data-stu-id="3694e-112">For example:</span></span>

```powershell
Get-Help Get-Help
```

<span data-ttu-id="3694e-113">若要在会话中获取所有 cmdlet 帮助文章的列表，请键入：</span><span class="sxs-lookup"><span data-stu-id="3694e-113">To get a list of all the cmdlet Help articles in your session, type:</span></span>

```powershell
Get-Help -Category Cmdlet
```

<span data-ttu-id="3694e-114">若要一次显示每篇帮助文章的一页，请使用 `help` 函数或其别名 `man`。</span><span class="sxs-lookup"><span data-stu-id="3694e-114">To display one page of each Help article at a time, use the `help` function or its alias `man`.</span></span>
<span data-ttu-id="3694e-115">例如，若要显示 `Get-ChildItem` cmdlet 的帮助信息，请键入</span><span class="sxs-lookup"><span data-stu-id="3694e-115">For example, to display Help for the `Get-ChildItem` cmdlet, type</span></span>

```powershell
man Get-ChildItem
```

<span data-ttu-id="3694e-116">或</span><span class="sxs-lookup"><span data-stu-id="3694e-116">or</span></span>

```powershell
help Get-ChildItem
```

<span data-ttu-id="3694e-117">若要显示详细信息，请使用 `Get-Help` cmdlet 的 Detailed  参数。</span><span class="sxs-lookup"><span data-stu-id="3694e-117">To display detailed information, use the **Detailed** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="3694e-118">例如，若要获取有关 `Get-ChildItem` cmdlet 的详细信息，请键入：</span><span class="sxs-lookup"><span data-stu-id="3694e-118">For example, to get detailed information about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Detailed
```

<span data-ttu-id="3694e-119">若要显示帮助文章中的所有内容，请使用 `Get-Help` cmdlet 的 Full  参数。</span><span class="sxs-lookup"><span data-stu-id="3694e-119">To display all content in the Help article, use the **Full** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="3694e-120">例如，若要显示 `Get-ChildItem` cmdlet 的帮助文章中的所有内容，请键入：</span><span class="sxs-lookup"><span data-stu-id="3694e-120">For example, to display all content in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Full
```

<span data-ttu-id="3694e-121">若要获取有关 cmdlet 的参数的详细帮助，请使用 `Get-Help` cmdlet 的 Parameter  参数。</span><span class="sxs-lookup"><span data-stu-id="3694e-121">To get detailed Help about the parameters of a cmdlet, use the **Parameter** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="3694e-122">例如，若要获取 `Get-ChildItem` cmdlet 的所有参数的详细帮助，请键入：</span><span class="sxs-lookup"><span data-stu-id="3694e-122">For example, to get detailed Help for all of the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Parameter *
```

<span data-ttu-id="3694e-123">若要仅显示帮助文章中的示例，请使用 `Get-Help` 的 Examples  参数。</span><span class="sxs-lookup"><span data-stu-id="3694e-123">To display only the examples in a Help article, use the **Examples** parameter of the `Get-Help`.</span></span>
<span data-ttu-id="3694e-124">例如，若要仅显示 `Get-ChildItem` cmdlet 的帮助文章中的示例，请键入：</span><span class="sxs-lookup"><span data-stu-id="3694e-124">For example, to display only the examples in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Examples
```

<span data-ttu-id="3694e-125">有关如何为你编写的 cmdlet 编写帮助文章的信息，请参阅[如何编写 Cmdlet 帮助](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)主题。</span><span class="sxs-lookup"><span data-stu-id="3694e-125">For information about how to write Help articles for the cmdlets that you write, see [How to Write Cmdlet Help](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="3694e-126">获取概念帮助</span><span class="sxs-lookup"><span data-stu-id="3694e-126">Getting conceptual help</span></span>

<span data-ttu-id="3694e-127">`Get-Help` cmdlet 也会显示有关 PowerShell 中的概念文章（包括有关 PowerShell 语言的文章）的信息。</span><span class="sxs-lookup"><span data-stu-id="3694e-127">The `Get-Help` cmdlet also displays information about conceptual articles in PowerShell, including articles about the PowerShell language.</span></span> <span data-ttu-id="3694e-128">概念帮助文章以“about_”前缀开头，例如 about_line_editing。</span><span class="sxs-lookup"><span data-stu-id="3694e-128">Conceptual Help articles begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="3694e-129">（概念文章的名称必须用英文输入，即使在非英语版本的 PowerShell 中也是如此。）</span><span class="sxs-lookup"><span data-stu-id="3694e-129">(The name of the conceptual article must be entered in English even on non-English versions of PowerShell.)</span></span>

<span data-ttu-id="3694e-130">若要显示概念文章的列表，请键入：</span><span class="sxs-lookup"><span data-stu-id="3694e-130">To display a list of conceptual articles, type:</span></span>

```powershell
Get-Help about_*
```

<span data-ttu-id="3694e-131">若要显示某一特别的帮助文章，请键入文章名称，例如：</span><span class="sxs-lookup"><span data-stu-id="3694e-131">To display a particular Help article, type the article name, for example:</span></span>

```powershell
Get-Help about_command_syntax
```

<span data-ttu-id="3694e-132">`Get-Help` 的参数（例如 Detailed  、Parameter  和 Examples  ）对概念帮助文章的显示没有影响。</span><span class="sxs-lookup"><span data-stu-id="3694e-132">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of conceptual Help articles.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="3694e-133">获取有关提供程序的帮助</span><span class="sxs-lookup"><span data-stu-id="3694e-133">Getting help about providers</span></span>

<span data-ttu-id="3694e-134">`Get-Help` cmdlet 显示有关 PowerShell 提供程序的信息。</span><span class="sxs-lookup"><span data-stu-id="3694e-134">The `Get-Help` cmdlet displays information about PowerShell providers.</span></span> <span data-ttu-id="3694e-135">若要获取有关提供程序的帮助，请键入 `Get-Help`，后跟提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="3694e-135">To get Help for a provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="3694e-136">例如，若要获取有关 Registry 提供程序的帮助，请键入：</span><span class="sxs-lookup"><span data-stu-id="3694e-136">For example, to get Help for the Registry provider, type:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="3694e-137">若要获取会话中的所有提供程序帮助文章的列表，请键入</span><span class="sxs-lookup"><span data-stu-id="3694e-137">To get a list of all the provider Help articles in your session, type</span></span>

```powershell
Get-Help -Category provider
```

<span data-ttu-id="3694e-138">`Get-Help` 的参数（例如 Detailed  、Parameter  和 Examples  ）对提供程序帮助文章的显示没有影响。</span><span class="sxs-lookup"><span data-stu-id="3694e-138">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of provider Help articles.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="3694e-139">获取有关脚本和函数的帮助</span><span class="sxs-lookup"><span data-stu-id="3694e-139">Getting help about scripts and functions</span></span>

<span data-ttu-id="3694e-140">PowerShell 中的许多脚本和函数都有帮助文章。</span><span class="sxs-lookup"><span data-stu-id="3694e-140">Many scripts and functions in PowerShell have Help articles.</span></span> <span data-ttu-id="3694e-141">使用 `Get-Help` cmdlet 显示脚本和函数的帮助文章。</span><span class="sxs-lookup"><span data-stu-id="3694e-141">Use the `Get-Help` cmdlet to display the Help articles for scripts and functions.</span></span>

<span data-ttu-id="3694e-142">若要显示有关某个函数的帮助，请键入 `Get-Help`，后跟函数名称。</span><span class="sxs-lookup"><span data-stu-id="3694e-142">To display the Help for a function, type `Get-Help` followed by the function name.</span></span> <span data-ttu-id="3694e-143">例如，若要获取有关 `Disable-PSRemoting` 函数的帮助，请键入：</span><span class="sxs-lookup"><span data-stu-id="3694e-143">For example, to get Help for the `Disable-PSRemoting` function, type:</span></span>

```powershell
Get-Help Disable-PSRemoting
```

<span data-ttu-id="3694e-144">若要显示有关某个脚本的帮助，请键入该脚本文件的路径。</span><span class="sxs-lookup"><span data-stu-id="3694e-144">To display the Help for a script, type the path to the script file.</span></span> <span data-ttu-id="3694e-145">如果该脚本不位于路径环境变量中列出的路径中，则必须使用完全限定的路径。</span><span class="sxs-lookup"><span data-stu-id="3694e-145">If the script is not in a path listed in the Path environment variable, you must use the fully qualified path.</span></span>

<span data-ttu-id="3694e-146">例如，如果名为“TestScript.ps1”的脚本位于 C:\\PS-Test 目录中，要显示有关该脚本的帮助文章，请键入：</span><span class="sxs-lookup"><span data-stu-id="3694e-146">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help article for the script, type:</span></span>

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="3694e-147">用于显示 cmdlet 帮助的参数也适用于脚本和函数帮助。</span><span class="sxs-lookup"><span data-stu-id="3694e-147">The parameters that are designed for displaying cmdlet Help work for script and function Help, too.</span></span> <span data-ttu-id="3694e-148">但是，在运行 `Get-Help *` 时，不会显示函数和脚本的帮助。</span><span class="sxs-lookup"><span data-stu-id="3694e-148">However, help for functions and scripts is not shown when you run `Get-Help *`.</span></span>

<span data-ttu-id="3694e-149">有关为函数和脚本编写帮助文章的信息，请参阅以下文章：</span><span class="sxs-lookup"><span data-stu-id="3694e-149">For information about writing Help articles for your functions and scripts, see the following articles:</span></span>

- [<span data-ttu-id="3694e-150">about_Functions</span><span class="sxs-lookup"><span data-stu-id="3694e-150">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="3694e-151">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="3694e-151">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="3694e-152">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="3694e-152">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a><span data-ttu-id="3694e-153">在线获取帮助</span><span class="sxs-lookup"><span data-stu-id="3694e-153">Getting help online</span></span>

<span data-ttu-id="3694e-154">在线查看帮助文章是获得帮助的最佳方式之一。</span><span class="sxs-lookup"><span data-stu-id="3694e-154">Viewing the Help articles online is one of the best ways to get help.</span></span> <span data-ttu-id="3694e-155">在线文章更易于更新并提供最新内容。</span><span class="sxs-lookup"><span data-stu-id="3694e-155">Online articles are easier to update and provide the most current content.</span></span>

<span data-ttu-id="3694e-156">若要在线获取帮助，请使用 `Get-Help` cmdlet 的 Online  参数。</span><span class="sxs-lookup"><span data-stu-id="3694e-156">To get Help online, use the **Online** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="3694e-157">PowerShell 附带的所有帮助文章（包括提供程序帮助和概念(关于)帮助文章），都可以在 [PowerShell](/powershell/scripting/powershell-scripting) 文档中在线获取。</span><span class="sxs-lookup"><span data-stu-id="3694e-157">All the Help articles that come with PowerShell, including provider Help and conceptual (About) Help articles, are available online in the [PowerShell](/powershell/scripting/powershell-scripting) documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="3694e-158">不能将 Online  参数用于概念 (about_\*) 或提供程序帮助文章。</span><span class="sxs-lookup"><span data-stu-id="3694e-158">You can't use the **Online** parameter with conceptual (about_\*) or provider Help articles.</span></span>
> <span data-ttu-id="3694e-159">在线帮助一个可选功能，并不适用于每一个 cmdlet、函数或脚本。</span><span class="sxs-lookup"><span data-stu-id="3694e-159">Online help is optional, so it does not work for every cmdlet, function, or script.</span></span>

<span data-ttu-id="3694e-160">例如，若要获取有关 `Get-ChildItem` cmdlett 的帮助文章的在线版本，请键入：</span><span class="sxs-lookup"><span data-stu-id="3694e-160">For example, to get the online version of the Help article about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Online
```

<span data-ttu-id="3694e-161">PowerShell 在默认浏览器中打开文章。</span><span class="sxs-lookup"><span data-stu-id="3694e-161">PowerShell opens the article in your default browser.</span></span> <span data-ttu-id="3694e-162">如果该帮助文章支持在线帮助，也可以查看该帮助文章的 URL。</span><span class="sxs-lookup"><span data-stu-id="3694e-162">If online Help is supported for a Help article, you can also view the URL of the Help article.</span></span> <span data-ttu-id="3694e-163">URL 将显示在帮助文章的“相关链接”部分中。</span><span class="sxs-lookup"><span data-stu-id="3694e-163">The URL appears in the Related Links section of a Help article.</span></span>

<span data-ttu-id="3694e-164">例如，若要查看 Add-Computer cmdlet 的在线版本的 URL，请键入：</span><span class="sxs-lookup"><span data-stu-id="3694e-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```powershell
Get-Help Add-Computer
```

<span data-ttu-id="3694e-165">该文章“相关链接”部分的第一行如下所示。</span><span class="sxs-lookup"><span data-stu-id="3694e-165">The first line in the Related Links section of the article is shown below.</span></span>

```Output
Online version: https://go.microsoft.com/fwlink/?LinkId=821564
```

<span data-ttu-id="3694e-166">有关如何提供帮助文章的在线支持的信息，请参阅 [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)。</span><span class="sxs-lookup"><span data-stu-id="3694e-166">For information about how to provide online support for your Help articles, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

## <a name="see-also"></a><span data-ttu-id="3694e-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3694e-167">See also</span></span>

- [<span data-ttu-id="3694e-168">about_Functions</span><span class="sxs-lookup"><span data-stu-id="3694e-168">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="3694e-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="3694e-169">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="3694e-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="3694e-170">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [<span data-ttu-id="3694e-171">Get-Help</span><span class="sxs-lookup"><span data-stu-id="3694e-171">Get-Help</span></span>](/powershell/module/microsoft.powershell.core/get-help)
