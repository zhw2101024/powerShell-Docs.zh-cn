---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "使用文件和文件夹"
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
ms.openlocfilehash: 73773df9f018c396c9c4237a40f2e9d2c841464e
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/03/2017
---
# <a name="working-with-files-and-folders"></a><span data-ttu-id="ddc48-103">使用文件和文件夹</span><span class="sxs-lookup"><span data-stu-id="ddc48-103">Working with Files and Folders</span></span>
<span data-ttu-id="ddc48-104">在 Windows PowerShell 驱动器中导航和操作其上面的项类似于操作 Windows 物理磁盘驱动器上的文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="ddc48-104">Navigating through Windows PowerShell drives and manipulating the items on them is similar to manipulating files and folders on Windows physical disk drives.</span></span> <span data-ttu-id="ddc48-105">本节我们将讨论如何处理特定文件和文件夹操作任务。</span><span class="sxs-lookup"><span data-stu-id="ddc48-105">We will discuss how to deal with specific file and folder manipulation tasks in this section.</span></span>

### <a name="listing-all-the-files-and-folders-within-a-folder"></a><span data-ttu-id="ddc48-106">列出某个文件夹内的所有文件和文件夹</span><span class="sxs-lookup"><span data-stu-id="ddc48-106">Listing All the Files and Folders Within a Folder</span></span>
<span data-ttu-id="ddc48-107">可以通过使用 **Get-ChildItem** 直接获取某个文件夹中的所有项目。</span><span class="sxs-lookup"><span data-stu-id="ddc48-107">You can get all items directly within a folder by using **Get-ChildItem**.</span></span> <span data-ttu-id="ddc48-108">添加可选的 **Force** 参数以显示隐藏项或系统项。</span><span class="sxs-lookup"><span data-stu-id="ddc48-108">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="ddc48-109">例如，此命令将显示 Windows PowerShell 驱动器 C（它与 Windows 物理驱动器 C 相同）的直观内容：</span><span class="sxs-lookup"><span data-stu-id="ddc48-109">For example, this command displays the direct contents of Windows PowerShell Drive C (which is the same as the Windows physical drive C):</span></span>

```
Get-ChildItem -Force C:\
```

<span data-ttu-id="ddc48-110">该命令将仅列出直接包含的项，类似于使用 Cmd.exe 的 **DIR** 命令或 UNIX shell 中的 **ls**。</span><span class="sxs-lookup"><span data-stu-id="ddc48-110">The command lists only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="ddc48-111">为了显示包含的项，你还需要指定 **-Recurse** 参数。</span><span class="sxs-lookup"><span data-stu-id="ddc48-111">In order to show contained items, you need to specify the **-Recurse** parameter as well.</span></span> <span data-ttu-id="ddc48-112">（这可能需要相当长的时间才能完成。）列出 C 驱动器上的所有内容：</span><span class="sxs-lookup"><span data-stu-id="ddc48-112">(This can take an extremely long time to complete.) To list everything on the C drive:</span></span>

```
Get-ChildItem -Force C:\ -Recurse
```

<span data-ttu-id="ddc48-113">**Get-ChildItem** 可以使用其 **Path**、**Filter**、**Include** 和 **Exclude** 参数筛选项，但那些通常只基于名称。</span><span class="sxs-lookup"><span data-stu-id="ddc48-113">**Get-ChildItem** can filter items with its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those are typically based only on name.</span></span> <span data-ttu-id="ddc48-114">还可以通过使用 **Where-Object** 基于项的其他属性执行复杂的筛选。</span><span class="sxs-lookup"><span data-stu-id="ddc48-114">You can perform complex filtering based on other properties of items by using **Where-Object**.</span></span>

<span data-ttu-id="ddc48-115">下面的命令用于查找上次于 2005 年 10 月 1 日之后修改，并且不小于 1 兆字节，也不大于 10 兆字节的 Program Files 文件夹中的所有可执行文件：</span><span class="sxs-lookup"><span data-stu-id="ddc48-115">The following command finds all executables within the Program Files folder that were last modified after October 1, 2005 and which are neither smaller than 1 megabyte nor larger than 10 megabytes:</span></span>

```
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt "2005-10-01") -and ($_.Length -ge 1m) -and ($_.Length -le 10m)}
```

### <a name="copying-files-and-folders"></a><span data-ttu-id="ddc48-116">复制文件和文件夹</span><span class="sxs-lookup"><span data-stu-id="ddc48-116">Copying Files and Folders</span></span>
<span data-ttu-id="ddc48-117">复制通过 **Copy-Item** 完成。</span><span class="sxs-lookup"><span data-stu-id="ddc48-117">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="ddc48-118">以下命令用于将 C:\\boot.ini 备份到 C:\\boot.bak：</span><span class="sxs-lookup"><span data-stu-id="ddc48-118">The following command backs up C:\\boot.ini to C:\\boot.bak:</span></span>

```
Copy-Item -Path c:\boot.ini -Destination c:\boot.bak
```

<span data-ttu-id="ddc48-119">如果目标文件已存在，则复制尝试失败。</span><span class="sxs-lookup"><span data-stu-id="ddc48-119">If the destination file already exists, the copy attempt fails.</span></span> <span data-ttu-id="ddc48-120">若要覆盖预先存在的目标，请使用 Force 参数：</span><span class="sxs-lookup"><span data-stu-id="ddc48-120">To overwrite a pre-existing destination, use the Force parameter:</span></span>

```
Copy-Item -Path c:\boot.ini -Destination c:\boot.bak -Force
```

<span data-ttu-id="ddc48-121">即使当目标为只读时，该命令也有效。</span><span class="sxs-lookup"><span data-stu-id="ddc48-121">This command works even when the destination is read-only.</span></span>

<span data-ttu-id="ddc48-122">复制文件夹的操作方式与此相同。</span><span class="sxs-lookup"><span data-stu-id="ddc48-122">Folder copying works the same way.</span></span> <span data-ttu-id="ddc48-123">此命令用于以递归方式将文件夹 C:\\temp\\test1 复制到新文件夹 c:\\temp\\DeleteMe：</span><span class="sxs-lookup"><span data-stu-id="ddc48-123">This command copies the folder C:\\temp\\test1 to the new folder c:\\temp\\DeleteMe recursively:</span></span>

```
Copy-Item C:\temp\test1 -Recurse c:\temp\DeleteMe
```

<span data-ttu-id="ddc48-124">还可以复制选定的项。</span><span class="sxs-lookup"><span data-stu-id="ddc48-124">You can also copy a selection of items.</span></span> <span data-ttu-id="ddc48-125">以下命令用于将 c:\\data 中任意位置包含的所有 .txt 文件复制到 c:\\temp\\text：</span><span class="sxs-lookup"><span data-stu-id="ddc48-125">The following command copies all .txt files contained anywhere in c:\\data to c:\\temp\\text:</span></span>

```
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination c:\temp\text
```

<span data-ttu-id="ddc48-126">你仍然可以使用其他工具执行文件系统复制。</span><span class="sxs-lookup"><span data-stu-id="ddc48-126">You can still use other tools to perform file system copies.</span></span> <span data-ttu-id="ddc48-127">XCOPY、ROBOCOPY 和 COM 对象（如 **Scripting.FileSystemObject**）都适用于 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ddc48-127">XCOPY, ROBOCOPY, and COM objects, such as the **Scripting.FileSystemObject,** all work in Windows PowerShell.</span></span> <span data-ttu-id="ddc48-128">例如，可以使用 Windows Script Host **Scripting.FileSystem COM** 类将 C:\\boot.ini 备份到 C:\\boot.bak：</span><span class="sxs-lookup"><span data-stu-id="ddc48-128">For example, you can use the Windows Script Host **Scripting.FileSystem COM** class to back up C:\\boot.ini to C:\\boot.bak:</span></span>

```
(New-Object -ComObject Scripting.FileSystemObject).CopyFile("c:\boot.ini", "c:\boot.bak")
```

### <a name="creating-files-and-folders"></a><span data-ttu-id="ddc48-129">创建文件和文件夹</span><span class="sxs-lookup"><span data-stu-id="ddc48-129">Creating Files and Folders</span></span>
<span data-ttu-id="ddc48-130">创建新项的操作方式在所有 Windows PowerShell 提供程序上都相同。</span><span class="sxs-lookup"><span data-stu-id="ddc48-130">Creating new items works the same on all Windows PowerShell providers.</span></span> <span data-ttu-id="ddc48-131">如果某个 Windows PowerShell 提供程序具有多个类型的项（例如，用于区分目录和文件的 FileSystem Windows PowerShell 提供程序），则需要指定项类型。</span><span class="sxs-lookup"><span data-stu-id="ddc48-131">If a Windows PowerShell provider has more than one type of item—for example, the FileSystem Windows PowerShell provider distinguishes between directories and files—you need to specify the item type.</span></span>

<span data-ttu-id="ddc48-132">以下命令可创建一个新文件夹 C:\\temp\\New Folder：</span><span class="sxs-lookup"><span data-stu-id="ddc48-132">This command creates a new folder C:\\temp\\New Folder:</span></span>

```
New-Item -Path 'C:\temp\New Folder' -ItemType "directory"
```

<span data-ttu-id="ddc48-133">以下命令可创建新的空文件 C:\\temp\\New Folder\\file.txt</span><span class="sxs-lookup"><span data-stu-id="ddc48-133">This command creates a new empty file C:\\temp\\New Folder\\file.txt</span></span>

```
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType "file"
```

### <a name="removing-all-files-and-folders-within-a-folder"></a><span data-ttu-id="ddc48-134">删除某个文件夹内的所有文件和文件夹</span><span class="sxs-lookup"><span data-stu-id="ddc48-134">Removing All Files and Folders Within a Folder</span></span>
<span data-ttu-id="ddc48-135">你可以使用 **Remove-Item** 删除包含的项，但如果项包含任何其他内容，系统将提示你确认该删除。</span><span class="sxs-lookup"><span data-stu-id="ddc48-135">You can remove contained items using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="ddc48-136">例如，如果尝试删除包含其他项的文件夹 C:\\temp\\DeleteMe，则在删除该文件夹之前 Windows PowerShell 会提示你确认：</span><span class="sxs-lookup"><span data-stu-id="ddc48-136">For example, if you attempt to delete the folder C:\\temp\\DeleteMe that contains other items, Windows PowerShell prompts you for confirmation before deleting the folder:</span></span>

```
Remove-Item C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="ddc48-137">如果不希望系统针对每个包含的项都提示你，则指定 **Recurse** 参数：</span><span class="sxs-lookup"><span data-stu-id="ddc48-137">If you do not want to be prompted for each contained item, specify the **Recurse** parameter:</span></span>

```
Remove-Item C:\temp\DeleteMe -Recurse
```

### <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a><span data-ttu-id="ddc48-138">将本地文件夹映射为 Windows 可访问驱动器</span><span class="sxs-lookup"><span data-stu-id="ddc48-138">Mapping a Local Folder as a Windows Accessible Drive</span></span>
<span data-ttu-id="ddc48-139">你还可以使用 **subst** 命令映射本地文件夹。</span><span class="sxs-lookup"><span data-stu-id="ddc48-139">You can also map a local folder, using the **subst** command.</span></span> <span data-ttu-id="ddc48-140">以下命令可在根路径为本地 Program Files 的目录中创建本地驱动器 P:：</span><span class="sxs-lookup"><span data-stu-id="ddc48-140">The following command creates a local drive P: rooted in the local Program Files directory:</span></span>

```
subst p: $env:programfiles
```

<span data-ttu-id="ddc48-141">正如网络驱动器一样，使用 **subst** 在 Windows PowerShell 内映射的驱动器将对 Windows PowerShell shell 立即可见。</span><span class="sxs-lookup"><span data-stu-id="ddc48-141">Just as with network drives, drives mapped within Windows PowerShell using **subst** are immediately visible to the Windows PowerShell shell.</span></span>

### <a name="reading-a-text-file-into-an-array"></a><span data-ttu-id="ddc48-142">将文本文件数据读取到数组中</span><span class="sxs-lookup"><span data-stu-id="ddc48-142">Reading a Text File into an Array</span></span>
<span data-ttu-id="ddc48-143">文本数据更常见的存储格式之一是采用文件形式，其中单独的行被视为不同的数据元素。</span><span class="sxs-lookup"><span data-stu-id="ddc48-143">One of the more common storage formats for text data is in a file with separate lines treated as distinct data elements.</span></span> <span data-ttu-id="ddc48-144">**Get-Content** cmdlet 可用于一步读取整个文件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ddc48-144">The **Get-Content** cmdlet can be used to read an entire file in one step, as shown here:</span></span>

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional 
with Data Execution Prevention" /noexecute=optin /fastdetect
```

<span data-ttu-id="ddc48-145">**Get-Content** 已将从文件读取的数据视为数组，其中每行文件内容视为一个元素。</span><span class="sxs-lookup"><span data-stu-id="ddc48-145">**Get-Content** already treats the data read from the file as an array, with one element per line of file content.</span></span> <span data-ttu-id="ddc48-146">可以通过检查返回的内容的**长度**来确认此点：</span><span class="sxs-lookup"><span data-stu-id="ddc48-146">You can confirm this by checking the **Length** of the returned content:</span></span>

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

<span data-ttu-id="ddc48-147">此命令对于直接从 Windows PowerShell 获取列表信息最为有用。</span><span class="sxs-lookup"><span data-stu-id="ddc48-147">This command is most useful for getting lists of information into Windows PowerShell directly.</span></span> <span data-ttu-id="ddc48-148">例如，你可能会在文件 C:\\temp\\domainMembers.txt 中存储计算机名称或 IP 地址的列表，其中文件的每一行上一个名称。</span><span class="sxs-lookup"><span data-stu-id="ddc48-148">For example, you might store a list of computer names or IP addresses in a file C:\\temp\\domainMembers.txt, with one name on each line of the file.</span></span> <span data-ttu-id="ddc48-149">你可以使用 **Get-Content** 来检索文件内容并将它们放在变量 **$Computers** 中：</span><span class="sxs-lookup"><span data-stu-id="ddc48-149">You can use **Get-Content** to retrieve the file contents and put them in the variable **$Computers**:</span></span>

```
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

<span data-ttu-id="ddc48-150">**$Computers** 现在是一个数组，其中每个元素包含一个计算机名。</span><span class="sxs-lookup"><span data-stu-id="ddc48-150">**$Computers** is now an array containing a computer name in each element.</span></span>

