---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell ISE 脚本对象模型的用途
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
ms.openlocfilehash: fd5ac2c34b173d4eba7636bb5760b1ac9abb4277
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951318"
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a><span data-ttu-id="b9cb5-103">Windows PowerShell ISE 脚本对象模型的用途</span><span class="sxs-lookup"><span data-stu-id="b9cb5-103">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>

<span data-ttu-id="b9cb5-104">对象与 Windows PowerShell 集成脚本环境 (ISE) 的窗体和函数相关。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-104">Objects are associated with the form and function of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="b9cb5-105">对象模型参考提供有关这些对象公开的成员属性和方法的详细信息。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-105">The object model reference provides details about the member properties and methods that these objects expose.</span></span> <span data-ttu-id="b9cb5-106">提供了示例来演示如何使用脚本直接访问这些方法和属性。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-106">Examples are provided to show how you can use scripts to directly access these methods and properties.</span></span> <span data-ttu-id="b9cb5-107">脚本对象模型使得可以轻松完成下列任务。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-107">The scripting object model makes the following range of tasks easier.</span></span>

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a><span data-ttu-id="b9cb5-108">自定义 Windows PowerShell ISE 的外观</span><span class="sxs-lookup"><span data-stu-id="b9cb5-108">Customizing the appearance of Windows PowerShell ISE</span></span>

<span data-ttu-id="b9cb5-109">对象模型可用于修改应用程序设置和选项。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-109">You can use the object model to modify the application settings and options.</span></span> <span data-ttu-id="b9cb5-110">例如，可以如下所示修改它们：</span><span class="sxs-lookup"><span data-stu-id="b9cb5-110">For example, you can modify them as follows:</span></span>

- <span data-ttu-id="b9cb5-111">可以更改错误、警告、详细输出和调试输出的颜色。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-111">You can change the color of errors, warnings, verbose outputs, and debug outputs.</span></span>
- <span data-ttu-id="b9cb5-112">可以获取或设置“命令”窗格、“输出”窗格以及“脚本”窗格的背景色。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-112">You can get or set the background colors for the Command pane, the Output pane, and the Script pane.</span></span>
- <span data-ttu-id="b9cb5-113">可以设置“输出”窗格的前景色。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-113">You can set the foreground color for the Output pane.</span></span>
- <span data-ttu-id="b9cb5-114">可以设置 Windows PowerShell ISE 的字体名称和字体大小。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-114">You can set the font name and font size for Windows PowerShell ISE.</span></span>
- <span data-ttu-id="b9cb5-115">可以配置警告。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-115">You can configure warnings.</span></span> <span data-ttu-id="b9cb5-116">此设置包含在多个 PowerShell 选项卡中打开一个文件或者在保存文件之前运行该文件中的脚本时将发出的警告。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-116">This setting includes warnings that are issued when a file is opened in multiple PowerShell tabs or when a script in the file is run before the file has been saved.</span></span>
- <span data-ttu-id="b9cb5-117">你可以在“脚本”窗格和“输出”窗格并排显示的视图与“脚本”窗格位于“输出”窗格之上的视图之间进行切换。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-117">You can switch between a view where the Script pane and the Output pane are side-by-side and a view where the Script pane is on top of the Output pane.</span></span> <span data-ttu-id="b9cb5-118">你可以将“命令”窗格停靠在“输出”窗格的底部或之上。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-118">You can dock the Command pane to the bottom or the top of the Output pane.</span></span>

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a><span data-ttu-id="b9cb5-119">增强 Windows PowerShell ISE 的功能</span><span class="sxs-lookup"><span data-stu-id="b9cb5-119">Enhancing the functionality of Windows PowerShell ISE</span></span>

<span data-ttu-id="b9cb5-120">对象模型可用于增强 Windows PowerShell ISE 的功能。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-120">You can use the object model to enhance the functionality of Windows PowerShell ISE.</span></span> <span data-ttu-id="b9cb5-121">例如，你能够：</span><span class="sxs-lookup"><span data-stu-id="b9cb5-121">For example, you can:</span></span>

- <span data-ttu-id="b9cb5-122">添加和修改 Windows PowerShell ISE 本身的实例。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-122">Add and modify the instance of Windows PowerShell ISE itself.</span></span> <span data-ttu-id="b9cb5-123">例如，若要更改菜单，可以添加新菜单项并将新菜单项映射到脚本。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-123">For example, to change the menus, you can add new menu items and map the new menu items to scripts.</span></span>
- <span data-ttu-id="b9cb5-124">创建执行可以通过使用 Windows PowerShell ISE 中的菜单命令和按钮执行的一些任务的脚本。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-124">Create scripts that perform some of the tasks that you can perform by using the menu commands and buttons in Windows PowerShell ISE.</span></span> <span data-ttu-id="b9cb5-125">例如，你可以添加、删除或选择一个 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-125">For example, you can add, remove, or select a PowerShell tab.</span></span>
- <span data-ttu-id="b9cb5-126">可以通过使用菜单命令和按钮执行的补充任务。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-126">Complement tasks that can be performed by using menu commands and buttons.</span></span> <span data-ttu-id="b9cb5-127">例如，你可以重命名 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-127">For example, you can rename a PowerShell tab.</span></span>
- <span data-ttu-id="b9cb5-128">操作“命令”窗格、“输出”窗格以及“脚本”窗格与文件相关联的文本缓冲区。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-128">Manipulate text buffers for the Command pane, the Output pane, and the Script pane that are associated with a file.</span></span> <span data-ttu-id="b9cb5-129">例如，你能够：</span><span class="sxs-lookup"><span data-stu-id="b9cb5-129">For example, you can:</span></span>
  - <span data-ttu-id="b9cb5-130">获取或设置所有文本。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-130">Get or set all text.</span></span>
  - <span data-ttu-id="b9cb5-131">获取或设置文本选择。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-131">Get or set a text selection.</span></span>
  - <span data-ttu-id="b9cb5-132">运行脚本或运行脚本的选定部分。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-132">Run a script or run a selected portion of a script.</span></span>
  - <span data-ttu-id="b9cb5-133">将某行滚动到视图中。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-133">Scroll a line into view.</span></span>
  - <span data-ttu-id="b9cb5-134">在脱字号位置插入文本。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-134">Insert text at a caret position.</span></span>
  - <span data-ttu-id="b9cb5-135">选择文本块。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-135">Select a block of text.</span></span>
  - <span data-ttu-id="b9cb5-136">获取最后一个行号。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-136">Get the last line number.</span></span>
- <span data-ttu-id="b9cb5-137">执行文件操作。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-137">Perform file operations.</span></span> <span data-ttu-id="b9cb5-138">例如，你能够：</span><span class="sxs-lookup"><span data-stu-id="b9cb5-138">For example, you can:</span></span>
  - <span data-ttu-id="b9cb5-139">打开文件、保存文件或使用其他名称保存文件。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-139">Open a file, save a file, or save a file by using a different name.</span></span>
  - <span data-ttu-id="b9cb5-140">确定文件自上次保存后是否已更改。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-140">Determine whether a file has been changed after it was last saved.</span></span>
  - <span data-ttu-id="b9cb5-141">获取文件名。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-141">Get the file name.</span></span>
  - <span data-ttu-id="b9cb5-142">选择一个文件。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-142">Select a file.</span></span>

## <a name="automating-tasks"></a><span data-ttu-id="b9cb5-143">自动执行任务</span><span class="sxs-lookup"><span data-stu-id="b9cb5-143">Automating tasks</span></span>

<span data-ttu-id="b9cb5-144">脚本对象模型可用于创建频繁执行的操作的键盘快捷方式。</span><span class="sxs-lookup"><span data-stu-id="b9cb5-144">You can use the scripting object model to create keyboard shortcuts for frequent operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9cb5-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b9cb5-145">See also</span></span>

- [<span data-ttu-id="b9cb5-146">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="b9cb5-146">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)