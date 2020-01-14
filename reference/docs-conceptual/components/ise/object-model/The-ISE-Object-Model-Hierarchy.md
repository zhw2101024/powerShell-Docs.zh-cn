---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: ISE 对象模型层次结构
ms.openlocfilehash: 1ec5810fc5e7b765c2a08af83bce0415dd61a54b
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737026"
---
# <a name="the-ise-object-model-hierarchy"></a><span data-ttu-id="2cd73-103">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="2cd73-103">The ISE Object Model Hierarchy</span></span>

<span data-ttu-id="2cd73-104">本主题介绍了属于 Windows PowerShell 集成脚本环境 (ISE) 一部分的对象的层次结构。</span><span class="sxs-lookup"><span data-stu-id="2cd73-104">This topic shows the hierarchy of objects that are part of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="2cd73-105">在 Windows PowerShell 3.0、4.0 和 5.1 中包含 Windows PowerShell ISE。</span><span class="sxs-lookup"><span data-stu-id="2cd73-105">Windows PowerShell ISE is included in Windows PowerShell 3.0, 4.0, and 5.1.</span></span> <span data-ttu-id="2cd73-106">单击一个对象，使你转到定义对象的类的参考文档。</span><span class="sxs-lookup"><span data-stu-id="2cd73-106">Click an object to take you to the reference documentation for the class that defines the object.</span></span>

## <a name="psise-object"></a><span data-ttu-id="2cd73-107">$psISE 对象</span><span class="sxs-lookup"><span data-stu-id="2cd73-107">$psISE Object</span></span>

<span data-ttu-id="2cd73-108">`$psISE` 对象是 Windows PowerShell ISE 对象层次结构的[根对象](The-ObjectModelRoot-Object.md)。</span><span class="sxs-lookup"><span data-stu-id="2cd73-108">The `$psISE` object is the [root object](The-ObjectModelRoot-Object.md) of the Windows PowerShell ISE object hierarchy.</span></span> <span data-ttu-id="2cd73-109">它位于顶层，使以下对象可用于脚本编写：</span><span class="sxs-lookup"><span data-stu-id="2cd73-109">Located at the top level, it makes the following objects available for scripting:</span></span>

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[<span data-ttu-id="2cd73-110">$psISE.CurrentFile</span><span class="sxs-lookup"><span data-stu-id="2cd73-110">$psISE.CurrentFile</span></span>](The-ISEFile-Object.md)

<span data-ttu-id="2cd73-111">`$psISE.CurrentFile` 对象是 [ISEFile](The-ISEFile-Object.md) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="2cd73-111">The `$psISE.CurrentFile` object is an instance of the [ISEFile](The-ISEFile-Object.md) class.</span></span>

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[<span data-ttu-id="2cd73-112">$psISE.CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="2cd73-112">$psISE.CurrentPowerShellTab</span></span>](The-PowerShellTab-Object.md)

<span data-ttu-id="2cd73-113">`$psISE.CurrentPowerShellTab` 对象是 [PowerShellTab](The-PowerShellTab-Object.md) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="2cd73-113">The `$psISE.CurrentPowerShellTab` object is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="psisecurrentvisiblehorizontaltool"></a><span data-ttu-id="2cd73-114">$psISE.CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="2cd73-114">$psISE.CurrentVisibleHorizontalTool</span></span>

<span data-ttu-id="2cd73-115">`$psISE.CurrentVisibleHorizontalTool` 对象是 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="2cd73-115">The `$psISE.CurrentVisibleHorizontalTool` object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="2cd73-116">它表示已安装的外接程序工具，当前停靠在 Windows PowerShell ISE 窗口的顶部。</span><span class="sxs-lookup"><span data-stu-id="2cd73-116">It represents the installed add-on tool that is currently docked to the top edge of the Windows PowerShell ISE window.</span></span>

## <a name="psisecurrentvisibleverticaltool"></a><span data-ttu-id="2cd73-117">$psISE.CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="2cd73-117">$psISE.CurrentVisibleVerticalTool</span></span>

<span data-ttu-id="2cd73-118">`$psISE.CurrentVisibleHorizontalTool` 对象是 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="2cd73-118">The `$psISE.CurrentVisibleHorizontalTool` object is an instance of the [ISEAddOnTool](The-ISEAddOnTool-Object.md) class.</span></span> <span data-ttu-id="2cd73-119">它表示已安装的外接程序工具，当前停靠在 Windows PowerShell ISE 窗口的右侧。</span><span class="sxs-lookup"><span data-stu-id="2cd73-119">It represents the installed add-on tool that is currently docked to the right-hand edge of the Windows PowerShell ISE window.</span></span>

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[<span data-ttu-id="2cd73-120">$psISE.Options</span><span class="sxs-lookup"><span data-stu-id="2cd73-120">$psISE.Options</span></span>](The-ISEOptions-Object.md)

<span data-ttu-id="2cd73-121">`$psISE.Options` 对象是 [ISEOptions](The-ISEOptions-Object.md) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="2cd73-121">The `$psISE.Options` object is an instance of the [ISEOptions](The-ISEOptions-Object.md) class.</span></span> <span data-ttu-id="2cd73-122">ISEOptions 对象代表 Windows PowerShell ISE 的各种设置。</span><span class="sxs-lookup"><span data-stu-id="2cd73-122">The ISEOptions object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="2cd73-123">它是 Microsoft.PowerShell.Host.ISE.ISEOptions 类的实例。</span><span class="sxs-lookup"><span data-stu-id="2cd73-123">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEOptions class.</span></span>

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[<span data-ttu-id="2cd73-124">$psISE.PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="2cd73-124">$psISE.PowerShellTabs</span></span>](The-PowerShellTabCollection-Object.md)

<span data-ttu-id="2cd73-125">`$psISE.PowerShellTabs` 对象是 [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="2cd73-125">The `$psISE.PowerShellTabs` object is an instance of the [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) class.</span></span> <span data-ttu-id="2cd73-126">它是所有当前打开的 PowerShell 选项卡的集合，表示本地计算机上或在已连接的远程计算机上可用的 Windows PowerShell 运行环境。</span><span class="sxs-lookup"><span data-stu-id="2cd73-126">It is a collection of all the currently open PowerShell tabs that represent the available Windows PowerShell run environments on the local computer or on connected remote computers.</span></span> <span data-ttu-id="2cd73-127">集合中的每个成员均为 [PowerShellTab](The-PowerShellTab-Object.md) 类的实例。</span><span class="sxs-lookup"><span data-stu-id="2cd73-127">Each member in the collection is an instance of the [PowerShellTab](The-PowerShellTab-Object.md) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="2cd73-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2cd73-128">See Also</span></span>

- [<span data-ttu-id="2cd73-129">Windows PowerShell ISE 脚本对象模型的用途</span><span class="sxs-lookup"><span data-stu-id="2cd73-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="2cd73-130">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="2cd73-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
