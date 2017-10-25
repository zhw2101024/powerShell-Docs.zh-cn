---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "使用注册表项"
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: efb2c016afa2212c2907c0740ad26c4e4cddd3af
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2017
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="15cc7-103">使用注册表项</span><span class="sxs-lookup"><span data-stu-id="15cc7-103">Working with Registry Keys</span></span>
<span data-ttu-id="15cc7-104">由于注册表项是 Windows PowerShell 驱动器上的项，因此使用它们的方法和使用文件及文件夹的方法非常相似。</span><span class="sxs-lookup"><span data-stu-id="15cc7-104">Because registry keys are items on Windows PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="15cc7-105">一个关键区别在于，基于注册表的 Windows PowerShell 驱动器上的每个项都是一个容器，就像文件系统驱动器上有一个文件夹一样。</span><span class="sxs-lookup"><span data-stu-id="15cc7-105">One critical difference is that every item on a registry-based Windows PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="15cc7-106">但是，注册表条目及其关联的值只是项的属性，而不是不同的项。</span><span class="sxs-lookup"><span data-stu-id="15cc7-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

### <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="15cc7-107">列出注册表项的所有子项</span><span class="sxs-lookup"><span data-stu-id="15cc7-107">Listing All Subkeys of a Registry Key</span></span>
<span data-ttu-id="15cc7-108">可以通过使用 **Get-ChildItem** 直接显示某个注册表项中的所有项目。</span><span class="sxs-lookup"><span data-stu-id="15cc7-108">You can show all items directly within a registry key by using **Get-ChildItem**.</span></span> <span data-ttu-id="15cc7-109">添加可选的 **Force** 参数以显示隐藏项或系统项。</span><span class="sxs-lookup"><span data-stu-id="15cc7-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="15cc7-110">例如，以下命令将直接显示 Windows PowerShell 驱动器 HKCU（对应于 HKEY_CURRENT_USER 注册表 Hive）中的项：</span><span class="sxs-lookup"><span data-stu-id="15cc7-110">For example, this command displays the items directly within Windows PowerShell drive HKCU:, which corresponds to the HKEY_CURRENT_USER registry hive:</span></span>

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

<span data-ttu-id="15cc7-111">这些是注册表编辑器 (Regedit.exe) 中 HKEY_CURRENT_USER 下可见的顶级项。</span><span class="sxs-lookup"><span data-stu-id="15cc7-111">These are the top-level keys visible under HKEY_CURRENT_USER in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="15cc7-112">还可以通过指定注册表提供程序的名称（后跟“**::**”）来指定此注册表路径。</span><span class="sxs-lookup"><span data-stu-id="15cc7-112">You can also specify this registry path by specifying the registry provider's name, followed by "**::**".</span></span> <span data-ttu-id="15cc7-113">注册表提供程序的全名是 **Microsoft.PowerShell.Core\\Registry**，但此名称可以缩短至只有 **Registry**。</span><span class="sxs-lookup"><span data-stu-id="15cc7-113">The registry provider's full name is **Microsoft.PowerShell.Core\\Registry**, but this can be shortened to just **Registry**.</span></span> <span data-ttu-id="15cc7-114">任一以下命令都可直接列出 HKCU 下面的内容：</span><span class="sxs-lookup"><span data-stu-id="15cc7-114">Any of the following commands will list the contents directly under HKCU:</span></span>

```
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="15cc7-115">这些命令将仅列出直接包含的项，类似于使用 Cmd.exe 的 **DIR** 命令或 UNIX shell 中的 **ls**。</span><span class="sxs-lookup"><span data-stu-id="15cc7-115">These commands list only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="15cc7-116">为了显示包含的项，需要指定 **Recurse** 参数。</span><span class="sxs-lookup"><span data-stu-id="15cc7-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="15cc7-117">若要列出 HKCU 中的所有注册表项，请使用以下命令（此操作可能需要很长的时间。）：</span><span class="sxs-lookup"><span data-stu-id="15cc7-117">To list all registry keys in HKCU, use the following command (This operation can take an extremely long time.):</span></span>

```
Get-ChildItem -Path hkcu:\ -Recurse
```

<span data-ttu-id="15cc7-118">**Get-ChildItem** 可以通过其 **Path**、**Filter**、**Include** 和 **Exclude** 参数执行复杂的筛选功能，但这些参数通常只基于名称。</span><span class="sxs-lookup"><span data-stu-id="15cc7-118">**Get-ChildItem** can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="15cc7-119">还可以通过使用 **Where-Object**cmdlet 基于项的其他属性执行复杂的筛选。</span><span class="sxs-lookup"><span data-stu-id="15cc7-119">You can perform complex filtering based on other properties of items by using the **Where-Object**cmdlet.</span></span> <span data-ttu-id="15cc7-120">下面的命令用于查找不止只有一个子项并且刚好具有 4 个值的 HKCU:\\Software 中的所有项：</span><span class="sxs-lookup"><span data-stu-id="15cc7-120">The following command finds all keys within HKCU:\\Software that have no more than one subkey and also have exactly four values:</span></span>

```
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### <a name="copying-keys"></a><span data-ttu-id="15cc7-121">复制项</span><span class="sxs-lookup"><span data-stu-id="15cc7-121">Copying Keys</span></span>
<span data-ttu-id="15cc7-122">复制通过 **Copy-Item** 完成。</span><span class="sxs-lookup"><span data-stu-id="15cc7-122">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="15cc7-123">下面的命令将 HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion 及其所有属性复制到 HKCU:\\，从而创建名为“CurrentVersion”的新项：</span><span class="sxs-lookup"><span data-stu-id="15cc7-123">The following command copies HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion and all of its properties to HKCU:\\, creating a new key named "CurrentVersion":</span></span>

```
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

<span data-ttu-id="15cc7-124">如果你在注册表编辑器中检查此新项或通过使用 **Get-ChildItem**，你会注意到在新位置中没有包含的子项的副本。</span><span class="sxs-lookup"><span data-stu-id="15cc7-124">If you examine this new key in the registry editor or by using **Get-ChildItem**, you will notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="15cc7-125">为了复制容器的所有内容，需要指定 **Recurse** 参数。</span><span class="sxs-lookup"><span data-stu-id="15cc7-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="15cc7-126">若要使上述的复制命令递归，你将使用此命令：</span><span class="sxs-lookup"><span data-stu-id="15cc7-126">To make the preceding copy command recursive, you would use this command:</span></span>

```
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

<span data-ttu-id="15cc7-127">你仍然可以使用已有的其他可用工具执行文件系统复制。</span><span class="sxs-lookup"><span data-stu-id="15cc7-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="15cc7-128">任何注册表编辑工具（包括 reg.exe、regini.exe 和 regedit.exe）以及支持注册表编辑的 COM 对象（如 WScript.Shell 和 WMI 的 StdRegProv 类）均可用于 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="15cc7-128">Any registry editing tools—including reg.exe, regini.exe, and regedit.exe—and COM objects that support registry editing (such as WScript.Shell and WMI's StdRegProv class) can be used from within Windows PowerShell.</span></span>

### <a name="creating-keys"></a><span data-ttu-id="15cc7-129">创建项</span><span class="sxs-lookup"><span data-stu-id="15cc7-129">Creating Keys</span></span>
<span data-ttu-id="15cc7-130">在注册表中创建新项比在文件系统中创建新项简单。</span><span class="sxs-lookup"><span data-stu-id="15cc7-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="15cc7-131">由于所有注册表项都是容器，因此，你无需指定项类型；只需提供一个明确的路径即可，如：</span><span class="sxs-lookup"><span data-stu-id="15cc7-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```
New-Item -Path hkcu:\software_DeleteMe
```

<span data-ttu-id="15cc7-132">此外还可以使用基于提供程序的路径来指定某项：</span><span class="sxs-lookup"><span data-stu-id="15cc7-132">You can also use a provider-based path to specify a key:</span></span>

```
New-Item -Path Registry::HKCU_DeleteMe
```

### <a name="deleting-keys"></a><span data-ttu-id="15cc7-133">删除项</span><span class="sxs-lookup"><span data-stu-id="15cc7-133">Deleting Keys</span></span>
<span data-ttu-id="15cc7-134">从本质而言，删除项对所有提供程序都是相同的。</span><span class="sxs-lookup"><span data-stu-id="15cc7-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="15cc7-135">以下命令将以无提示方式删除项：</span><span class="sxs-lookup"><span data-stu-id="15cc7-135">The following commands will silently remove items:</span></span>

```
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="15cc7-136">删除特定项下的所有项</span><span class="sxs-lookup"><span data-stu-id="15cc7-136">Removing All Keys Under a Specific Key</span></span>
<span data-ttu-id="15cc7-137">可以通过使用 **Remove-Item** 删除包含的项，但如果项包含任何其他内容，系统将提示你确认该删除。</span><span class="sxs-lookup"><span data-stu-id="15cc7-137">You can remove contained items by using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="15cc7-138">例如，如果我们尝试删除我们创建的 HKCU:\\CurrentVersion 子项，我们将看到：</span><span class="sxs-lookup"><span data-stu-id="15cc7-138">For example, if we attempt to delete the HKCU:\\CurrentVersion subkey we created, we see this:</span></span>

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="15cc7-139">若要在无提示下删除包含的项，请指定 **-Recurse** 参数：</span><span class="sxs-lookup"><span data-stu-id="15cc7-139">To delete contained items without prompting, specify the **-Recurse** parameter:</span></span>

```
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="15cc7-140">如果想要删除 HKCU:\\CurrentVersion 中的所有项而不是 HKCU:\\CurrentVersion 本身，则可以改为使用：</span><span class="sxs-lookup"><span data-stu-id="15cc7-140">If you wanted to remove all items within HKCU:\\CurrentVersion but not HKCU:\\CurrentVersion itself, you could instead use:</span></span>

```
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```

