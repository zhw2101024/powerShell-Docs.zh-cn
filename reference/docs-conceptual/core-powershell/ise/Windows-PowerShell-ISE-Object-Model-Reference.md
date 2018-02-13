---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Windows PowerShell ISE 对象模型参考"
ms.assetid: e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c
ms.openlocfilehash: 624ddca3895ba3e24bf52a27babdb07e8714baae
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2018
---
# <a name="windows-powershell-ise-object-model-reference"></a><span data-ttu-id="9bdb7-103">Windows PowerShell ISE 对象模型参考</span><span class="sxs-lookup"><span data-stu-id="9bdb7-103">Windows PowerShell ISE Object Model Reference</span></span>
  
## <a name="object-model-reference"></a><span data-ttu-id="9bdb7-104">对象模型参考</span><span class="sxs-lookup"><span data-stu-id="9bdb7-104">Object Model Reference</span></span>
 <span data-ttu-id="9bdb7-105">本部分对定义 Windows PowerShell® 集成脚本环境 (ISE) 中的各种对象的基础类提供了参考。</span><span class="sxs-lookup"><span data-stu-id="9bdb7-105">This section provides a reference on the underlying classes that define the various objects inWindows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="9bdb7-106">若要查看在其层次结构中组织的对象，请参阅 [ISE 对象模型层次结构](The-ISE-Object-Model-Hierarchy.md)。</span><span class="sxs-lookup"><span data-stu-id="9bdb7-106">To see the objects organized in their hierarchy, see [The ISE Object Model Hierarchy](The-ISE-Object-Model-Hierarchy.md).</span></span>

 <span data-ttu-id="9bdb7-107">[ISEAddOnTool 对象](The-ISEAddOnTool-Object.md) 示例：$psISE.CurrentVisibleHorizontalTool、$psISE.CurrentVisibleVerticalTool。</span><span class="sxs-lookup"><span data-stu-id="9bdb7-107">[The ISEAddOnTool Object](The-ISEAddOnTool-Object.md) Examples: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.</span></span>

 <span data-ttu-id="9bdb7-108">[ISEAddOnTool 对象](The-ISEAddOnTool-Object.md) [ISEEditor 对象](The-ISEEditor-Object.md) 示例：$psISE.CurrentFile.Editor、$psISE.CurrentPowerShellTab.Output、$psISE.CurrentPowerShellTab.CommandPane。</span><span class="sxs-lookup"><span data-stu-id="9bdb7-108">[The ISEAddOnTool Object](The-ISEAddOnTool-Object.md) [The ISEEditor Object](The-ISEEditor-Object.md) Examples: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.</span></span>

 <span data-ttu-id="9bdb7-109">[ISEFile 对象](The-ISEFile-Object.md) 示例：$psISE.CurrentFile、$psISE.PowerShellTabs.Files\[0\]。</span><span class="sxs-lookup"><span data-stu-id="9bdb7-109">[The ISEFile Object](The-ISEFile-Object.md) Examples: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].</span></span>

 <span data-ttu-id="9bdb7-110">[ISEFileCollection 对象](The-ISEFileCollection-Object.md) 示例：$psISE.PowerShellTabs.Files。</span><span class="sxs-lookup"><span data-stu-id="9bdb7-110">[The ISEFileCollection Object](The-ISEFileCollection-Object.md) Examples: $psISE.PowerShellTabs.Files.</span></span>

 <span data-ttu-id="9bdb7-111">[ISEMenuItem 对象](The-ISEMenuItem-Object.md) 示例：$psISE.CurrentPowerShellTab.AddOnsMenu、$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\]。</span><span class="sxs-lookup"><span data-stu-id="9bdb7-111">[The ISEMenuItem Object](The-ISEMenuItem-Object.md) Examples: $psISE.CurrentPowerShellTab.AddOnsMenu , $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].</span></span>

 <span data-ttu-id="9bdb7-112">[ISEMenuItemCollection 对象](The-ISEMenuItemCollection-Object.md) 示例：$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus。</span><span class="sxs-lookup"><span data-stu-id="9bdb7-112">[The ISEMenuItemCollection Object](The-ISEMenuItemCollection-Object.md) Example: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.</span></span>

 <span data-ttu-id="9bdb7-113">[ISEOptions 对象](The-ISEOptions-Object.md) 示例：$psISE.Options、$psISE.Options.DefaultOptions。</span><span class="sxs-lookup"><span data-stu-id="9bdb7-113">[The ISEOptions Object](The-ISEOptions-Object.md) Examples: $psISE.Options, $psISE.Options.DefaultOptions.</span></span>

 <span data-ttu-id="9bdb7-114">[ObjectModelRoot 对象](The-ObjectModelRoot-Object.md) 示例：根 $psISE 对象。</span><span class="sxs-lookup"><span data-stu-id="9bdb7-114">[The ObjectModelRoot Object](The-ObjectModelRoot-Object.md) Example: The root $psISE object.</span></span>

 <span data-ttu-id="9bdb7-115">[PowerShellTab 对象](The-PowerShellTab-Object.md) 示例：$psISE.CurrentPowerShellTab、$psISE.PowerShellTabs\[0\]。</span><span class="sxs-lookup"><span data-stu-id="9bdb7-115">[The PowerShellTab Object](The-PowerShellTab-Object.md) Examples: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].</span></span>

 <span data-ttu-id="9bdb7-116">[PowerShellTabCollection 对象](The-PowerShellTabCollection-Object.md) 示例：$psISE.PowerShellTabs。</span><span class="sxs-lookup"><span data-stu-id="9bdb7-116">[The PowerShellTabCollection Object](The-PowerShellTabCollection-Object.md) Example: $psISE.PowerShellTabs.</span></span>

## <a name="see-also"></a><span data-ttu-id="9bdb7-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9bdb7-117">See Also</span></span>
- [<span data-ttu-id="9bdb7-118">Windows PowerShell ISE 脚本对象模型</span><span class="sxs-lookup"><span data-stu-id="9bdb7-118">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
