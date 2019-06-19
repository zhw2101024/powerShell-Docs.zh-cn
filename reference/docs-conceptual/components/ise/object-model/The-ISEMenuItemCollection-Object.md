---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISEMenuItemCollection 对象
ms.openlocfilehash: b3795af1a6ed61ed6e371e5fc20cc4e95f643fd4
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030540"
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="2017d-103">ISEMenuItemCollection 对象</span><span class="sxs-lookup"><span data-stu-id="2017d-103">The ISEMenuItemCollection Object</span></span>

<span data-ttu-id="2017d-104">**ISEMenuItemCollection** 对象是 **ISEMenuItem** 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="2017d-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="2017d-105">它是 Microsoft.PowerShell.Host.ISE.ISEOptions 类的实例。</span><span class="sxs-lookup"><span data-stu-id="2017d-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="2017d-106">一个示例是用于在 Windows PowerShell® 集成脚本环境 (ISE) 中自定义“加载项”  菜单的 **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** 对象。</span><span class="sxs-lookup"><span data-stu-id="2017d-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="2017d-107">方法</span><span class="sxs-lookup"><span data-stu-id="2017d-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="2017d-108">添加\(字符串 DisplayName、System.Management.Automation.ScriptBlock Action、System.Windows.Input.KeyGesture 快捷方式\)</span><span class="sxs-lookup"><span data-stu-id="2017d-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>

<span data-ttu-id="2017d-109">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="2017d-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2017d-110">将菜单项添加到集合。</span><span class="sxs-lookup"><span data-stu-id="2017d-110">Adds a menu item to the collection.</span></span>

<span data-ttu-id="2017d-111">**DisplayName** 要添加的菜单显示名称。</span><span class="sxs-lookup"><span data-stu-id="2017d-111">**DisplayName** The display name of the menu to be added.</span></span>

<span data-ttu-id="2017d-112">**Action** 用于指定与此菜单项关联的操作的 System.Management.Automation.ScriptBlock 对象  。</span><span class="sxs-lookup"><span data-stu-id="2017d-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

<span data-ttu-id="2017d-113">**Shortcut** 此操作的键盘快捷方式。</span><span class="sxs-lookup"><span data-stu-id="2017d-113">**Shortcut** The keyboard shortcut for the action.</span></span>

<span data-ttu-id="2017d-114">**Returns** 刚添加的 ISEMenuItem 对象。</span><span class="sxs-lookup"><span data-stu-id="2017d-114">**Returns** The ISEMenuItem object that was just added.</span></span>

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a><span data-ttu-id="2017d-115">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="2017d-115">Clear\(\)</span></span>

<span data-ttu-id="2017d-116">在 Windows PowerShell ISE 2.0 和更高版本中受支持。</span><span class="sxs-lookup"><span data-stu-id="2017d-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2017d-117">从菜单项中删除所有子菜单。</span><span class="sxs-lookup"><span data-stu-id="2017d-117">Removes all submenus from the menu item.</span></span>

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a><span data-ttu-id="2017d-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2017d-118">See Also</span></span>

- [<span data-ttu-id="2017d-119">ISEMenuItem 对象</span><span class="sxs-lookup"><span data-stu-id="2017d-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md)
- [<span data-ttu-id="2017d-120">Windows PowerShell ISE 脚本对象模型的用途</span><span class="sxs-lookup"><span data-stu-id="2017d-120">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="2017d-121">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="2017d-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
