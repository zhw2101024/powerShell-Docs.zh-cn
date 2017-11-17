---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISESnippetCollection 对象"
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: b19c5b5c88f7c8bd0d0c466c7861fa9288bdc7a2
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2017
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="af725-103">ISESnippetCollection 对象</span><span class="sxs-lookup"><span data-stu-id="af725-103">The ISESnippetCollection Object</span></span>
  <span data-ttu-id="af725-104">**ISESnippetCollection** 对象是 **ISESnippet** 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="af725-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="af725-105">与 **PowerShellTab** 对象关联的文件集合是此类的成员。</span><span class="sxs-lookup"><span data-stu-id="af725-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="af725-106">比如 **$psISE.CurrentPowerShellTab.Files** 集合。</span><span class="sxs-lookup"><span data-stu-id="af725-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="af725-107">方法</span><span class="sxs-lookup"><span data-stu-id="af725-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="af725-108">Load\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="af725-108">Load\( FilePathName \)</span></span>
  <span data-ttu-id="af725-109">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="af725-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="af725-110">加载包含用户定义的代码段的 .snippets.ps1xml 文件。</span><span class="sxs-lookup"><span data-stu-id="af725-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="af725-111">创建代码段最简单的方法就是使用 New-IseSnippet cmdlet，后者会自动将它们存储在配置文件文件夹中，以便你每次启动 Windows PowerShell ISE 时进行加载。</span><span class="sxs-lookup"><span data-stu-id="af725-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

 <span data-ttu-id="af725-112">**FilePathName** - 字符串，包含代码段定义的 .snippets.ps1xml 文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="af725-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## <a name="see-also"></a><span data-ttu-id="af725-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="af725-113">See Also</span></span>
- [<span data-ttu-id="af725-114">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="af725-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md) 
- [<span data-ttu-id="af725-115">Windows PowerShell ISE 脚本对象模型</span><span class="sxs-lookup"><span data-stu-id="af725-115">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="af725-116">Windows PowerShell ISE 对象模型参考</span><span class="sxs-lookup"><span data-stu-id="af725-116">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="af725-117">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="af725-117">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
