---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISESnippet 对象"
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: 5cc49cd504a1343a5737f78eb886bb41591d087d
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="1c0ea-103">ISESnippet 对象</span><span class="sxs-lookup"><span data-stu-id="1c0ea-103">The ISESnippetObject</span></span>
  <span data-ttu-id="1c0ea-104">**ISESnippet** 对象是 Microsoft.PowerShell.Host.ISE.ISESnippet 类的实例。</span><span class="sxs-lookup"><span data-stu-id="1c0ea-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="1c0ea-105">**$psISE.CurrentPowerShellTab.Snippets** 集合的成员均为 **ISESnippet** 对象的示例。</span><span class="sxs-lookup"><span data-stu-id="1c0ea-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="1c0ea-106">创建代码段的最简单方法是使用 [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1c0ea-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="1c0ea-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="1c0ea-107">Properties</span></span>

###  <span data-ttu-id="1c0ea-108"><a name="DisplayName"></a> 作者</span><span class="sxs-lookup"><span data-stu-id="1c0ea-108"><a name="DisplayName"></a> Author</span></span>
  <span data-ttu-id="1c0ea-109">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="1c0ea-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="1c0ea-110">只读属性，可获取代码段作者的姓名。</span><span class="sxs-lookup"><span data-stu-id="1c0ea-110">The read-only property that gets the name of the author of the snippet.</span></span>

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

###  <span data-ttu-id="1c0ea-111"><a name="Action"></a> CodeFragment</span><span class="sxs-lookup"><span data-stu-id="1c0ea-111"><a name="Action"></a> CodeFragment</span></span>
  <span data-ttu-id="1c0ea-112">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="1c0ea-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="1c0ea-113">只读属性，可获取要插入到编辑器中的代码片段。</span><span class="sxs-lookup"><span data-stu-id="1c0ea-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

###  <span data-ttu-id="1c0ea-114"><a name="Shortcut"></a> 快捷方式</span><span class="sxs-lookup"><span data-stu-id="1c0ea-114"><a name="Shortcut"></a> Shortcut</span></span>
  <span data-ttu-id="1c0ea-115">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="1c0ea-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="1c0ea-116">只读属性，可获取菜单项的 Windows 键盘快捷方式。</span><span class="sxs-lookup"><span data-stu-id="1c0ea-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="1c0ea-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1c0ea-117">See Also</span></span>
- [<span data-ttu-id="1c0ea-118">ISESnippetCollection 对象</span><span class="sxs-lookup"><span data-stu-id="1c0ea-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md) 
- [<span data-ttu-id="1c0ea-119">Windows PowerShell ISE 脚本对象模型</span><span class="sxs-lookup"><span data-stu-id="1c0ea-119">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="1c0ea-120">Windows PowerShell ISE 对象模型参考</span><span class="sxs-lookup"><span data-stu-id="1c0ea-120">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="1c0ea-121">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="1c0ea-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
