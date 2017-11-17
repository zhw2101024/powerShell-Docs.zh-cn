---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISE 对象模型层次结构"
ms.openlocfilehash: 2df6d40f39dbe14bd3f46a6400cde4a6e91052ef
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2017
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="dfbc7-103">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="dfbc7-103">The ISE Object Model Hierarchy</span></span>
<span data-ttu-id="dfbc7-104">本主题介绍了属于 Windows PowerShell 集成脚本环境 (ISE) 一部分的对象的层次结构。</span><span class="sxs-lookup"><span data-stu-id="dfbc7-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="dfbc7-105">在 Windows PowerShell 3.0 和 Windows PowerShell 4.0 中包含 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="dfbc7-105">Windows PowerShell ISE is included in Windows PowerShell 3.0 and in Windows PowerShell 4.0.</span></span> <span data-ttu-id="dfbc7-106">单击一个对象，使你转到定义对象的类的参考文档。</span><span class="sxs-lookup"><span data-stu-id="dfbc7-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

## <a name="psise-object"></a><span data-ttu-id="dfbc7-107">$psISE 对象</span><span class="sxs-lookup"><span data-stu-id="dfbc7-107">$psISE Object</span></span>

<span data-ttu-id="dfbc7-108">**$PsISE** 对象是 Windows PowerShell ISE 对象层次结构的[根对象](The-ObjectModelRoot-Object.md)。</span><span class="sxs-lookup"><span data-stu-id="dfbc7-108">The **$psISE** object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span>
<span data-ttu-id="dfbc7-109">它位于顶层，使以下对象可用于脚本编写：</span><span class="sxs-lookup"><span data-stu-id="dfbc7-109">Located at the top level, it makes the following objects available for scripting:</span></span>

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[<span data-ttu-id="dfbc7-110">$psISE.CurrentFile</span><span class="sxs-lookup"><span data-stu-id="dfbc7-110">$psISE.CurrentFile</span></span>](The-ISEFile-Object.md)

<span data-ttu-id="dfbc7-111">$PsISE.CurrentFile 对象是 [ISEFile](The-ISEFile-Object.md) 类的一个实例。</span><span class="sxs-lookup"><span data-stu-id="dfbc7-111">The **$psISE.CurrentFile** object is an instance of the [ISEFile](The-ISEFile-Object.md) class.</span></span>

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[<span data-ttu-id="dfbc7-112">$psISE.CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="dfbc7-112">$psISE.CurrentPowerShellTab</span></span>](The-PowerShellTab-Object.md)

<span data-ttu-id="dfbc7-113">**$PsISE.CurrentPowerShellTab**对象是的一个实例[PowerShellTab](The-PowerShellTab-Object.md)类。</span><span class="sxs-lookup"><span data-stu-id="dfbc7-113">The **$psISE.CurrentPowerShellTab** object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="dfbc7-114">$psISE.CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="dfbc7-114">$psISE.CurrentVisibleHorizontalTool</span></span>

<span data-ttu-id="dfbc7-115">**$PsISE.CurrentVisibleHorizontalTool** 对象是 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="dfbc7-115">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="dfbc7-116">它表示已安装的外接程序工具，当前停靠在 Windows PowerShell ISE 窗口的顶部。</span><span class="sxs-lookup"><span data-stu-id="dfbc7-116">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span>

## <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="dfbc7-117">$psISE.CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="dfbc7-117">$psISE.CurrentVisibleVerticalTool</span></span>

<span data-ttu-id="dfbc7-118">**$PsISE.CurrentVisibleHorizontalTool** 对象是 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="dfbc7-118">The **$psISE.CurrentVisibleHorizontalTool** object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span>
<span data-ttu-id="dfbc7-119">它表示已安装的外接程序工具，当前停靠在 Windows PowerShell ISE 窗口的右侧。</span><span class="sxs-lookup"><span data-stu-id="dfbc7-119">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span>

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[<span data-ttu-id="dfbc7-120">$psISE.Options</span><span class="sxs-lookup"><span data-stu-id="dfbc7-120">$psISE.Options</span></span>](The-ISEOptions-Object.md)

<span data-ttu-id="dfbc7-121">$PsISE.Options 对象是 [ISEOptions](The-ISEOptions-Object.md) 类的一个实例。</span><span class="sxs-lookup"><span data-stu-id="dfbc7-121">The **$psISE.Options** object is an instance of the [ISEOptions](The-ISEOptions-Object.md) class.</span></span>
<span data-ttu-id="dfbc7-122">ISEOptions 对象代表 Windows PowerShell ISE 的各种设置。</span><span class="sxs-lookup"><span data-stu-id="dfbc7-122">The ISEOptions object represents various settings for Windows PowerShell ISE.</span></span>
<span data-ttu-id="dfbc7-123">它是 Microsoft.PowerShell.Host.ISE.ISEOptions 类的实例。</span><span class="sxs-lookup"><span data-stu-id="dfbc7-123">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEOptions class.</span></span>

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[<span data-ttu-id="dfbc7-124">$psISE.PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="dfbc7-124">$psISE.PowerShellTabs</span></span>](The-PowerShellTabCollection-Object.md)

<span data-ttu-id="dfbc7-125">**$PsISE.PowerShellTabs** 对象是 [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="dfbc7-125">The **$psISE.PowerShellTabs** object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span>
<span data-ttu-id="dfbc7-126">它是所有当前打开的 PowerShell 选项卡的集合，表示本地计算机上或在已连接的远程计算机上可用的 Windows PowerShell 运行环境。</span><span class="sxs-lookup"><span data-stu-id="dfbc7-126">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span> <span data-ttu-id="dfbc7-127">集合中的每个成员均为 [PowerShellTab](The-PowerShellTab-Object.md) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="dfbc7-127">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="dfbc7-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dfbc7-128">See Also</span></span>
- [<span data-ttu-id="dfbc7-129">Windows PowerShell ISE 脚本对象模型</span><span class="sxs-lookup"><span data-stu-id="dfbc7-129">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="dfbc7-130">Windows PowerShell ISE 对象模型参考</span><span class="sxs-lookup"><span data-stu-id="dfbc7-130">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
