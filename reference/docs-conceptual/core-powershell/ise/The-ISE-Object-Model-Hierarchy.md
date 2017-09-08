---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISE 对象模型层次结构"
ms.assetid: bc3300e4-9c17-4f00-a621-c8867126e3b3
ms.openlocfilehash: b6e251eac7db56896490362392e0a1c4c10a8d4a
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2017
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="0a201-103">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="0a201-103">The ISE Object Model Hierarchy</span></span>
  <span data-ttu-id="0a201-104">本主题介绍了属于 Windows PowerShell 集成脚本环境 (ISE) 一部分的对象的层次结构。</span><span class="sxs-lookup"><span data-stu-id="0a201-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="0a201-105">在 Windows PowerShell 3.0 和 Windows PowerShell 4.0 中包含 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="0a201-105">Windows PowerShell ISE is included in Windows PowerShell 3.0 and in Windows PowerShell 4.0.</span></span> <span data-ttu-id="0a201-106">单击一个对象，使你转到定义对象的类的参考文档。</span><span class="sxs-lookup"><span data-stu-id="0a201-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

##  <a name="psise-object"></a><span data-ttu-id="0a201-107">**$psISE 对象**</span><span class="sxs-lookup"><span data-stu-id="0a201-107">**$psISE Object**</span></span>
 <span data-ttu-id="0a201-108">**$PsISE** 对象是 Windows PowerShell ISE 对象层次结构的[根对象](The-ObjectModelRoot-Object.md)。</span><span class="sxs-lookup"><span data-stu-id="0a201-108">The **$psISE** object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span> <span data-ttu-id="0a201-109">它位于顶层，使以下对象可用于脚本编写：</span><span class="sxs-lookup"><span data-stu-id="0a201-109">Located at the top level, it makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="0a201-110">**[$psISE.CurrentFile]()**</span><span class="sxs-lookup"><span data-stu-id="0a201-110">**[$psISE.CurrentFile]()**</span></span>

-   <span data-ttu-id="0a201-111">**[$psISE.CurrentPowerShellTab]()**</span><span class="sxs-lookup"><span data-stu-id="0a201-111">**[$psISE.CurrentPowerShellTab]()**</span></span>

-   <span data-ttu-id="0a201-112">**[$psISE.CurrentVisibleHorizontalTool]()**</span><span class="sxs-lookup"><span data-stu-id="0a201-112">**[$psISE.CurrentVisibleHorizontalTool]()**</span></span>

-   <span data-ttu-id="0a201-113">**[$psISE.CurrentVisibleVerticalTool]()**</span><span class="sxs-lookup"><span data-stu-id="0a201-113">**[$psISE.CurrentVisibleVerticalTool]()**</span></span>

-   <span data-ttu-id="0a201-114">**[$psISE.Options]()**</span><span class="sxs-lookup"><span data-stu-id="0a201-114">**[$psISE.Options]()**</span></span>

-   <span data-ttu-id="0a201-115">**[$psISE.PowerShellTabs]()**</span><span class="sxs-lookup"><span data-stu-id="0a201-115">**[$psISE.PowerShellTabs]()**</span></span>

##  <a name="psisecurrentfilethe-isefile-objectmd"></a><span data-ttu-id="0a201-116">**[$psISE.CurrentFile](The-ISEFile-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="0a201-116">**[$psISE.CurrentFile](The-ISEFile-Object.md)**</span></span>
 <span data-ttu-id="0a201-117">**$PsISE.CurrentFile** 对象是 [ISEFile](The-ISEFile-Object.md) 类的实例，使以下对象可用于脚本编写：</span><span class="sxs-lookup"><span data-stu-id="0a201-117">The **$psISE.CurrentFile** object is an instance of the [ISEFile](The-ISEFile-Object.md) class and makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="0a201-118">**[$psISE.CurrentFile.DisplayName](The-ISEFile-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="0a201-118">**[$psISE.CurrentFile.DisplayName](The-ISEFile-Object.md)**</span></span>

-   <span data-ttu-id="0a201-119">**[$psISE.CurrentFile.Editor](The-ISEEditor-Object.md)**  此对象是 [ISEEditor](The-ISEEditor-Object.md) 类的实例，使以下对象可用于脚本编写：</span><span class="sxs-lookup"><span data-stu-id="0a201-119">**[$psISE.CurrentFile.Editor](The-ISEEditor-Object.md)**  This object is an instance of the [ISEEditor](The-ISEEditor-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="0a201-120">**[$psISE.CurrentFile.Editor.CanGoToMatch](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="0a201-120">**[$psISE.CurrentFile.Editor.CanGoToMatch](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="0a201-121">**[CaretColumn](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="0a201-121">**[CaretColumn](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="0a201-122">**[CaretLine](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="0a201-122">**[CaretLine](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="0a201-123">**[$psISE.CurrentFile.Editor.CaretLineText](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="0a201-123">**[$psISE.CurrentFile.Editor.CaretLineText](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="0a201-124">**[LineCount](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="0a201-124">**[LineCount](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="0a201-125">**[SelectedText](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="0a201-125">**[SelectedText](The-ISEEditor-Object.md)**</span></span>

    -   <span data-ttu-id="0a201-126">**[Text](The-ISEEditor-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="0a201-126">**[Text](The-ISEEditor-Object.md)**</span></span>

-   <span data-ttu-id="0a201-127">[EncodingThe-ISEFile-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-127">**[EncodingThe-ISEFile-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-128">[FullPathThe-ISEFile-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-128">**[FullPathThe-ISEFile-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-129">[IsSavedThe-ISEFile-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-129">**[IsSavedThe-ISEFile-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-130">[IsUntitledThe-ISEFile-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-130">**[IsUntitledThe-ISEFile-Object.md]()**</span></span>

##  <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a><span data-ttu-id="0a201-131">**[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="0a201-131">**[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)**</span></span>
 <span data-ttu-id="0a201-132">**$psISE.CurrentPowerShellTab** 对象是 [PowerShellTab](The-PowerShellTab-Object.md) 类的实例，使以下对象可用于脚本编写：</span><span class="sxs-lookup"><span data-stu-id="0a201-132">The **$psISE.CurrentPowerShellTab** object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class and makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="0a201-133">**[$psISE.CurrentPowerShellTab.AddOnsMenu](The-ISEMenuItem-Object.md)**  此对象是 [ISEMenuItem](The-ISEMenuItem-Object.md) 类的实例，使以下对象可用于脚本编写：</span><span class="sxs-lookup"><span data-stu-id="0a201-133">**[$psISE.CurrentPowerShellTab.AddOnsMenu](The-ISEMenuItem-Object.md)**  This object is an instance of the [ISEMenuItem](The-ISEMenuItem-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="0a201-134">[$psISE.CurrentPowerShellTab.AddOnsMenu.ActionThe-ISEMenuItem-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-134">**[$psISE.CurrentPowerShellTab.AddOnsMenu.ActionThe-ISEMenuItem-Object.md]()**</span></span>

    -   <span data-ttu-id="0a201-135">[$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayNameThe-ISEMenuItem-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-135">**[$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayNameThe-ISEMenuItem-Object.md]()**</span></span>

    -   <span data-ttu-id="0a201-136">[$psISE.CurrentPowerShellTab.AddOnsMenu.ShortcutThe-ISEMenuItem-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-136">**[$psISE.CurrentPowerShellTab.AddOnsMenu.ShortcutThe-ISEMenuItem-Object.md]()**</span></span>

    -   <span data-ttu-id="0a201-137">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus](The-ISEMenuItemCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="0a201-137">**[$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus](The-ISEMenuItemCollection-Object.md)**</span></span>

-   <span data-ttu-id="0a201-138">[$psISE.CurrentPowerShellTab.CanInvokeThe-PowerShellTab-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-138">**[$psISE.CurrentPowerShellTab.CanInvokeThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-139">**[$psISE.CurrentPowerShellTab.ConsolePane](The-ISEEditor-Object.md)**  此对象是 [ISEEditor](The-ISEEditor-Object.md) 类的实例，使以下对象可用于脚本编写：</span><span class="sxs-lookup"><span data-stu-id="0a201-139">**[$psISE.CurrentPowerShellTab.ConsolePane](The-ISEEditor-Object.md)**  This object is an instance of the [ISEEditor](The-ISEEditor-Object.md) class and makes the following objects available for scripting:</span></span>

    -   <span data-ttu-id="0a201-140">[$psISE.CurrentPowerShellTab.ConsolePane.CanGoToMatchThe-ISEEditor-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-140">**[$psISE.CurrentPowerShellTab.ConsolePane.CanGoToMatchThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="0a201-141">[CaretColumnThe-ISEEditor-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-141">**[CaretColumnThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="0a201-142">[CaretLineThe-ISEEditor-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-142">**[CaretLineThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="0a201-143">[$psISE.CurrentPowerShellTab.ConsolePane.CaretLineTextThe-ISEEditor-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-143">**[$psISE.CurrentPowerShellTab.ConsolePane.CaretLineTextThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="0a201-144">[LineCountThe-ISEEditor-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-144">**[LineCountThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="0a201-145">[SelectedTextThe-ISEEditor-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-145">**[SelectedTextThe-ISEEditor-Object.md]()**</span></span>

    -   <span data-ttu-id="0a201-146">[TextThe-ISEEditor-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-146">**[TextThe-ISEEditor-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-147">[$psISE.CurrentPowerShellTab.DisplayNameThe-PowerShellTab-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-147">**[$psISE.CurrentPowerShellTab.DisplayNameThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-148">[$psISE.CurrentPowerShellTab.ExpandedScriptThe-PowerShellTab-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-148">**[$psISE.CurrentPowerShellTab.ExpandedScriptThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-149">**[$psISE.CurrentPowerShellTab.Files](The-ISEFileCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="0a201-149">**[$psISE.CurrentPowerShellTab.Files](The-ISEFileCollection-Object.md)**</span></span>

-   <span data-ttu-id="0a201-150">**[$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="0a201-150">**[$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="0a201-151">[$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-151">**[$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-152">[$psISE.CurrentPowerShellTab.PromptThe-PowerShellTab-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-152">**[$psISE.CurrentPowerShellTab.PromptThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-153">[$psISE.CurrentPowerShellTab.ShowCommandsThe-PowerShellTab-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-153">**[$psISE.CurrentPowerShellTab.ShowCommandsThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-154">**[$psISE.CurrentPowerShellTab.Snippets](The-ISESnippetCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="0a201-154">**[$psISE.CurrentPowerShellTab.Snippets](The-ISESnippetCollection-Object.md)**</span></span>

-   <span data-ttu-id="0a201-155">[$psISE.CurrentPowerShellTab.StatusTextThe-PowerShellTab-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-155">**[$psISE.CurrentPowerShellTab.StatusTextThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-156">**[$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="0a201-156">**[$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="0a201-157">[$psISE.CurrentPowerShellTab.VerticalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-157">**[$psISE.CurrentPowerShellTab.VerticalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-158">**[$psISE.CurrentPowerShellTab.VisibleHorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="0a201-158">**[$psISE.CurrentPowerShellTab.VisibleHorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

-   <span data-ttu-id="0a201-159">**[$psISE.CurrentPowerShellTab.VisibleVerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="0a201-159">**[$psISE.CurrentPowerShellTab.VisibleVerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**</span></span>

##  <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="0a201-160">$psISE.CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="0a201-160">**$psISE.CurrentVisibleHorizontalTool**</span></span>
 <span data-ttu-id="0a201-161">**$PsISE.CurrentVisibleHorizontalTool** 对象是 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="0a201-161">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="0a201-162">它表示已安装的外接程序工具，当前停靠在 Windows PowerShell ISE 窗口的顶部。</span><span class="sxs-lookup"><span data-stu-id="0a201-162">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="0a201-163">此对象使以下对象可用于脚本编写：</span><span class="sxs-lookup"><span data-stu-id="0a201-163">This object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="0a201-164">[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-164">**[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-165">[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-165">**[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-166">[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-166">**[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**</span></span>

##  <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="0a201-167">$psISE.CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="0a201-167">**$psISE.CurrentVisibleVerticalTool**</span></span>
 <span data-ttu-id="0a201-168">**$PsISE.CurrentVisibleHorizontalTool** 对象是 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="0a201-168">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="0a201-169">它表示已安装的外接程序工具，当前停靠在 Windows PowerShell ISE 窗口的右侧。</span><span class="sxs-lookup"><span data-stu-id="0a201-169">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="0a201-170">此对象使以下对象可用于脚本编写：</span><span class="sxs-lookup"><span data-stu-id="0a201-170">This object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="0a201-171">[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-171">**[$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-172">[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-172">**[$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-173">[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-173">**[$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()**</span></span>

##  <a name="psiseoptions"></a><span data-ttu-id="0a201-174">$psISE.Options</span><span class="sxs-lookup"><span data-stu-id="0a201-174">**$psISE.Options**</span></span>
 <span data-ttu-id="0a201-175">**$psISE.Options** 对象使以下对象可用于脚本编写：</span><span class="sxs-lookup"><span data-stu-id="0a201-175">The **$psISE.Options** object makes the following objects available for scripting:</span></span>

-   <span data-ttu-id="0a201-176">[$psISE.Options.AutoSaveMinuteIntervalThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-176">**[$psISE.Options.AutoSaveMinuteIntervalThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-177">[$psISE.Options.ConsolePaneBackgroundColorThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-177">**[$psISE.Options.ConsolePaneBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-178">[$psISE.Options.ConsolePaneTextForegroundColorThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-178">**[$psISE.Options.ConsolePaneTextForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-179">[$psISE.Options.ConsolePaneTextBackgroundColorThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-179">**[$psISE.Options.ConsolePaneTextBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-180">[$psISE.Options.ConsoleTokenColorsThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-180">**[$psISE.Options.ConsoleTokenColorsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-181">[$psISE.Options.DebugBackgroundColorThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-181">**[$psISE.Options.DebugBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-182">[$psISE.Options.DebugForegroundColorThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-182">**[$psISE.Options.DebugForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-183">**[$psISE.Options.DefaultOptions](The-ISEOptions-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="0a201-183">**[$psISE.Options.DefaultOptions](The-ISEOptions-Object.md)**</span></span>

-   <span data-ttu-id="0a201-184">[$psISE.Options.ErrorBackgroundColorThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-184">**[$psISE.Options.ErrorBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-185">[$psISE.Options.ErrorForegroundColorThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-185">**[$psISE.Options.ErrorForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-186">[$psISE.Options.FontNameThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-186">**[$psISE.Options.FontNameThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-187">[$psISE.Options.FontsizeThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-187">**[$psISE.Options.FontsizeThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-188">[$psISE.Options.IntellisenseTimeoutInSecondsThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-188">**[$psISE.Options.IntellisenseTimeoutInSecondsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-189">[$psISE.Options.MRUCountThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-189">**[$psISE.Options.MRUCountThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-190">[$psISE.Options.ScriptPaneBackgroundColorThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-190">**[$psISE.Options.ScriptPaneBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-191">[$psISE.Options.ScriptPaneForegroundColorThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-191">**[$psISE.Options.ScriptPaneForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-192">[$psISE.Options.SelectedScriptPaneStateThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-192">**[$psISE.Options.SelectedScriptPaneStateThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-193">[$psISE.Options.ShowDefaultSnippetsThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-193">**[$psISE.Options.ShowDefaultSnippetsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-194">[$psISE.Options.ShowIntellisenseInConsolePaneThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-194">**[$psISE.Options.ShowIntellisenseInConsolePaneThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-195">[$psISE.Options.ShowIntellisenseInScriptPaneThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-195">**[$psISE.Options.ShowIntellisenseInScriptPaneThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-196">[$psISE.Options.ShowLineNumbersThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-196">**[$psISE.Options.ShowLineNumbersThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-197">[$psISE.Options.ShowOutliningThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-197">**[$psISE.Options.ShowOutliningThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-198">[$psISE.Options.ShowToolBarThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-198">**[$psISE.Options.ShowToolBarThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-199">[$psISE.Options.ShowWarningBeforeSavingOnRunThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-199">**[$psISE.Options.ShowWarningBeforeSavingOnRunThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-200">[$psISE.Options.ShowWarningForDuplicateFilesThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-200">**[$psISE.Options.ShowWarningForDuplicateFilesThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-201">[$psISE.Options.TokenColorsThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-201">**[$psISE.Options.TokenColorsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-202">[$psISE.Options.UseEnterToSelectConsolePaneIntellisenseThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-202">**[$psISE.Options.UseEnterToSelectConsolePaneIntellisenseThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-203">**[$psISE.Options.UseEnterToSelectScriptPaneIntellisenseThe-ISEOptions-Object.md]()**</span><span class="sxs-lookup"><span data-stu-id="0a201-203">**[$psISE.Options. UseEnterToSelectScriptPaneIntellisenseThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-204">[$psISE.Options.UseLocalHelpThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-204">**[$psISE.Options.UseLocalHelpThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-205">[$psISE.Options.VerboseBackgroundColorThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-205">**[$psISE.Options.VerboseBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-206">[$psISE.Options.VerboseForegroundColorThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-206">**[$psISE.Options.VerboseForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-207">[$psISE.Options.WarningBackgroundColorThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-207">**[$psISE.Options.WarningBackgroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-208">[$psISE.Options.WarningForegroundColorThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-208">**[$psISE.Options.WarningForegroundColorThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-209">[$psISE.Options.XmlTokenColorsThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-209">**[$psISE.Options.XmlTokenColorsThe-ISEOptions-Object.md]()**</span></span>

-   <span data-ttu-id="0a201-210">[$psISE.Options.ZoomThe-ISEOptions-Object.md]()</span><span class="sxs-lookup"><span data-stu-id="0a201-210">**[$psISE.Options.ZoomThe-ISEOptions-Object.md]()**</span></span>

##  <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a><span data-ttu-id="0a201-211">**[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)**</span><span class="sxs-lookup"><span data-stu-id="0a201-211">**[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)**</span></span>
 <span data-ttu-id="0a201-212">**$PsISE.PowerShellTabs** 对象是 [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="0a201-212">The **$psISE.PowerShellTabs** object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span> <span data-ttu-id="0a201-213">它是所有当前打开的 PowerShell 选项卡的集合，表示本地计算机上或在已连接的远程计算机上可用的 Windows PowerShell 运行环境。</span><span class="sxs-lookup"><span data-stu-id="0a201-213">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span> <span data-ttu-id="0a201-214">集合中的每个成员均为 [PowerShellTab](The-PowerShellTab-Object.md) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="0a201-214">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a201-215">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0a201-215">See Also</span></span>
- [<span data-ttu-id="0a201-216">Windows PowerShell ISE 脚本对象模型</span><span class="sxs-lookup"><span data-stu-id="0a201-216">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="0a201-217">Windows PowerShell ISE 对象模型参考</span><span class="sxs-lookup"><span data-stu-id="0a201-217">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)

