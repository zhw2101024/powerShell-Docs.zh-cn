---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISESnippetCollection 对象
ms.openlocfilehash: 6c392c08767fba004f63155d5a469777856a0b59
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030496"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="58170-103">ISESnippetCollection 对象</span><span class="sxs-lookup"><span data-stu-id="58170-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="58170-104">**ISESnippetCollection** 对象是 **ISESnippet** 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="58170-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="58170-105">与 **PowerShellTab** 对象关联的文件集合是此类的成员。</span><span class="sxs-lookup"><span data-stu-id="58170-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="58170-106">比如 **$psISE.CurrentPowerShellTab.Files** 集合。</span><span class="sxs-lookup"><span data-stu-id="58170-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="58170-107">方法</span><span class="sxs-lookup"><span data-stu-id="58170-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="58170-108">Load\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="58170-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="58170-109">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="58170-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="58170-110">加载包含用户定义的代码段的 .snippets.ps1xml 文件。</span><span class="sxs-lookup"><span data-stu-id="58170-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="58170-111">创建代码段最简单的方法就是使用 New-IseSnippet cmdlet，后者会自动将它们存储在配置文件文件夹中，以便你每次启动 Windows PowerShell ISE 时进行加载。</span><span class="sxs-lookup"><span data-stu-id="58170-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="58170-112">**FilePathName** - 字符串，包含代码段定义的 .snippets.ps1xml 文件的路径和文件名。</span><span class="sxs-lookup"><span data-stu-id="58170-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="58170-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="58170-113">See Also</span></span>

- [<span data-ttu-id="58170-114">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="58170-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="58170-115">Windows PowerShell ISE 脚本对象模型的用途</span><span class="sxs-lookup"><span data-stu-id="58170-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="58170-116">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="58170-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
