---
ms.date: 2017-08-25
keywords: powershell,cmdlet
title: "ObjectModelRoot 对象"
ms.openlocfilehash: eb3424ff147c35364fa08543d59ebd30f6d2d857
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2017
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="3fcd3-103">ObjectModelRoot 对象</span><span class="sxs-lookup"><span data-stu-id="3fcd3-103">The ObjectModelRoot Object</span></span>

<span data-ttu-id="3fcd3-104">Windows PowerShell® 集成脚本环境 (ISE) 中的主体根对象（**$psISE** 对象）是 Microsoft.PowerShell.Host.ISE.ObjectModelRoot 类的实例。</span><span class="sxs-lookup"><span data-stu-id="3fcd3-104">The **$psISE** object, which is the principal root object in Windows PowerShell® Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span>
<span data-ttu-id="3fcd3-105">本主题介绍 **ObjectModelRoot** 对象的属性。</span><span class="sxs-lookup"><span data-stu-id="3fcd3-105">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="3fcd3-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="3fcd3-106">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="3fcd3-107">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="3fcd3-107">CurrentFile</span></span>

> <span data-ttu-id="3fcd3-108">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="3fcd3-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="3fcd3-109">只读属性，可获取与该主机对象相关联的当前具有焦点的文件。</span><span class="sxs-lookup"><span data-stu-id="3fcd3-109">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="3fcd3-110">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="3fcd3-110">CurrentPowerShellTab</span></span>

> <span data-ttu-id="3fcd3-111">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="3fcd3-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="3fcd3-112">只读属性，可获取具有焦点的 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="3fcd3-112">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="3fcd3-113">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="3fcd3-113">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="3fcd3-114">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="3fcd3-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="3fcd3-115">只读属性，可获取位于编辑器底部水平工具窗格中、当前可见的 Windows PowerShell ISE 加载项工具。</span><span class="sxs-lookup"><span data-stu-id="3fcd3-115">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="3fcd3-116">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="3fcd3-116">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="3fcd3-117">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="3fcd3-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="3fcd3-118">只读属性，可获取位于编辑器右侧竖直工具窗格中、当前可见的 Windows PowerShell ISE 加载项工具。</span><span class="sxs-lookup"><span data-stu-id="3fcd3-118">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="3fcd3-119">选项</span><span class="sxs-lookup"><span data-stu-id="3fcd3-119">Options</span></span>

> <span data-ttu-id="3fcd3-120">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="3fcd3-120">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="3fcd3-121">只读属性，可获取可以更改 Windows PowerShell ISE 中设置的各种选项。</span><span class="sxs-lookup"><span data-stu-id="3fcd3-121">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="3fcd3-122">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="3fcd3-122">PowerShellTabs</span></span>

> <span data-ttu-id="3fcd3-123">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="3fcd3-123">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="3fcd3-124">只读属性，可获取 Windows PowerShell ISE 中打开的 PowerShell 选项卡的集合。</span><span class="sxs-lookup"><span data-stu-id="3fcd3-124">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="3fcd3-125">默认情况下，此对象包含一个 PowerShell 选项卡。但是，可以将更多 PowerShell 选项卡添加到此对象中，方法是通过使用脚本或者使用 Windows PowerShell ISE 中的菜单。</span><span class="sxs-lookup"><span data-stu-id="3fcd3-125">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="3fcd3-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3fcd3-126">See Also</span></span>

- [<span data-ttu-id="3fcd3-127">Windows PowerShell ISE 脚本对象模型</span><span class="sxs-lookup"><span data-stu-id="3fcd3-127">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="3fcd3-128">Windows PowerShell ISE 对象模型参考</span><span class="sxs-lookup"><span data-stu-id="3fcd3-128">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="3fcd3-129">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="3fcd3-129">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
