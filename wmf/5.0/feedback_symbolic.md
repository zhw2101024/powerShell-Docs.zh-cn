---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 82451c550014c684958aaf0f324457db8f0d8ceb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="interact-with-symbolic-links-using-improved-item-cmdlets"></a><span data-ttu-id="b98a5-102">使用改进的 Item cmdlet 与符号链接交互</span><span class="sxs-lookup"><span data-stu-id="b98a5-102">Interact with Symbolic links using improved Item cmdlets</span></span>

<span data-ttu-id="b98a5-103">为支持符号链接，扩展了 **\*-Item** 和几个相关 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b98a5-103">To support symbolic links, **\*-Item** and a few related cmdlets have been extended.</span></span> <span data-ttu-id="b98a5-104">现可使用 **New-Item** 在简单的单行中创建符号链接。</span><span class="sxs-lookup"><span data-stu-id="b98a5-104">Now you can create symbolic links in a single, simple line with **New-Item**.</span></span> <span data-ttu-id="b98a5-105">你将注意到，Item 相关的 cmdlet（**Remove-Item、Get-ChildItem**）的行为与以前非常相似。</span><span class="sxs-lookup"><span data-stu-id="b98a5-105">You’ll notice that the Item-related cmdlets (**Remove-Item, Get-ChildItem**) behave very similarly to before.</span></span>

<span data-ttu-id="b98a5-106">以下为新功能的一些用例：</span><span class="sxs-lookup"><span data-stu-id="b98a5-106">The following shows some use cases of the new capabilities:</span></span>

## <a name="new-item"></a><span data-ttu-id="b98a5-107">NEW-ITEM</span><span class="sxs-lookup"><span data-stu-id="b98a5-107">NEW-ITEM</span></span>

### <a name="symbolic-link-files"></a><span data-ttu-id="b98a5-108">符号链接文件</span><span class="sxs-lookup"><span data-stu-id="b98a5-108">SYMBOLIC LINK FILES</span></span>

```powershell
# Create a new symbolic link file named MySymLinkFile.txt in C:\Temp which links to $pshome\profile.ps1
cd C:\Temp
New-Item -ItemType SymbolicLink -Name MySymLinkFile.txt -Target $pshome\profile.ps1

# Target is an alias to the Value parameter
# All 3 commands below are equivalent to above
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkFile.txt -Value $pshome\profile.ps1
```

### <a name="symbolic-link-directories"></a><span data-ttu-id="b98a5-109">符号链接目录</span><span class="sxs-lookup"><span data-stu-id="b98a5-109">SYMBOLIC LINK DIRECTORIES</span></span>

```powershell
# Create a new symbolic link directory named MySymLinkDir in C:\Temp which links to the $pshome folder
# ItemType is the same for files and directories - autodetect based on specified target
cd C:\Temp
New-Item -ItemType SymbolicLink -Name MySymLinkDir -Target $pshome

# Target is an alias to the Value parameter
# Similar to above, any combination of Path and Name also works
New-Item -ItemType SymbolicLink -Path C:\Temp -Name MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Path C:\Temp\MySymLinkDir -Value $pshome
New-Item -ItemType SymbolicLink -Name C:\Temp\MySymLinkDir -Value $pshome
```

### <a name="hard-links"></a><span data-ttu-id="b98a5-110">硬链接</span><span class="sxs-lookup"><span data-stu-id="b98a5-110">HARD LINKS</span></span>

```powershell
New-Item -ItemType HardLink -Path C:\Temp -Name MyHardLinkFile.txt -Value $pshome\profile.ps1
# Same combinations of Path and Name allowed as described above
```

### <a name="directory-junctions"></a><span data-ttu-id="b98a5-111">目录联接</span><span class="sxs-lookup"><span data-stu-id="b98a5-111">DIRECTORY JUNCTIONS</span></span>

```powershell
New-Item -ItemType Junction -Path C:\Temp\MyJunctionDir -Value $pshome
# Same combinations of Path and Name allowed as described above
```

## <a name="get-childitem"></a><span data-ttu-id="b98a5-112">GET-CHILDITEM</span><span class="sxs-lookup"><span data-stu-id="b98a5-112">GET-CHILDITEM</span></span>

```powershell
# Append link type column to Mode property and display with Get-ChildItem
# Use 'l' for all link types
# Increase the width of the Length column by 4 (from 10 to 14)
Get-ChildItem C:\Temp | sort LastWriteTime -Descending

Directory: C:\Temp

Mode LastWriteTime Length Name
---- ------------- ------ ----
-a---- 6/13/2014 3:00 PM 16 File.txt
-a---- 6/13/2014 3:00 PM 98956046499840 My90TB.vhd
d----- 6/13/2014 3:00 PM Directory
-a---l 6/13/2014 3:21 PM 0 MySymLinkFile.txt
d----l 6/13/2014 3:22 PM MySymLinkDir
-a---l 6/13/2014 3:23 PM 23304 MyHardLinkFile.txt
d----l 6/13/2014 3:24 PM MyJunctionDir

# New Target property works with any link type
# Not displayed in the default table view, but displayed in the default list view

# New LinkType property with values: SymbolicLink
Get-ChildItem C:\Temp\MySymLinkFile.txt | Format-List

Directory: C:\Temp

Name : MySymLinkFile.txt
Length : 0
Mode : -a---l
LinkType : SymbolicLink
Target : C:\Windows\System32\WindowsPowerShell\v1.0\profile.ps1
CreationTime : 6/16/2014 3:21:01 PM
LastWriteTime : 6/16/2014 3:21:01 PM
LastAccessTime : 6/16/2014 3:21:01 PM
VersionInfo : File: C:\Temp\MySymLinkFile.txt
InternalName:
OriginalFilename:
FileVersion:
FileDescription:
Product:
ProductVersion:
Debug: False
Patched: False
PreRelease: False
PrivateBuild: False
SpecialBuild: False
Language:
```

## <a name="remove-item"></a><span data-ttu-id="b98a5-113">REMOVE-ITEM</span><span class="sxs-lookup"><span data-stu-id="b98a5-113">REMOVE-ITEM</span></span>

```powershell
# Works like any other item type
# Removes MySymLinkFile.txt
Remove-Item C:\Temp\MySymLinkFile.txt

# Returns an error as this is a reparse point.
Remove-Item C:\Temp\MySymLinkDir

# Removes the files in the target directory and MySymLinkDir
Remove-Item C:\Temp\MySymLinkDir -Force
```
