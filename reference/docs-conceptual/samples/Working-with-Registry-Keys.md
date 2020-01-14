---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 使用注册表项
ms.openlocfilehash: 3feaf6d26db51a507434a6cec1f1095c9013efc8
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736839"
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="c7aff-103">使用注册表项</span><span class="sxs-lookup"><span data-stu-id="c7aff-103">Working with Registry Keys</span></span>

<span data-ttu-id="c7aff-104">由于注册表项是 PowerShell 驱动器上的项，因此使用它们的方法和使用文件及文件夹的方法非常相似。</span><span class="sxs-lookup"><span data-stu-id="c7aff-104">Because registry keys are items on PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="c7aff-105">一个关键区别在于，基于注册表的 PowerShell 驱动器上的每个项都是一个容器，就像文件系统驱动器上有一个文件夹一样。</span><span class="sxs-lookup"><span data-stu-id="c7aff-105">One critical difference is that every item on a registry-based PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="c7aff-106">但是，注册表条目及其关联的值只是项的属性，而不是不同的项。</span><span class="sxs-lookup"><span data-stu-id="c7aff-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

## <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="c7aff-107">列出注册表项的所有子项</span><span class="sxs-lookup"><span data-stu-id="c7aff-107">Listing All Subkeys of a Registry Key</span></span>

<span data-ttu-id="c7aff-108">可以通过使用 `Get-ChildItem` 直接显示某个注册表项中的所有项目。</span><span class="sxs-lookup"><span data-stu-id="c7aff-108">You can show all items directly within a registry key by using `Get-ChildItem`.</span></span> <span data-ttu-id="c7aff-109">添加可选的 **Force** 参数以显示隐藏项或系统项。</span><span class="sxs-lookup"><span data-stu-id="c7aff-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="c7aff-110">例如，以下命令将直接显示 PowerShell 驱动器 `HKCU:`（对应于 `HKEY_CURRENT_USER` 注册表 Hive）中的项：</span><span class="sxs-lookup"><span data-stu-id="c7aff-110">For example, this command displays the items directly within PowerShell drive `HKCU:`, which corresponds to the `HKEY_CURRENT_USER` registry hive:</span></span>

```powershell
Get-ChildItem -Path HKCU:\ | Select-Object Name
```

```Output
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

Name
----
HKEY_CURRENT_USER\AppEvents
HKEY_CURRENT_USER\Console
HKEY_CURRENT_USER\Control Panel
HKEY_CURRENT_USER\DirectShow
HKEY_CURRENT_USER\dummy
HKEY_CURRENT_USER\Environment
HKEY_CURRENT_USER\EUDC
HKEY_CURRENT_USER\Keyboard Layout
HKEY_CURRENT_USER\MediaFoundation
HKEY_CURRENT_USER\Microsoft
HKEY_CURRENT_USER\Network
HKEY_CURRENT_USER\Printers
HKEY_CURRENT_USER\Software
HKEY_CURRENT_USER\System
HKEY_CURRENT_USER\Uninstall
HKEY_CURRENT_USER\WXP
HKEY_CURRENT_USER\Volatile Environment
```

<span data-ttu-id="c7aff-111">这些是注册表编辑器 (Regedit.exe) 中 `HKEY_CURRENT_USER` 下可见的顶级项。</span><span class="sxs-lookup"><span data-stu-id="c7aff-111">These are the top-level keys visible under `HKEY_CURRENT_USER` in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="c7aff-112">还可以通过指定注册表提供程序的名称（后跟“`::`”）来指定此注册表路径。</span><span class="sxs-lookup"><span data-stu-id="c7aff-112">You can also specify this registry path by specifying the registry provider's name, followed by `::`.</span></span> <span data-ttu-id="c7aff-113">注册表提供程序的全名是 `Microsoft.PowerShell.Core\Registry`，但是可以将其缩短为仅 `Registry`。</span><span class="sxs-lookup"><span data-stu-id="c7aff-113">The registry provider's full name is `Microsoft.PowerShell.Core\Registry`, but this can be shortened to just `Registry`.</span></span> <span data-ttu-id="c7aff-114">任一以下命令都可直接列出 `HKCU:` 下面的内容。</span><span class="sxs-lookup"><span data-stu-id="c7aff-114">Any of the following commands will list the contents directly under `HKCU:`.</span></span>

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="c7aff-115">这些命令将仅列出直接包含的项，类似于使用 Cmd.exe 中的 `DIR`  或 UNIX shell 中的 `ls`。</span><span class="sxs-lookup"><span data-stu-id="c7aff-115">These commands list only the directly contained items, much like using `DIR` in **Cmd.exe** or `ls` in a UNIX shell.</span></span> <span data-ttu-id="c7aff-116">为了显示包含的项，需要指定 **Recurse** 参数。</span><span class="sxs-lookup"><span data-stu-id="c7aff-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="c7aff-117">若要列出 `HKCU:` 中的所有注册表项，请使用以下命令。</span><span class="sxs-lookup"><span data-stu-id="c7aff-117">To list all registry keys in `HKCU:`, use the following command.</span></span>

```powershell
Get-ChildItem -Path HKCU:\ -Recurse
```

<span data-ttu-id="c7aff-118">`Get-ChildItem` 可以通过其 Path  、Filter  、Include  和 Exclude  参数执行复杂的筛选功能，但这些参数通常只基于名称。</span><span class="sxs-lookup"><span data-stu-id="c7aff-118">`Get-ChildItem` can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="c7aff-119">还可以通过使用 `Where-Object` cmdlet 基于项的其他属性执行复杂的筛选。</span><span class="sxs-lookup"><span data-stu-id="c7aff-119">You can perform complex filtering based on other properties of items by using the `Where-Object` cmdlet.</span></span> <span data-ttu-id="c7aff-120">下面的命令用于查找 `HKCU:\Software` 中不止只有一个子项并且刚好具有 4 个值的所有项：</span><span class="sxs-lookup"><span data-stu-id="c7aff-120">The following command finds all keys within `HKCU:\Software` that have no more than one subkey and also have exactly four values:</span></span>

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse |
  Where-Object {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a><span data-ttu-id="c7aff-121">复制项</span><span class="sxs-lookup"><span data-stu-id="c7aff-121">Copying Keys</span></span>

<span data-ttu-id="c7aff-122">复制通过 `Copy-Item` 完成。</span><span class="sxs-lookup"><span data-stu-id="c7aff-122">Copying is done with `Copy-Item`.</span></span> <span data-ttu-id="c7aff-123">下面的示例将 `HKLM:\SOFTWARE\Microsoft\Windows\` 的 `CurrentVersion` 子项及其所有属性复制到 `HKCU:\`。</span><span class="sxs-lookup"><span data-stu-id="c7aff-123">The following example copies the `CurrentVersion` subkey of `HKLM:\SOFTWARE\Microsoft\Windows\` and all of its properties to `HKCU:\`.</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU:
```

<span data-ttu-id="c7aff-124">如果你在注册表编辑器中或通过使用 `Get-ChildItem` 检查此新项，你会注意到在新位置中没有所包含子项的副本。</span><span class="sxs-lookup"><span data-stu-id="c7aff-124">If you examine this new key in the registry editor or by using `Get-ChildItem`, you notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="c7aff-125">为了复制容器的所有内容，需要指定 **Recurse** 参数。</span><span class="sxs-lookup"><span data-stu-id="c7aff-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="c7aff-126">若要使上述的复制命令递归，你将使用此命令：</span><span class="sxs-lookup"><span data-stu-id="c7aff-126">To make the preceding copy command recursive, you would use this command:</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU: -Recurse
```

<span data-ttu-id="c7aff-127">你仍然可以使用已有的其他可用工具执行文件系统复制。</span><span class="sxs-lookup"><span data-stu-id="c7aff-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="c7aff-128">任何注册表编辑工具（包括 reg.exe  、regini.exe  和 regedit.exe  ）以及支持注册表编辑的 COM 对象（如 WScript.Shell  和 WMI 的 StdRegProv  类）均可用于 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="c7aff-128">Any registry editing tools—including **reg.exe**, **regini.exe**, **regedit.exe**, and COM objects that support registry editing, such as **WScript.Shell** and WMI's **StdRegProv** class can be used from within Windows PowerShell.</span></span>

## <a name="creating-keys"></a><span data-ttu-id="c7aff-129">创建项</span><span class="sxs-lookup"><span data-stu-id="c7aff-129">Creating Keys</span></span>

<span data-ttu-id="c7aff-130">在注册表中创建新项比在文件系统中创建新项简单。</span><span class="sxs-lookup"><span data-stu-id="c7aff-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="c7aff-131">由于所有注册表项都是容器，因此，你无需指定项类型；只需提供一个明确的路径即可，如：</span><span class="sxs-lookup"><span data-stu-id="c7aff-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```powershell
New-Item -Path HKCU:\Software_DeleteMe
```

<span data-ttu-id="c7aff-132">此外还可以使用基于提供程序的路径来指定某项：</span><span class="sxs-lookup"><span data-stu-id="c7aff-132">You can also use a provider-based path to specify a key:</span></span>

```powershell
New-Item -Path Registry::HKCU\Software_DeleteMe
```

## <a name="deleting-keys"></a><span data-ttu-id="c7aff-133">删除项</span><span class="sxs-lookup"><span data-stu-id="c7aff-133">Deleting Keys</span></span>

<span data-ttu-id="c7aff-134">从本质而言，删除项对所有提供程序都是相同的。</span><span class="sxs-lookup"><span data-stu-id="c7aff-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="c7aff-135">以下命令将以无提示方式删除项：</span><span class="sxs-lookup"><span data-stu-id="c7aff-135">The following commands will silently remove items:</span></span>

```powershell
Remove-Item -Path HKCU:\Software_DeleteMe
Remove-Item -Path 'HKCU:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="c7aff-136">删除特定项下的所有项</span><span class="sxs-lookup"><span data-stu-id="c7aff-136">Removing All Keys Under a Specific Key</span></span>

<span data-ttu-id="c7aff-137">可以通过使用 `Remove-Item` 删除包含的项，但如果项包含任何其他内容，系统将提示你确认该删除。</span><span class="sxs-lookup"><span data-stu-id="c7aff-137">You can remove contained items by using `Remove-Item`, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="c7aff-138">例如，如果我们尝试删除我们创建的 `HKCU:\CurrentVersion` 子项，我们将看到：</span><span class="sxs-lookup"><span data-stu-id="c7aff-138">For example, if we attempt to delete the `HKCU:\CurrentVersion` subkey we created, we see this:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion
```

```Output
Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="c7aff-139">若要在无提示下删除包含的项，请指定 Recurse  参数：</span><span class="sxs-lookup"><span data-stu-id="c7aff-139">To delete contained items without prompting, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="c7aff-140">如果要删除 `HKCU:\CurrentVersion` 中的所有项，但不删除 `HKCU:\CurrentVersion` 本身，则可以改用：</span><span class="sxs-lookup"><span data-stu-id="c7aff-140">If you wanted to remove all items within `HKCU:\CurrentVersion` but not `HKCU:\CurrentVersion` itself, you could instead use:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```
