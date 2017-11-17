---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISESnippet 对象"
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: 6112f5252d2d1e868092da4a6cd04feb1875b597
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2017
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="adda8-103">ISESnippet 对象</span><span class="sxs-lookup"><span data-stu-id="adda8-103">The ISESnippetObject</span></span>
  <span data-ttu-id="adda8-104">**ISESnippet** 对象是 Microsoft.PowerShell.Host.ISE.ISESnippet 类的实例。</span><span class="sxs-lookup"><span data-stu-id="adda8-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="adda8-105">**$psISE.CurrentPowerShellTab.Snippets** 集合的成员均为 **ISESnippet** 对象的示例。</span><span class="sxs-lookup"><span data-stu-id="adda8-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="adda8-106">创建代码段的最简单方法是使用 [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="adda8-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="adda8-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="adda8-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="adda8-108">作者</span><span class="sxs-lookup"><span data-stu-id="adda8-108">Author</span></span>
  <span data-ttu-id="adda8-109">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="adda8-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="adda8-110">只读属性，可获取代码段作者的姓名。</span><span class="sxs-lookup"><span data-stu-id="adda8-110">The read-only property that gets the name of the author of the snippet.</span></span>

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

### <a name="codefragment"></a><span data-ttu-id="adda8-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="adda8-111">CodeFragment</span></span>
  <span data-ttu-id="adda8-112">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="adda8-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="adda8-113">只读属性，可获取要插入到编辑器中的代码片段。</span><span class="sxs-lookup"><span data-stu-id="adda8-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

### <a name="shortcut"></a><span data-ttu-id="adda8-114">快捷方式</span><span class="sxs-lookup"><span data-stu-id="adda8-114">Shortcut</span></span>
  <span data-ttu-id="adda8-115">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="adda8-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="adda8-116">只读属性，可获取菜单项的 Windows 键盘快捷方式。</span><span class="sxs-lookup"><span data-stu-id="adda8-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="adda8-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="adda8-117">See Also</span></span>
- [<span data-ttu-id="adda8-118">ISESnippetCollection 对象</span><span class="sxs-lookup"><span data-stu-id="adda8-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md) 
- [<span data-ttu-id="adda8-119">Windows PowerShell ISE 脚本对象模型</span><span class="sxs-lookup"><span data-stu-id="adda8-119">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="adda8-120">Windows PowerShell ISE 对象模型参考</span><span class="sxs-lookup"><span data-stu-id="adda8-120">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="adda8-121">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="adda8-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
