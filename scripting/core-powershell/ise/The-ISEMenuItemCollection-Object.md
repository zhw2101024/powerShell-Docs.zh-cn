---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISEMenuItemCollection 对象"
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7ce9132021d4d5e755503e0adb355beb388a625a
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="95810-103">ISEMenuItemCollection 对象</span><span class="sxs-lookup"><span data-stu-id="95810-103">The ISEMenuItemCollection Object</span></span>
  <span data-ttu-id="95810-104">**ISEMenuItemCollection** 对象是 **ISEMenuItem** 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="95810-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="95810-105">它是 Microsoft.PowerShell.Host.ISE.ISEOptions 类的实例。</span><span class="sxs-lookup"><span data-stu-id="95810-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="95810-106">一个示例是用于在 Windows PowerShell® 集成脚本环境 (ISE) 中自定义“加载项”菜单的 **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** 对象。</span><span class="sxs-lookup"><span data-stu-id="95810-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="95810-107">方法</span><span class="sxs-lookup"><span data-stu-id="95810-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="95810-108">添加\(字符串 DisplayName、System.Management.Automation.ScriptBlock Action、System.Windows.Input.KeyGesture 快捷方式\)</span><span class="sxs-lookup"><span data-stu-id="95810-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>
  <span data-ttu-id="95810-109">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="95810-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="95810-110">将菜单项添加到集合。</span><span class="sxs-lookup"><span data-stu-id="95810-110">Adds a menu item to the collection.</span></span>

 <span data-ttu-id="95810-111">**DisplayName**
 要添加的菜单显示名称。</span><span class="sxs-lookup"><span data-stu-id="95810-111">**DisplayName**
 The display name of the menu to be added.</span></span>

 <span data-ttu-id="95810-112">**Action**
 **System.Management.Automation.ScriptBlock** 对象指定与此菜单项关联的操作。</span><span class="sxs-lookup"><span data-stu-id="95810-112">**Action**
 The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

 <span data-ttu-id="95810-113">**Shortcut**
 此操作的键盘快捷方式。</span><span class="sxs-lookup"><span data-stu-id="95810-113">**Shortcut**
 The keyboard shortcut for the action.</span></span>

 <span data-ttu-id="95810-114">**Returns**
 刚添加 ISEMenuItem 对象。</span><span class="sxs-lookup"><span data-stu-id="95810-114">**Returns**
 The ISEMenuItem object that was just added.</span></span>

```
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
```

### <a name="clear"></a><span data-ttu-id="95810-115">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="95810-115">Clear\(\)</span></span>
  <span data-ttu-id="95810-116">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="95810-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="95810-117">从菜单项中删除所有子菜单。</span><span class="sxs-lookup"><span data-stu-id="95810-117">Removes all submenus from the menu item.</span></span>

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## <a name="see-also"></a><span data-ttu-id="95810-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="95810-118">See Also</span></span>
- [<span data-ttu-id="95810-119">ISEMenuItem 对象</span><span class="sxs-lookup"><span data-stu-id="95810-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md) 
- [<span data-ttu-id="95810-120">Windows PowerShell ISE 脚本对象模型</span><span class="sxs-lookup"><span data-stu-id="95810-120">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="95810-121">Windows PowerShell ISE 对象模型参考</span><span class="sxs-lookup"><span data-stu-id="95810-121">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="95810-122">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="95810-122">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
