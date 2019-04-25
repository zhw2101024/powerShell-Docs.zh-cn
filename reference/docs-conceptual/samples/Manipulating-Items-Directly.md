---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 直接操作项
ms.assetid: 8cbd4867-917d-41ea-9ff0-b8e765509735
ms.openlocfilehash: 4caa7d2e0eecff9783556062d8503fe10e616fe5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086215"
---
# <a name="manipulating-items-directly"></a><span data-ttu-id="ad72a-103">直接操作项</span><span class="sxs-lookup"><span data-stu-id="ad72a-103">Manipulating Items Directly</span></span>

<span data-ttu-id="ad72a-104">在 Windows PowerShell 驱动器中看到的元素（例如文件系统驱动器中的文件和文件夹），以及 Windows PowerShell 注册表驱动器中的注册表项在 Windows PowerShell 中均称为*项*。</span><span class="sxs-lookup"><span data-stu-id="ad72a-104">The elements that you see in Windows PowerShell drives, such as the files and folders in the file system drives, and the registry keys in the Windows PowerShell registry drives, are called *items* in Windows PowerShell.</span></span> <span data-ttu-id="ad72a-105">用于使用这些项的 cmdlet 名称中具有名词 **Item**。</span><span class="sxs-lookup"><span data-stu-id="ad72a-105">The cmdlets for working with them item have the noun **Item** in their names.</span></span>

<span data-ttu-id="ad72a-106">**Get-Command -Noun Item** 命令的输出显示有九个 Windows PowerShell 项 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ad72a-106">The output of the **Get-Command -Noun Item** command shows that there are nine Windows PowerShell item cmdlets.</span></span>

```
PS> Get-Command -Noun Item

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Clear-Item                      Clear-Item [-Path] <String[]...
Cmdlet          Copy-Item                       Copy-Item [-Path] <String[]>...
Cmdlet          Get-Item                        Get-Item [-Path] <String[]> ...
Cmdlet          Invoke-Item                     Invoke-Item [-Path] <String[...
Cmdlet          Move-Item                       Move-Item [-Path] <String[]>...
Cmdlet          New-Item                        New-Item [-Path] <String[]> ...
Cmdlet          Remove-Item                     Remove-Item [-Path] <String[...
Cmdlet          Rename-Item                     Rename-Item [-Path] <String>...
Cmdlet          Set-Item                        Set-Item [-Path] <String[]> ...
```

## <a name="creating-new-items-new-item"></a><span data-ttu-id="ad72a-107">创建新项 (New-Item)</span><span class="sxs-lookup"><span data-stu-id="ad72a-107">Creating New Items (New-Item)</span></span>

<span data-ttu-id="ad72a-108">若要在文件系统中创建新项，请使用 **New-Item** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ad72a-108">To create a new item in the file system, use the **New-Item** cmdlet.</span></span> <span data-ttu-id="ad72a-109">包含带有项的路径的 **Path** 参数，以及值为“file”或“directory”的 **ItemType** 参数。</span><span class="sxs-lookup"><span data-stu-id="ad72a-109">Include the **Path** parameter with path to the item, and the **ItemType** parameter with a value of "file" or "directory".</span></span>

<span data-ttu-id="ad72a-110">例如，若要在 C:\\Temp 目录中创建名为“New.Directory”的新目录，请键入：</span><span class="sxs-lookup"><span data-stu-id="ad72a-110">For example, to create a new directory named "New.Directory"in the C:\\Temp directory,  type:</span></span>

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

<span data-ttu-id="ad72a-111">若要创建文件，请将 **ItemType** 参数的值更改为“file”。</span><span class="sxs-lookup"><span data-stu-id="ad72a-111">To create a file, change the value of the **ItemType** parameter to "file".</span></span> <span data-ttu-id="ad72a-112">例如，若要在 New.Directory 目录中创建名为“file1.txt”的文件，请键入：</span><span class="sxs-lookup"><span data-stu-id="ad72a-112">For example, to create a file named "file1.txt" in the New.Directory directory, type:</span></span>

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

<span data-ttu-id="ad72a-113">可以使用相同技术创建新的注册表项。</span><span class="sxs-lookup"><span data-stu-id="ad72a-113">You can use the same technique to create a new registry key.</span></span> <span data-ttu-id="ad72a-114">事实上，注册表项更容易创建，因为 Windows 注册表中的唯一项类型就是注册表项。</span><span class="sxs-lookup"><span data-stu-id="ad72a-114">In fact, a registry key is easier to create because the only item type in the Windows registry is a key.</span></span> <span data-ttu-id="ad72a-115">（注册表条目是项*属性*。）例如，若要在 CurrentVersion 子项中创建名为“_Test”的项，请键入：</span><span class="sxs-lookup"><span data-stu-id="ad72a-115">(Registry entries are item *properties*.) For example, to create a key named "_Test" in the CurrentVersion subkey, type:</span></span>

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

<span data-ttu-id="ad72a-116">在键入注册表路径时，请确保在 Windows PowerShell 驱动器名称中包含冒号 (**:**)，如 HKLM: 和 HKCU:。</span><span class="sxs-lookup"><span data-stu-id="ad72a-116">When typing a registry path, be sure to include the colon (**:**) in the Windows PowerShell drive names, HKLM: and HKCU:.</span></span> <span data-ttu-id="ad72a-117">如果不带冒号，则 Windows PowerShell 无法识别路径中的驱动器名称。</span><span class="sxs-lookup"><span data-stu-id="ad72a-117">Without the colon, Windows PowerShell does not recognize the drive name in the path.</span></span>

## <a name="why-registry-values-are-not-items"></a><span data-ttu-id="ad72a-118">为什么注册表值不是项</span><span class="sxs-lookup"><span data-stu-id="ad72a-118">Why Registry Values are not Items</span></span>

<span data-ttu-id="ad72a-119">当你使用 **Get-ChildItem** cmdlet 查找注册表项中的项时，你将永远不会看到实际的注册表条目或其值。</span><span class="sxs-lookup"><span data-stu-id="ad72a-119">When you use the **Get-ChildItem** cmdlet to find the items in a registry key, you will never see actual registry entries or their values.</span></span>

<span data-ttu-id="ad72a-120">例如，注册表项 **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** 通常包含若干注册表条目，用于表示在系统启动时运行的应用程序。</span><span class="sxs-lookup"><span data-stu-id="ad72a-120">For example, the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** usually contains several registry entries that represent applications that run when the system starts.</span></span>

<span data-ttu-id="ad72a-121">但是，当你使用 **Get-ChildItem** 查找注册表项中的子项时，你只会看到注册表项的 **OptionalComponents** 子项：</span><span class="sxs-lookup"><span data-stu-id="ad72a-121">However, when you use **Get-ChildItem** to look for child items in the key, all you will see is the **OptionalComponents** subkey of the key:</span></span>

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

<span data-ttu-id="ad72a-122">尽管将注册表条目视为项会很方便，但无法确保指定的注册表条目路径是唯一的。</span><span class="sxs-lookup"><span data-stu-id="ad72a-122">Although it would be convenient to treat registry entries as items, you cannot specify a path to a registry entry in a way that ensures that it is unique.</span></span> <span data-ttu-id="ad72a-123">路径表示法不区分名为 **Run** 的注册表子项和 **Run** 子项中的 **(Default)** 注册表条目。</span><span class="sxs-lookup"><span data-stu-id="ad72a-123">The path notation does not distinguish between the registry subkey named **Run** and the **(Default)** registry entry in the **Run** subkey.</span></span> <span data-ttu-id="ad72a-124">此外，由于注册表条目名称可以包含反斜杠字符 (\\)，因此如果注册表条目是项，则无法使用路径表示法区分名为 Windows\\CurrentVersion\\Run 的注册表条目和此路径中的子项。</span><span class="sxs-lookup"><span data-stu-id="ad72a-124">Furthermore, because registry entry names can contain the backslash character (**\\**), if registry entries were items, then you could not use the path notation to distinguish a registry entry named **Windows\\CurrentVersion\\Run** from the subkey that is located in that path.</span></span>

## <a name="renaming-existing-items-rename-item"></a><span data-ttu-id="ad72a-125">重命名现有项 (Rename-Item)</span><span class="sxs-lookup"><span data-stu-id="ad72a-125">Renaming Existing Items (Rename-Item)</span></span>

<span data-ttu-id="ad72a-126">若要更改文件或文件夹的名称，请使用 **Rename-Item** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ad72a-126">To change the name of a file or folder, use the **Rename-Item** cmdlet.</span></span> <span data-ttu-id="ad72a-127">以下命令将 **file1.txt** 文件的名称更改为 **fileOne.txt**。</span><span class="sxs-lookup"><span data-stu-id="ad72a-127">The following command changes the name of the **file1.txt** file to **fileOne.txt**.</span></span>

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

<span data-ttu-id="ad72a-128">**Rename-Item** cmdlet 可以更改文件或文件夹的名称，但它不能移动项。</span><span class="sxs-lookup"><span data-stu-id="ad72a-128">The **Rename-Item** cmdlet can change the name of a file or a folder, but it cannot move an item.</span></span> <span data-ttu-id="ad72a-129">以下命令将失败，因为它尝试将文件从 New.Directory 目录移动到 Temp 目录。</span><span class="sxs-lookup"><span data-stu-id="ad72a-129">The following command fails because it attempts to move the file from the New.Directory directory to the Temp directory.</span></span>

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

## <a name="moving-items-move-item"></a><span data-ttu-id="ad72a-130">移动项 (Move-Item)</span><span class="sxs-lookup"><span data-stu-id="ad72a-130">Moving Items (Move-Item)</span></span>

<span data-ttu-id="ad72a-131">若要移动文件或文件夹，请使用 **Move-Item** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ad72a-131">To move a file or folder, use the **Move-Item** cmdlet.</span></span>

<span data-ttu-id="ad72a-132">例如，以下命令将 New.Directory 目录从 C:\\temp 目录移动到 C: 驱动器的根目录。</span><span class="sxs-lookup"><span data-stu-id="ad72a-132">For example, the following command moves the New.Directory directory from the C:\\temp directory to the root of the C: drive.</span></span> <span data-ttu-id="ad72a-133">若要验证该项是否已移动，请包含 **Move-Item** cmdlet 的 **PassThru** 参数。</span><span class="sxs-lookup"><span data-stu-id="ad72a-133">To verify that the item was moved, include the **PassThru** parameter of the **Move-Item** cmdlet.</span></span> <span data-ttu-id="ad72a-134">在没有 **Passthru** 的情况下，**Move-Item** cmdlet 不显示任何结果。</span><span class="sxs-lookup"><span data-stu-id="ad72a-134">Without **Passthru**, the **Move-Item** cmdlet does not display any results.</span></span>

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

## <a name="copying-items-copy-item"></a><span data-ttu-id="ad72a-135">复制项 (Copy-Item)</span><span class="sxs-lookup"><span data-stu-id="ad72a-135">Copying Items (Copy-Item)</span></span>

<span data-ttu-id="ad72a-136">如果你熟悉其他 shell 中的复制操作，你可能会发现 Windows PowerShell 中的 **Copy-Item** cmdlet 行为不正常。</span><span class="sxs-lookup"><span data-stu-id="ad72a-136">If you are familiar with the copy operations in other shells, you might find the behavior of the **Copy-Item** cmdlet in Windows PowerShell to be unusual.</span></span> <span data-ttu-id="ad72a-137">当你将项从一个位置复制到另一个位置时，默认情况下 Copy-Item 不会复制其内容。</span><span class="sxs-lookup"><span data-stu-id="ad72a-137">When you copy an item from one location to another, Copy-Item does not copy its contents by default.</span></span>

<span data-ttu-id="ad72a-138">例如，如果将 **New.Directory** 目录从 C: 驱动器复制到 C:\\temp 目录，命令会成功运行，但不会复制 New.Directory 目录中的文件。</span><span class="sxs-lookup"><span data-stu-id="ad72a-138">For example, if you copy the **New.Directory** directory from the C: drive to the C:\\temp directory, the command succeeds, but the files in the New.Directory directory are not copied.</span></span>

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

<span data-ttu-id="ad72a-139">如果显示 **C:\\temp\\New.Directory** 的内容，你将发现它未包含任何文件：</span><span class="sxs-lookup"><span data-stu-id="ad72a-139">If you display the contents of **C:\\temp\\New.Directory**, you will find that it contains no files:</span></span>

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

<span data-ttu-id="ad72a-140">为什么 **Copy-Item** cmdlet 不将内容复制到新位置？</span><span class="sxs-lookup"><span data-stu-id="ad72a-140">Why doesn't the **Copy-Item** cmdlet copy the contents to the new location?</span></span>

<span data-ttu-id="ad72a-141">**Copy-Item** cmdlet 的设计目标是通用；它不再仅仅用于复制文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="ad72a-141">The **Copy-Item** cmdlet was designed to be generic; it is not just for copying files and folders.</span></span> <span data-ttu-id="ad72a-142">此外，即使在复制文件和文件夹时，你也可能只想要复制容器，而不是复制其中的项。</span><span class="sxs-lookup"><span data-stu-id="ad72a-142">Also, even when copying files and folders, you might want to copy only the container and not the items within it.</span></span>

<span data-ttu-id="ad72a-143">若要复制文件夹中的所有内容，请在命令中包含 **Copy-Item** cmdlet 的 **Recurse** 参数。</span><span class="sxs-lookup"><span data-stu-id="ad72a-143">To copy all of the contents of a folder, include the **Recurse** parameter of the **Copy-Item** cmdlet in the command.</span></span> <span data-ttu-id="ad72a-144">如果你已复制目录，而未复制其内容，则可添加 **Force** 参数，该参数允许你覆盖空文件夹。</span><span class="sxs-lookup"><span data-stu-id="ad72a-144">If you have already copied the directory without its contents, add the **Force** parameter, which allows you to overwrite the empty folder.</span></span>

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp -Recurse -Force -Passthru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18   1:53 PM            New.Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

## <a name="deleting-items-remove-item"></a><span data-ttu-id="ad72a-145">删除项 (Remove-Item)</span><span class="sxs-lookup"><span data-stu-id="ad72a-145">Deleting Items (Remove-Item)</span></span>

<span data-ttu-id="ad72a-146">若要删除文件和文件夹，请使用 **Remove-Item** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ad72a-146">To delete files and folders, use the **Remove-Item** cmdlet.</span></span> <span data-ttu-id="ad72a-147">可进行重要且不可逆更改的 Windows PowerShell cmdlet（例如 **Remove-Item**）在你输入其命令时通常将提示你进行确认。</span><span class="sxs-lookup"><span data-stu-id="ad72a-147">Windows PowerShell cmdlets, such as **Remove-Item**, that can make significant, irreversible changes will often prompt for confirmation when you enter its commands.</span></span> <span data-ttu-id="ad72a-148">例如，如果你尝试删除 **New.Directory** 文件夹，系统将提示你确认命令，因为该文件夹中包含文件：</span><span class="sxs-lookup"><span data-stu-id="ad72a-148">For example, if you try to remove the **New.Directory** folder, you will be prompted to confirm the command, because the folder contains files:</span></span>

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="ad72a-149">由于“是”是默认响应，因此若要删除文件夹及其文件，请按“Enter”键。</span><span class="sxs-lookup"><span data-stu-id="ad72a-149">Because **Yes** is the default response, to delete the folder and its files, press the **Enter** key.</span></span> <span data-ttu-id="ad72a-150">若要删除文件夹而不进行确认，请使用 **-Recurse**参数。</span><span class="sxs-lookup"><span data-stu-id="ad72a-150">To remove the folder without confirming, use the **-Recurse** parameter.</span></span>

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

## <a name="executing-items-invoke-item"></a><span data-ttu-id="ad72a-151">执行项 (Invoke-Item)</span><span class="sxs-lookup"><span data-stu-id="ad72a-151">Executing Items (Invoke-Item)</span></span>

<span data-ttu-id="ad72a-152">Windows PowerShell 使用 **Invoke-Item** cmdlet 针对文件或文件夹执行默认操作。</span><span class="sxs-lookup"><span data-stu-id="ad72a-152">Windows PowerShell uses the **Invoke-Item** cmdlet to perform a default action for a file or folder.</span></span> <span data-ttu-id="ad72a-153">此默认操作由注册表中的默认应用程序处理程序确定；效果与在文件资源管理器中双击该项的效果相同。</span><span class="sxs-lookup"><span data-stu-id="ad72a-153">This default action is determined by the default application handler in the registry; the effect is the same as if you double-click the item in File Explorer.</span></span>

<span data-ttu-id="ad72a-154">例如，假设你要运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ad72a-154">For example, suppose you run the following command:</span></span>

```powershell
Invoke-Item C:\WINDOWS
```

<span data-ttu-id="ad72a-155">位于 C:\\Windows 中的“资源管理器”窗口将会出现，正如你双击 C:\\Windows 文件夹一样。</span><span class="sxs-lookup"><span data-stu-id="ad72a-155">An Explorer window that is located in C:\\Windows appears, just as if you had double-clicked the C:\\Windows folder.</span></span>

<span data-ttu-id="ad72a-156">如果在 Windows Vista 之前的系统上调用 **Boot.ini** 文件：</span><span class="sxs-lookup"><span data-stu-id="ad72a-156">If you invoke the **Boot.ini** file on a system prior to Windows Vista:</span></span>

```powershell
Invoke-Item C:\boot.ini
```

<span data-ttu-id="ad72a-157">如果 .ini 文件类型与记事本相关联，则 boot.ini 文件将在记事本中打开。</span><span class="sxs-lookup"><span data-stu-id="ad72a-157">If the .ini file type is associated with Notepad, the boot.ini file opens in Notepad.</span></span>
