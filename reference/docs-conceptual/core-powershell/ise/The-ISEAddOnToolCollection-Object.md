---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISEAddOnToolCollection 对象
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: ff4f19d1a85a592f2f4f09c62caa0971751bdff7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="358cb-103">ISEAddOnToolCollection 对象</span><span class="sxs-lookup"><span data-stu-id="358cb-103">The ISEAddOnToolCollection Object</span></span>

<span data-ttu-id="358cb-104">**ISEAddOnToolCollection** 对象是 **ISEAddOnTool** 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="358cb-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="358cb-105">示例是 **$psISE.CurrentPowerShellTab.VerticalAddOnTools** 对象。</span><span class="sxs-lookup"><span data-stu-id="358cb-105">An example is the **$psISE.CurrentPowerShellTab.VerticalAddOnTools** object.</span></span>

## <a name="methods"></a><span data-ttu-id="358cb-106">方法</span><span class="sxs-lookup"><span data-stu-id="358cb-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="358cb-107">Add\( Name、ControlType、\[IsVisible\]\)</span><span class="sxs-lookup"><span data-stu-id="358cb-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>

<span data-ttu-id="358cb-108">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="358cb-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="358cb-109">将新附加工具添加到集合。</span><span class="sxs-lookup"><span data-stu-id="358cb-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="358cb-110">它将返回新添加的附加工具。</span><span class="sxs-lookup"><span data-stu-id="358cb-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="358cb-111">在运行此命令之前，必须在本地计算机上安装附加工具并加载程序集。</span><span class="sxs-lookup"><span data-stu-id="358cb-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

<span data-ttu-id="358cb-112">**Name** - 字符串，指定添加到 Windows PowerShell ISE 的附加工具的显示名称。</span><span class="sxs-lookup"><span data-stu-id="358cb-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

<span data-ttu-id="358cb-113">**ControlType** - 类型，指定要添加的控件。</span><span class="sxs-lookup"><span data-stu-id="358cb-113">**ControlType** -Type Specifies the control that is added.</span></span>

<span data-ttu-id="358cb-114">**\[IsVisible\]** - 可选布尔值，如果设置为 **$true**，可立即在关联的工具窗格中看到附加工具。</span><span class="sxs-lookup"><span data-stu-id="358cb-114">**\[IsVisible\]** - optional Boolean If set to **$true**, the add-on tool is immediately visible in the associated tool pane.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="358cb-115">Remove\( Item \)</span><span class="sxs-lookup"><span data-stu-id="358cb-115">Remove\( Item \)</span></span>

<span data-ttu-id="358cb-116">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="358cb-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="358cb-117">从集合中删除指定的附加工具。</span><span class="sxs-lookup"><span data-stu-id="358cb-117">Removes the specified add-on tool from the collection.</span></span>

<span data-ttu-id="358cb-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool，指定要从 Windows PowerShell ISE 删除的对象。</span><span class="sxs-lookup"><span data-stu-id="358cb-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="358cb-119">SetSelectedPowerShellTab\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="358cb-119">SetSelectedPowerShellTab\( psTab \)</span></span>

<span data-ttu-id="358cb-120">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="358cb-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="358cb-121">选择 **psTab** 参数指定的 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="358cb-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="358cb-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab，要选择的 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="358cb-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a><span data-ttu-id="358cb-123">Remove\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="358cb-123">Remove\( psTab \)</span></span>

<span data-ttu-id="358cb-124">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="358cb-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="358cb-125">删除 **psTab** 参数指定的 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="358cb-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="358cb-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab，要删除的 PowerShell 选项卡。</span><span class="sxs-lookup"><span data-stu-id="358cb-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="358cb-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="358cb-127">See Also</span></span>

- [<span data-ttu-id="358cb-128">PowerShellTab 对象</span><span class="sxs-lookup"><span data-stu-id="358cb-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="358cb-129">Windows PowerShell ISE 脚本对象模型的用途</span><span class="sxs-lookup"><span data-stu-id="358cb-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="358cb-130">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="358cb-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)