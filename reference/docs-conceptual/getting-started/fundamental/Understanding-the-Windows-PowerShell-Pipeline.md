---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "了解 Windows PowerShell 管道"
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: 6d152e52d2fcfb9dd592eb9ac40500615f2186cb
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
# <a name="understanding-the-windows-powershell-pipeline"></a><span data-ttu-id="3a367-103">了解 Windows PowerShell 管道</span><span class="sxs-lookup"><span data-stu-id="3a367-103">Understanding the Windows PowerShell Pipeline</span></span>
<span data-ttu-id="3a367-104">在 Windows PowerShell 中，管道的作用几乎随处可见。</span><span class="sxs-lookup"><span data-stu-id="3a367-104">Piping works virtually everywhere in Windows PowerShell.</span></span> <span data-ttu-id="3a367-105">尽管你会在屏幕上看到文本，但 Windows PowerShell 不通过管道在命令之间传递文本。</span><span class="sxs-lookup"><span data-stu-id="3a367-105">Although you see text on the screen, Windows PowerShell does not pipe text between commands.</span></span> <span data-ttu-id="3a367-106">而是通过管道传递对象。</span><span class="sxs-lookup"><span data-stu-id="3a367-106">Instead, it pipes objects.</span></span>

<span data-ttu-id="3a367-107">管道使用的表示法与其他 Shell 中使用的类似，因此乍看之下，似乎 Windows PowerShell 并未引入什么新的内容。</span><span class="sxs-lookup"><span data-stu-id="3a367-107">The notation used for pipelines is similar to that used in other shells, so at first glance, it may not be apparent that Windows PowerShell introduces something new.</span></span> <span data-ttu-id="3a367-108">例如，如果你使用 **Out-Host** cmdlet 来强制逐页显示来自于另一个命令的输出，则这一输出看起来就像分页显示在屏幕上的普通文本：</span><span class="sxs-lookup"><span data-stu-id="3a367-108">For example, if you use the **Out-Host** cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\system32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2005-10-22  11:04 PM        315 $winnt$.inf
-a---        2004-08-04   8:00 AM      68608 access.cpl
-a---        2004-08-04   8:00 AM      64512 acctres.dll
-a---        2004-08-04   8:00 AM     183808 accwiz.exe
-a---        2004-08-04   8:00 AM      61952 acelpdec.ax
-a---        2004-08-04   8:00 AM     129536 acledit.dll
-a---        2004-08-04   8:00 AM     114688 aclui.dll
-a---        2004-08-04   8:00 AM     194048 activeds.dll
-a---        2004-08-04   8:00 AM     111104 activeds.tlb
-a---        2004-08-04   8:00 AM       4096 actmovie.exe
-a---        2004-08-04   8:00 AM     101888 actxprxy.dll
-a---        2003-02-21   6:50 PM     143150 admgmt.msc
-a---        2006-01-25   3:35 PM      53760 admparse.dll
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="3a367-109">如果你想要缓慢显示冗长输出，Out-Host-Paging 命令会是一个有用的管道元素。</span><span class="sxs-lookup"><span data-stu-id="3a367-109">The Out-Host -Paging command is a useful pipeline element whenever you have lengthy output that you would like to display slowly.</span></span> <span data-ttu-id="3a367-110">尤其是在操作会大量占用 CPU 的情况下，会十分有用。</span><span class="sxs-lookup"><span data-stu-id="3a367-110">It is especially useful if the operation is very CPU-intensive.</span></span> <span data-ttu-id="3a367-111">因为当有可以立即显示的完整页面时，处理进程会转移到 Out-Host cmdlet，而管道中在其之前的 cmdlet 会停止操作，直到输出了下一页为止。</span><span class="sxs-lookup"><span data-stu-id="3a367-111">Because processing is transferred to the Out-Host cmdlet when it has a complete page ready to display, cmdlets that precede it in the pipeline halt operation until the next page of output is available.</span></span> <span data-ttu-id="3a367-112">如果使用 Windows 任务管理器监视 Windows PowerShell 的 CPU 和内存使用情况，便会见到这种情况。</span><span class="sxs-lookup"><span data-stu-id="3a367-112">You can see this if you use the Windows Task Manager to monitor CPU and memory use by Windows PowerShell.</span></span>

<span data-ttu-id="3a367-113">运行命令：**Get-ChildItem C:\\Windows-Recurse**。</span><span class="sxs-lookup"><span data-stu-id="3a367-113">Run the following command: **Get-ChildItem C:\\Windows -Recurse**.</span></span> <span data-ttu-id="3a367-114">将 CPU 和内存的使用情况与此命令相比较：**Get-ChildItem C:\\Windows-Recurse | Out-Host-Paging**。</span><span class="sxs-lookup"><span data-stu-id="3a367-114">Compare the CPU and memory usage to this command: **Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging**.</span></span> <span data-ttu-id="3a367-115">你在屏幕上会看到文本，但那是因为在控制台窗口中以文本形式表示对象是必需的。</span><span class="sxs-lookup"><span data-stu-id="3a367-115">What you see on the screen is text, but that is because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="3a367-116">这只是 Windows PowerShell 中实际运行内容的表示形式。</span><span class="sxs-lookup"><span data-stu-id="3a367-116">This is just a representation of what is really going on inside Windows PowerShell.</span></span> <span data-ttu-id="3a367-117">例如，想想 Get-Location cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3a367-117">For example, consider the Get-Location cmdlet.</span></span> <span data-ttu-id="3a367-118">如果你键入 **Get-Location**，而你当前的位置是 C 驱动器的根路径时，你将看到以下输出：</span><span class="sxs-lookup"><span data-stu-id="3a367-118">If you type **Get-Location** while your current location is the root of the C drive, you would see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="3a367-119">如果 Windows PowerShell 通过管道传递文本，并发出，比如说，命令 **Get-Location | Out-Host**，则会将一组字符按其在屏幕上的显示顺序从 **Get-Location** 传递到 **Out-Host**。</span><span class="sxs-lookup"><span data-stu-id="3a367-119">If Windows PowerShell pipelined text, issuing a command such as **Get-Location | Out-Host**, would pass from **Get-Location** to **Out-Host** a set of characters in the order they are displayed onscreen.</span></span> <span data-ttu-id="3a367-120">换言之，如你打算忽略标题信息，**Out-Host** 会首先收到字符“**C”**，接着是字符“**:”**，然后是字符“**\\”**。</span><span class="sxs-lookup"><span data-stu-id="3a367-120">In other words, if you were to ignore the heading information, **Out-Host** would first receive the character '**C'**, then the character '**:'**, then the character '**\\'**.</span></span> <span data-ttu-id="3a367-121">**Out-Host** cmdlet 无法确定要与 **Get-Location** cmdlet 输出的字符关联的含义。</span><span class="sxs-lookup"><span data-stu-id="3a367-121">The **Out-Host** cmdlet could not determine what meaning to associate with the characters output by the **Get-Location** cmdlet.</span></span>

<span data-ttu-id="3a367-122">Windows PowerShell 在管道通信中不使用文本运行命令，而是使用对象。</span><span class="sxs-lookup"><span data-stu-id="3a367-122">Instead of using text to let commands in a pipeline communicate, Windows PowerShell uses objects.</span></span> <span data-ttu-id="3a367-123">从用户角度来看，对象将相关信息打包成一种可使信息作为单元进行操作变得更容易以及提取所需的特定项变得更容易的形式。</span><span class="sxs-lookup"><span data-stu-id="3a367-123">From the standpoint of a user, objects package related information into a form that makes it easier to manipulate the information as a unit, and extract specific items that you need.</span></span>

<span data-ttu-id="3a367-124">**Get-Location** 命令不返回包含当前路径的文本。</span><span class="sxs-lookup"><span data-stu-id="3a367-124">The **Get-Location** command does not return text that contains the current path.</span></span> <span data-ttu-id="3a367-125">它返回称为 **PathInfo** 对象的一个信息包，其中包含了当前路径以及一些其他信息。</span><span class="sxs-lookup"><span data-stu-id="3a367-125">It returns a package of information called a **PathInfo** object that contains the current path along with some other information.</span></span> <span data-ttu-id="3a367-126">然后 **Out-Host** cmdlet 将此 **PathInfo** 对象发送到屏幕，Windows PowerShell 会根据其格式设置规则决定要显示的信息以及显示的方式。</span><span class="sxs-lookup"><span data-stu-id="3a367-126">The **Out-Host** cmdlet then sends this **PathInfo** object to the screen, and Windows PowerShell decides what information to display and how to display it based on its formatting rules.</span></span>

<span data-ttu-id="3a367-127">实际上，只会在此进程结束时添加 **Get-Location** cmdlet 输出的标题信息，作为屏幕上所显示数据的格式设置过程的一部分。</span><span class="sxs-lookup"><span data-stu-id="3a367-127">In fact, the heading information output by the **Get-Location** cmdlet is added only at the end of the process, as part of the process of formatting the data for onscreen display.</span></span> <span data-ttu-id="3a367-128">你在屏幕上看到的只是信息摘要，而非输出对象的完整表示形式。</span><span class="sxs-lookup"><span data-stu-id="3a367-128">What you see onscreen is a summary of information, and not a complete representation of the output object.</span></span>

<span data-ttu-id="3a367-129">假设从 Windows PowerShell 命令输出的信息比我们在控制台窗口中看到的多，该如何检索不可见的元素呢？</span><span class="sxs-lookup"><span data-stu-id="3a367-129">Given that there may be more information output from a Windows PowerShell command than what we see displayed in the console window, how can you retrieve the non-visible elements?</span></span> <span data-ttu-id="3a367-130">如何查看额外的数据？</span><span class="sxs-lookup"><span data-stu-id="3a367-130">How do you view the extra data?</span></span> <span data-ttu-id="3a367-131">并且如果你想以不同于 Windows PowerShell 通常使用的格式来查看数据，应该怎么做？</span><span class="sxs-lookup"><span data-stu-id="3a367-131">And what if you want to view the data in a format different than the one Windows PowerShell normally uses?</span></span>

<span data-ttu-id="3a367-132">本章的其余部分将讨论如何发现特定 Windows PowerShell 对象的结构，同时选择特定项并将其设置为更易显示的格式，以及如何将此信息发送至备用输出位置，比如文件和打印机。</span><span class="sxs-lookup"><span data-stu-id="3a367-132">The rest of this chapter discusses how you can discover the structure of specific Windows PowerShell objects, selecting specific items and formatting them for easier display, and how to send this information to alternative output locations such as files and printers.</span></span>

