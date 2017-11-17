---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISEMenuItem 对象"
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 5561955040e56110a6af0619c286548f5812fb47
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2017
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="08ed6-103">ISEMenuItem 对象</span><span class="sxs-lookup"><span data-stu-id="08ed6-103">The ISEMenuItem Object</span></span>
  <span data-ttu-id="08ed6-104">**ISEMenuItem** 对象是 Microsoft.PowerShell.Host.ISE.ISEMenuItem 类的实例。</span><span class="sxs-lookup"><span data-stu-id="08ed6-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="08ed6-105">“**加载项**”菜单上的所有对象都是 **Microsoft.PowerShell.Host.ISE.ISEMenuItem** 类的实例。</span><span class="sxs-lookup"><span data-stu-id="08ed6-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="08ed6-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="08ed6-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="08ed6-107">DisplayName</span><span class="sxs-lookup"><span data-stu-id="08ed6-107">DisplayName</span></span>
  <span data-ttu-id="08ed6-108">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="08ed6-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="08ed6-109">只读属性，可获取菜单项的显示名称。</span><span class="sxs-lookup"><span data-stu-id="08ed6-109">The read-only property that gets the display name of the menu item.</span></span>

```
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName

```

### <a name="action"></a><span data-ttu-id="08ed6-110">操作</span><span class="sxs-lookup"><span data-stu-id="08ed6-110">Action</span></span>
  <span data-ttu-id="08ed6-111">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="08ed6-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="08ed6-112">只读属性，可获取脚本块。</span><span class="sxs-lookup"><span data-stu-id="08ed6-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="08ed6-113">单击菜单项时，它将调用该操作。</span><span class="sxs-lookup"><span data-stu-id="08ed6-113">It invokes the action when you click the menu item.</span></span>

```
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item 
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="08ed6-114">快捷方式</span><span class="sxs-lookup"><span data-stu-id="08ed6-114">Shortcut</span></span>
  <span data-ttu-id="08ed6-115">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="08ed6-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="08ed6-116">只读属性，可获取菜单项的 Windows 输入键盘快捷方式。</span><span class="sxs-lookup"><span data-stu-id="08ed6-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="08ed6-117">子菜单</span><span class="sxs-lookup"><span data-stu-id="08ed6-117">Submenus</span></span>
  <span data-ttu-id="08ed6-118">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="08ed6-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="08ed6-119">只读属性，可获取菜单项的[子菜单列表](The-ISEMenuItemCollection-Object.md)。</span><span class="sxs-lookup"><span data-stu-id="08ed6-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="08ed6-120">脚本示例</span><span class="sxs-lookup"><span data-stu-id="08ed6-120">Scripting example</span></span>
 <span data-ttu-id="08ed6-121">若要更好地了解加载项菜单及其可编写脚本属性的使用，请通读下面的脚本示例。</span><span class="sxs-lookup"><span data-stu-id="08ed6-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

```

# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu - a parent and a child submenu item. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")

```

## <a name="see-also"></a><span data-ttu-id="08ed6-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="08ed6-122">See Also</span></span>
- [<span data-ttu-id="08ed6-123">ISEMenuItemCollection 对象</span><span class="sxs-lookup"><span data-stu-id="08ed6-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md) 
- [<span data-ttu-id="08ed6-124">Windows PowerShell ISE 脚本对象模型</span><span class="sxs-lookup"><span data-stu-id="08ed6-124">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="08ed6-125">Windows PowerShell ISE 对象模型参考</span><span class="sxs-lookup"><span data-stu-id="08ed6-125">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="08ed6-126">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="08ed6-126">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
