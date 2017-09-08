---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "获取详细的帮助信息"
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: c786ce089073abccdf186dc1d9e8ee383f83655d
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2017
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="600d4-103">获取详细的帮助信息</span><span class="sxs-lookup"><span data-stu-id="600d4-103">Getting Detailed Help Information</span></span>
<span data-ttu-id="600d4-104">Windows PowerShell 包含了详细的帮助主题，其中解释了 Windows PowerShell 概念和 Windows PowerShell 语言。</span><span class="sxs-lookup"><span data-stu-id="600d4-104">Windows PowerShell includes detailed Help topics that explain Windows PowerShell concepts and the Windows PowerShell language.</span></span> <span data-ttu-id="600d4-105">还有针对每个 cmdlet 和提供程序的帮助主题，以及针对许多函数和脚本的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="600d4-105">There are also Help topics for each cmdlet and provider and Help topics for many functions and scripts.</span></span>

<span data-ttu-id="600d4-106">可以在命令提示符下显示这些帮助主题，或在 Microsoft TechNet 库中查看这些主题的最近更新的版本。</span><span class="sxs-lookup"><span data-stu-id="600d4-106">You can display these Help topics at the command prompt or view the most recently updated versions of these topics in the Microsoft TechNet Library.</span></span> <span data-ttu-id="600d4-107">许多托管 Windows PowerShell 的程序（如 Windows PowerShell 集成脚本环境）提供了其他帮助功能，如区分上下文的帮助和编译的帮助文件 (.chm)。</span><span class="sxs-lookup"><span data-stu-id="600d4-107">Many programs that host Windows PowerShell, such as Windows PowerShell Integrated Scripting Environment, provide additional Help features, such as context-sensitive Help and compiled Help file (.chm).</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="600d4-108">获取有关 Cmdlet 的帮助</span><span class="sxs-lookup"><span data-stu-id="600d4-108">Getting Help for Cmdlets</span></span>
<span data-ttu-id="600d4-109">若要获取有关 Windows PowerShell cmdlet 的帮助，请使用 [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="600d4-109">To get Help about Windows PowerShell cmdlets, use the [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet.</span></span> <span data-ttu-id="600d4-110">例如，若要获取 [Get-ChildItem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet 的帮助，请键入：</span><span class="sxs-lookup"><span data-stu-id="600d4-110">For example, to get Help for the [Get-ChildItem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet, type:</span></span>

```
get-help get-childitem
```

<span data-ttu-id="600d4-111">或</span><span class="sxs-lookup"><span data-stu-id="600d4-111">or</span></span>

```
get-childitem -?
```

<span data-ttu-id="600d4-112">甚至可以获取有关 Get-Help cmdlet 的帮助。</span><span class="sxs-lookup"><span data-stu-id="600d4-112">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="600d4-113">例如：</span><span class="sxs-lookup"><span data-stu-id="600d4-113">For example:</span></span>

```
get-help get-help
```

<span data-ttu-id="600d4-114">若要在会话中获取所有 cmdlet 帮助主题的列表，请键入：</span><span class="sxs-lookup"><span data-stu-id="600d4-114">To get a list of all the cmdlet Help topics in your session, type:</span></span>

```
get-help -category cmdlet
```

<span data-ttu-id="600d4-115">若要一次显示每个帮助主题一页，请使用 **help** 函数或其别名 **man**。</span><span class="sxs-lookup"><span data-stu-id="600d4-115">To display one page of each Help topic at a time, use the **help** function or its alias **man**.</span></span> <span data-ttu-id="600d4-116">例如，若要显示有关 Get-ChildItem cmdlet 的帮助，请键入</span><span class="sxs-lookup"><span data-stu-id="600d4-116">For example, to display Help for the Get-ChildItem cmdlet, type</span></span>

```
man get-childitem
```

<span data-ttu-id="600d4-117">或</span><span class="sxs-lookup"><span data-stu-id="600d4-117">or</span></span>

```
help get-childitem
```

<span data-ttu-id="600d4-118">若要显示有关 cmdlet、函数或脚本的详细信息，包括其参数的说明和其用法的示例，请使用 Get-Help cmdlet 的 *Detailed* 参数。</span><span class="sxs-lookup"><span data-stu-id="600d4-118">To display detailed information about a cmdlet, function, or script, including descriptions of its parameters and examples of its use, use the *Detailed* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="600d4-119">例如，若要获取有关 Get-ChildItem cmdlet 的详细信息，请键入：</span><span class="sxs-lookup"><span data-stu-id="600d4-119">For example, to get detailed information about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -detailed
```

<span data-ttu-id="600d4-120">若要显示帮助主题中的所有内容，请使用 Get-Help cmdlet 的 *Full* 参数。</span><span class="sxs-lookup"><span data-stu-id="600d4-120">To display all content in the Help topic, use the *Full* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="600d4-121">例如，若要显示 Get-ChildItem cmdlet 的帮助主题中的所有内容，请键入：</span><span class="sxs-lookup"><span data-stu-id="600d4-121">For example, to display all content in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -full
```

<span data-ttu-id="600d4-122">若要获取有关 cmdlet 的参数的详细帮助，请使用 Get-Help cmdlet 的 *Parameter* 参数。</span><span class="sxs-lookup"><span data-stu-id="600d4-122">To get detailed Help about the parameters of a cmdlet, use the *Parameter* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="600d4-123">例如，若要获取 Get-ChildItem cmdlet 的所有参数的详细帮助，请键入：</span><span class="sxs-lookup"><span data-stu-id="600d4-123">For example, to get detailed Help for all of the parameters of the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -parameter *
```

<span data-ttu-id="600d4-124">若要仅显示帮助主题中的示例，请使用 Get-Help 的 *Example* 参数。</span><span class="sxs-lookup"><span data-stu-id="600d4-124">To display only the examples in a Help topic, use the *Example* parameter of the Get-Help.</span></span> <span data-ttu-id="600d4-125">例如，若要仅显示 Get-ChildItem cmdlet 的帮助主题中的示例，请键入：</span><span class="sxs-lookup"><span data-stu-id="600d4-125">For example, to display only the examples in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -examples
```

<span data-ttu-id="600d4-126">有关如何为你编写的 cmdlet 编写帮助主题的信息，请参阅 MSDN 库中的 [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415)（如何编写 Cmdlet 帮助）主题。</span><span class="sxs-lookup"><span data-stu-id="600d4-126">For information about how to write Help topics for the cmdlets that you write, see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="600d4-127">获取概念帮助</span><span class="sxs-lookup"><span data-stu-id="600d4-127">Getting Conceptual Help</span></span>
<span data-ttu-id="600d4-128">Get-Help cmdlet 也将显示有关 Windows PowerShell 中的概念主题（包括有关 Windows PowerShell 语言的主题）的信息。</span><span class="sxs-lookup"><span data-stu-id="600d4-128">The Get-Help cmdlet also displays information about conceptual topics in Windows PowerShell, including topics about the Windows PowerShell language.</span></span> <span data-ttu-id="600d4-129">概念主题以“about_”前缀开头，例如 about_line_editing。</span><span class="sxs-lookup"><span data-stu-id="600d4-129">Conceptual Help topics begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="600d4-130">（概念主题的名称必须用英文输入，即使在非英语版本的 Windows PowerShell 中也是如此。）</span><span class="sxs-lookup"><span data-stu-id="600d4-130">(The name of the conceptual topic must be entered in English even on non-English versions of Windows PowerShell.)</span></span>

<span data-ttu-id="600d4-131">若要显示概念主题的列表，请键入：</span><span class="sxs-lookup"><span data-stu-id="600d4-131">To display a list of conceptual topics, type:</span></span>

```
get-help about_*
```

<span data-ttu-id="600d4-132">若要显示某一特别的帮助主题，请键入主题名称，例如：</span><span class="sxs-lookup"><span data-stu-id="600d4-132">To display a particular Help topic, type the topic name, for example:</span></span>

```
get-help about_command_syntax
```

<span data-ttu-id="600d4-133">Get-Help 的参数，例如 *Detailed*、*Parameter* 和 *Examples*，它们对概念帮助主题的显示没有影响。</span><span class="sxs-lookup"><span data-stu-id="600d4-133">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of conceptual Help topics.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="600d4-134">获取有关提供程序的帮助</span><span class="sxs-lookup"><span data-stu-id="600d4-134">Getting Help About Providers</span></span>
<span data-ttu-id="600d4-135">Get-Help cmdlet 显示有关 Windows PowerShell 提供程序的信息。</span><span class="sxs-lookup"><span data-stu-id="600d4-135">The Get-Help cmdlet displays information about Windows PowerShell providers.</span></span> <span data-ttu-id="600d4-136">若要获取有关提供程序的帮助，请键入“Get-Help”，后跟提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="600d4-136">To get Help for a provider, type "Get-Help" followed by the provider name.</span></span> <span data-ttu-id="600d4-137">例如，若要获取有关 Registr 提供程序的帮助，请键入：</span><span class="sxs-lookup"><span data-stu-id="600d4-137">For example, to get Help for the Registry provider, type:</span></span>

```
get-help registry
```

<span data-ttu-id="600d4-138">若要获取会话中的所有提供程序帮助主题的列表，请键入：</span><span class="sxs-lookup"><span data-stu-id="600d4-138">To get a list of all the provider Help topics in your session, type</span></span>

```
get-help -category provider
```

<span data-ttu-id="600d4-139">Get-Help 的参数，例如 *Detailed*、*Parameter* 和 *Examples*，它们对提供程序帮助主题的显示没有影响。</span><span class="sxs-lookup"><span data-stu-id="600d4-139">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of provider Help topics.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="600d4-140">获取有关脚本和函数的帮助</span><span class="sxs-lookup"><span data-stu-id="600d4-140">Getting Help About Scripts and Functions</span></span>
<span data-ttu-id="600d4-141">Windows PowerShell 中的许多脚本和函数都有帮助主题。</span><span class="sxs-lookup"><span data-stu-id="600d4-141">Many scripts and functions in Windows PowerShell have Help topics.</span></span> <span data-ttu-id="600d4-142">使用 Get-Help cmdlet 显示脚本和函数的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="600d4-142">Use the Get-Help cmdlet to display the Help topics for scripts and functions.</span></span>

<span data-ttu-id="600d4-143">若要显示有关某个函数的帮助，请键入“get-help”，后跟函数名称。</span><span class="sxs-lookup"><span data-stu-id="600d4-143">To display the Help for a function, type "get-help" followed by the function name.</span></span> <span data-ttu-id="600d4-144">例如，若要获取有关 Disable-PSRemoting 函数的帮助，请键入：</span><span class="sxs-lookup"><span data-stu-id="600d4-144">For example, to get Help for the Disable-PSRemoting function, type:</span></span>

```
get-help disable-psremoting
```

<span data-ttu-id="600d4-145">若要显示有关某个脚本的帮助，请键入该脚本文件的完整限定路径。</span><span class="sxs-lookup"><span data-stu-id="600d4-145">To display the Help for a script, type the fully qualified path to the script file.</span></span> <span data-ttu-id="600d4-146">如果脚本位于 Path 环境变量中列出的路径中，你可以在命令中省略路径。</span><span class="sxs-lookup"><span data-stu-id="600d4-146">If the script is in a path that is listed in the Path environment variable, you can omit the path from the command.</span></span>

<span data-ttu-id="600d4-147">例如，如果名为“TestScript.ps1”的脚本位于 C:\\PS-Test 库中，若要显示有关该脚本的帮助主题，请键入：</span><span class="sxs-lookup"><span data-stu-id="600d4-147">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help topic for the script, type:</span></span>

```
get-help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="600d4-148">用于显示 cmdlet 帮助的参数，如 *Detailed**Full**Examples* 和 *Parameter* 也适用于脚本帮助和函数帮助。</span><span class="sxs-lookup"><span data-stu-id="600d4-148">The parameters that were designed for displaying cmdlet Help, such as *Detailed*, *Full*, *Examples*, and *Parameter*, work for script Help and function Help, too.</span></span> <span data-ttu-id="600d4-149">但是，当你通过键入“get-help \*”显示所有帮助时，将不显示有关函数和脚本的帮助。</span><span class="sxs-lookup"><span data-stu-id="600d4-149">However, when you display all Help, by typing "get-help \*", Help for functions and scripts does not appear.</span></span>

<span data-ttu-id="600d4-150">有关为函数和脚本编写帮助的信息，请参阅 [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)、[about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af) 和 [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)。</span><span class="sxs-lookup"><span data-stu-id="600d4-150">For information about writing Help topics for your functions and scripts, see [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af), and [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span></span>

## <a name="getting-help-online"></a><span data-ttu-id="600d4-151">在线获取帮助</span><span class="sxs-lookup"><span data-stu-id="600d4-151">Getting Help Online</span></span>
<span data-ttu-id="600d4-152">如果已经连接到 Internet，获取帮助的最好方法之一就是在线查看帮助主题。</span><span class="sxs-lookup"><span data-stu-id="600d4-152">If you are connected to the Internet, one of the best ways to get Help is to view the Help topics online.</span></span> <span data-ttu-id="600d4-153">由于在线主题易于更新，所以它们倾向于提供最新内容。</span><span class="sxs-lookup"><span data-stu-id="600d4-153">Because online topics are easy to update, they are likely to provide the most current content.</span></span>

<span data-ttu-id="600d4-154">若要在线获取帮助，请尝试使用 Get-Help cmdlet 的 *Online* 参数。</span><span class="sxs-lookup"><span data-stu-id="600d4-154">To get Help online, try the *Online* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="600d4-155">Get-Help cmdlet 的 *Online* 参数仅适用于 cmdlet 帮助、函数帮助和脚本帮助。</span><span class="sxs-lookup"><span data-stu-id="600d4-155">The *Online* parameter of the Get-Help cmdlet works only for cmdlet Help, function Help, and script Help.</span></span> <span data-ttu-id="600d4-156">不能将 *Online* 参数用于概念（关于）主题或提供程序帮助主题。</span><span class="sxs-lookup"><span data-stu-id="600d4-156">You cannot use the *Online* parameter with conceptual (About) topics or provider Help topics.</span></span> <span data-ttu-id="600d4-157">此外，由于这是一个可选功能，所以它并不适用于每一个 cmdlet、函数或脚本帮助主题。</span><span class="sxs-lookup"><span data-stu-id="600d4-157">Also, because this feature is optional, it does not work for every cmdlet, function, or script Help topic.</span></span>

<span data-ttu-id="600d4-158">但是，Windows PowerShell 附带的所有帮助主题（包括提供程序帮助和概念（有关）帮助主题）均在 Microsoft TechNet 库的 [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) 部分中在线提供。</span><span class="sxs-lookup"><span data-stu-id="600d4-158">However, all the Help topics that come with Windows PowerShell, including provider Help and conceptual (About) Help topics, are available online in the [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) section of the Microsoft TechNet Library.</span></span>

<span data-ttu-id="600d4-159">若要使用 Get-Help cmdlet 的 *Online* 参数，请使用下列命令格式。</span><span class="sxs-lookup"><span data-stu-id="600d4-159">To use the *Online* parameter of the Get-Help cmdlet, use the following command format.</span></span>

```
get-help <command-name> -online
```

<span data-ttu-id="600d4-160">例如，若要获取有关 Get-ChildItem cmdlet 的帮助主题的在线版本，请键入：</span><span class="sxs-lookup"><span data-stu-id="600d4-160">For example, to get the online version of the Help topic about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -online
```

<span data-ttu-id="600d4-161">如果该帮助主题有在线版本可用，则将在你的默认浏览器中打开它。</span><span class="sxs-lookup"><span data-stu-id="600d4-161">If an online version of the Help topic is available, it will open in your default browser.</span></span>

<span data-ttu-id="600d4-162">如果该帮助主题支持在线帮助，则你也可以查看该帮助主题的 Internet 地址 (URL)。</span><span class="sxs-lookup"><span data-stu-id="600d4-162">If online Help is supported for a Help topic, you can also view the Internet address (URL) of the Help topic.</span></span> <span data-ttu-id="600d4-163">Internet 地址将显示在帮助主题的“相关链接”部分中。</span><span class="sxs-lookup"><span data-stu-id="600d4-163">The Internet address appears in the Related Links section of a Help topic.</span></span>

<span data-ttu-id="600d4-164">例如，若要查看 Add-Computer cmdlet 的在线版本的 URL，请键入：</span><span class="sxs-lookup"><span data-stu-id="600d4-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```
get-help add-computer
```

<span data-ttu-id="600d4-165">该主题的“相关链接”的第一行如下所示。</span><span class="sxs-lookup"><span data-stu-id="600d4-165">The first line in the Related Links section of the topic is shown below.</span></span>

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

<span data-ttu-id="600d4-166">有关如何为帮助主题提供在线支持的信息，请参阅 [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf) 和 MSDN 库中的 [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415)（如何编写 Cmdlet 帮助）。</span><span class="sxs-lookup"><span data-stu-id="600d4-166">For information about how to provide online support for your Help topics, see [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf), and see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="see-also"></a><span data-ttu-id="600d4-167">另请参阅</span><span class="sxs-lookup"><span data-stu-id="600d4-167">See Also</span></span>
- [<span data-ttu-id="600d4-168">about_Functions [m2]</span><span class="sxs-lookup"><span data-stu-id="600d4-168">about_Functions [m2]</span></span>](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)
- [<span data-ttu-id="600d4-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="600d4-169">about_Scripts</span></span>](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af)
- [<span data-ttu-id="600d4-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="600d4-170">about_Comment_Based_Help</span></span>](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
- [<span data-ttu-id="600d4-171">Get-Help [m2]</span><span class="sxs-lookup"><span data-stu-id="600d4-171">Get-Help [m2]</span></span>](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)

