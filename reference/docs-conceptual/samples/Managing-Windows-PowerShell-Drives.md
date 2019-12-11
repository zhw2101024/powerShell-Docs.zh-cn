---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 管理 Windows PowerShell 驱动器
ms.openlocfilehash: 5d1aba459caeaab2542e17e74534da6713b0faa9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "70215507"
---
# <a name="managing-windows-powershell-drives"></a><span data-ttu-id="5b228-103">管理 Windows PowerShell 驱动器</span><span class="sxs-lookup"><span data-stu-id="5b228-103">Managing Windows PowerShell Drives</span></span>

<span data-ttu-id="5b228-104">*Windows PowerShell 驱动器*是一个数据存储位置，你可以像访问 Windows PowerShell 中的文件系统驱动器那样访问它。</span><span class="sxs-lookup"><span data-stu-id="5b228-104">A *Windows PowerShell drive* is a data store location that you can access like a file system drive in Windows PowerShell.</span></span> <span data-ttu-id="5b228-105">Windows PowerShell 提供程序将为你创建一些驱动器，例如文件系统驱动器（包括 C: 和 D:）、注册表驱动器（HKCU: 和 HKLM:）和证书驱动器 (Cert:)，你也可以创建自己的 Windows PowerShell 驱动器。</span><span class="sxs-lookup"><span data-stu-id="5b228-105">The Windows PowerShell providers create some drives for you, such as the file system drives (including C: and D:), the registry drives (HKCU: and HKLM:), and the certificate drive (Cert:), and you can create your own Windows PowerShell drives.</span></span> <span data-ttu-id="5b228-106">这些驱动器非常有用，但它们仅在 Windows PowerShell 内可用。</span><span class="sxs-lookup"><span data-stu-id="5b228-106">These drives are very useful, but they are available only within Windows PowerShell.</span></span> <span data-ttu-id="5b228-107">你无法通过使用其他 Windows 工具（如文件资源管理器或 Cmd.exe）访问它们。</span><span class="sxs-lookup"><span data-stu-id="5b228-107">You cannot access them by using other Windows tools, such as File Explorer or Cmd.exe.</span></span>

<span data-ttu-id="5b228-108">Windows PowerShell 可针对适用于 Windows PowerShell 驱动器的命令使用名词 **PSDrive**。</span><span class="sxs-lookup"><span data-stu-id="5b228-108">Windows PowerShell uses the noun, **PSDrive**, for commands that work with Windows PowerShell drives.</span></span> <span data-ttu-id="5b228-109">有关 Windows PowerShell 会话中的 Windows PowerShell 驱动器列表，请使用 **Get-PSDrive** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5b228-109">For a list of the Windows PowerShell drives in your Windows PowerShell session, use the **Get-PSDrive** cmdlet.</span></span>

```
PS> Get-PSDrive

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
Alias      Alias
C          FileSystem    C:\                                 ...And Settings\me
cert       Certificate   \
D          FileSystem    D:\
Env        Environment
Function   Function
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
Variable   Variable
```

<span data-ttu-id="5b228-110">尽管显示内容中的驱动器与你的系统上的驱动器有所不同，但是该列表将看起来类似于 **Get-PSDrive** 命令的输出（如上所示）。</span><span class="sxs-lookup"><span data-stu-id="5b228-110">Although the drives in the display vary with the drives on your system, the listing will look similar to the output of the **Get-PSDrive** command shown above.</span></span>

<span data-ttu-id="5b228-111">文件系统驱动器是 Windows PowerShell 驱动器的子集。</span><span class="sxs-lookup"><span data-stu-id="5b228-111">File system drives are a subset of the Windows PowerShell drives.</span></span> <span data-ttu-id="5b228-112">你可以通过 Provider 列中的 FileSystem 条目标识文件系统驱动器。</span><span class="sxs-lookup"><span data-stu-id="5b228-112">You can identify the file system drives by the FileSystem entry in the Provider column.</span></span> <span data-ttu-id="5b228-113">（Windows PowerShell 中的文件系统驱动器受 Windows PowerShell FileSystem 提供程序支持。）</span><span class="sxs-lookup"><span data-stu-id="5b228-113">(The file system drives in Windows PowerShell are supported by the Windows PowerShell FileSystem provider.)</span></span>

<span data-ttu-id="5b228-114">若要查看 **Get-PSDrive** cmdlet 的语法，请使用 **Syntax** 参数键入 **Get-Command** 命令：</span><span class="sxs-lookup"><span data-stu-id="5b228-114">To see the syntax of the **Get-PSDrive** cmdlet, type a **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

<span data-ttu-id="5b228-115">**PSProvider** 参数允许你仅显示受特定提供程序支持的 Windows PowerShell 驱动器。</span><span class="sxs-lookup"><span data-stu-id="5b228-115">The **PSProvider** parameter lets you display only the Windows PowerShell drives that are supported by a particular provider.</span></span> <span data-ttu-id="5b228-116">例如，若要仅显示受 Windows PowerShell FileSystem 提供程序支持的 Windows PowerShell 驱动器，请使用 **PSProvider** 参数和 **FileSystem** 值键入 **Get-PSDrive** 命令：</span><span class="sxs-lookup"><span data-stu-id="5b228-116">For example, to display only the Windows PowerShell drives that are supported by the Windows PowerShell FileSystem provider, type a **Get-PSDrive** command with the **PSProvider** parameter and the **FileSystem** value:</span></span>

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

<span data-ttu-id="5b228-117">若要查看表示注册表配置单元的 Windows PowerShell 驱动器，请使用 **PSProvider** 参数来仅显示受 Windows PowerShell Registry 提供程序支持的 Windows PowerShell 驱动器：</span><span class="sxs-lookup"><span data-stu-id="5b228-117">To view the Windows PowerShell drives that represent registry hives, use the **PSProvider** parameter to display only the Windows PowerShell drives that are supported by the Windows PowerShell Registry provider:</span></span>

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

<span data-ttu-id="5b228-118">你还可以将标准 Location cmdlet 与 Windows PowerShell 驱动器结合使用：</span><span class="sxs-lookup"><span data-stu-id="5b228-118">You can also use the standard Location cmdlets with the Windows PowerShell drives:</span></span>

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a><span data-ttu-id="5b228-119">添加新的 Windows PowerShell 驱动器 (New-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="5b228-119">Adding New Windows PowerShell Drives (New-PSDrive)</span></span>

<span data-ttu-id="5b228-120">你可以通过使用 **New-PSDrive** 命令添加自己的 Windows PowerShell 驱动器。</span><span class="sxs-lookup"><span data-stu-id="5b228-120">You can add your own Windows PowerShell drives by using the **New-PSDrive** command.</span></span> <span data-ttu-id="5b228-121">若要获取 **New-PSDrive** 命令的语法，请使用 **Syntax** 参数输入 **Get-Command** 命令：</span><span class="sxs-lookup"><span data-stu-id="5b228-121">To get the syntax for the **New-PSDrive** command, enter the **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

<span data-ttu-id="5b228-122">若要创建一个新的 Windows PowerShell 驱动器，你必须提供三个参数：</span><span class="sxs-lookup"><span data-stu-id="5b228-122">To create a new Windows PowerShell drive, you must supply three parameters:</span></span>

- <span data-ttu-id="5b228-123">驱动器的名称（可使用任何有效的 Windows PowerShell 名称）</span><span class="sxs-lookup"><span data-stu-id="5b228-123">A name for the drive (you can use any valid Windows PowerShell name)</span></span>

- <span data-ttu-id="5b228-124">PSProvider（将“FileSystem”用于文件系统位置，将“Registry”用于注册表位置）</span><span class="sxs-lookup"><span data-stu-id="5b228-124">The PSProvider (use "FileSystem" for file system locations and "Registry" for registry locations)</span></span>

- <span data-ttu-id="5b228-125">根，即指向新驱动器的根目录的路径</span><span class="sxs-lookup"><span data-stu-id="5b228-125">The root, that is, the path to the root of the new drive</span></span>

<span data-ttu-id="5b228-126">例如，可以创建一个名为“Office”的驱动器，它将映射到包含你的计算机上的 Microsoft Office 应用程序的文件夹，例如 **C:\\Program Files\\Microsoft Office\\OFFICE11**。</span><span class="sxs-lookup"><span data-stu-id="5b228-126">For example, you can create a drive named "Office" that is mapped to the folder that contains the Microsoft Office applications on your computer, such as **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span></span> <span data-ttu-id="5b228-127">若要创建该驱动器，请键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="5b228-127">To create the drive, type the following command:</span></span>

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Microsoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> <span data-ttu-id="5b228-128">一般情况下，路径不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="5b228-128">In general, paths are not case-sensitive.</span></span>

<span data-ttu-id="5b228-129">在执行所有 Windows PowerShell 驱动器时，请参考新的 Windows PowerShell 驱动器，格式是在名称后面跟一个冒号 ( **:** )。</span><span class="sxs-lookup"><span data-stu-id="5b228-129">You refer to the new Windows PowerShell drive as you do all Windows PowerShell drives -- by its name followed by a colon (**:**).</span></span>

<span data-ttu-id="5b228-130">Windows PowerShell 驱动器可以使许多任务变得更简单。</span><span class="sxs-lookup"><span data-stu-id="5b228-130">A Windows PowerShell drive can make many tasks much simpler.</span></span> <span data-ttu-id="5b228-131">例如，Windows 注册表中的某些最重要的项的路径长度非常长，难以访问且难以记住这些路径。</span><span class="sxs-lookup"><span data-stu-id="5b228-131">For example, some of the most important keys in the Windows registry have extremely long paths, making them cumbersome to access and difficult to remember.</span></span> <span data-ttu-id="5b228-132">关键的配置信息位于 **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**。</span><span class="sxs-lookup"><span data-stu-id="5b228-132">Critical configuration information resides under **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span> <span data-ttu-id="5b228-133">若要查看和更改 CurrentVersion 注册表项中的项，你可以创建一个其根在该项中的 Windows PowerShell 驱动器，方法是键入：</span><span class="sxs-lookup"><span data-stu-id="5b228-133">To view and change items in the CurrentVersion registry key, you can create a Windows PowerShell drive that is rooted in that key by typing:</span></span>

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\Windows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

<span data-ttu-id="5b228-134">然后，你可以像对任何其他驱动器一样，将位置更改为 cvkey:  驱动器：</span><span class="sxs-lookup"><span data-stu-id="5b228-134">You can then change location to the **cvkey:** drive as you would any other drive:</span></span>

```
PS> cd cvkey:
```

<span data-ttu-id="5b228-135">或者：</span><span class="sxs-lookup"><span data-stu-id="5b228-135">or:</span></span>

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

<span data-ttu-id="5b228-136">New-PsDrive cmdlet 仅将新的驱动器添加到当前 Windows PowerShell 会话中。</span><span class="sxs-lookup"><span data-stu-id="5b228-136">The New-PsDrive cmdlet adds the new drive only to the current Windows PowerShell session.</span></span> <span data-ttu-id="5b228-137">如果关闭 Windows PowerShell 窗口，则会丢失新的驱动器。</span><span class="sxs-lookup"><span data-stu-id="5b228-137">If you close the Windows PowerShell window, the new drive is lost.</span></span> <span data-ttu-id="5b228-138">若要保存 Windows PowerShell 驱动器，请使用 Export-Console cmdlet 导出当前 Windows PowerShell 会话，然后使用 PowerShell.exe **PSConsoleFile** 参数来将其导入。</span><span class="sxs-lookup"><span data-stu-id="5b228-138">To save a Windows PowerShell drive, use the Export-Console cmdlet to export the current Windows PowerShell session, and then use the PowerShell.exe **PSConsoleFile** parameter to import it.</span></span> <span data-ttu-id="5b228-139">或者，将新的驱动器添加到 Windows PowerShell 配置文件中。</span><span class="sxs-lookup"><span data-stu-id="5b228-139">Or, add the new drive to your Windows PowerShell profile.</span></span>

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a><span data-ttu-id="5b228-140">删除 Windows PowerShell 驱动器 (Remove-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="5b228-140">Deleting Windows PowerShell Drives (Remove-PSDrive)</span></span>

<span data-ttu-id="5b228-141">你可以通过使用 **Remove-PSDrive** cmdlet 从 Windows PowerShell 中删除驱动器。</span><span class="sxs-lookup"><span data-stu-id="5b228-141">You can delete drives from Windows PowerShell by using the **Remove-PSDrive** cmdlet.</span></span> <span data-ttu-id="5b228-142">**Remove-PSDrive** cmdlet 易于使用；若要删除特定 Windows PowerShell 驱动器，只需提供 Windows PowerShell 驱动器名称。</span><span class="sxs-lookup"><span data-stu-id="5b228-142">The **Remove-PSDrive** cmdlet is easy to use; to delete a specific Windows PowerShell drive, you just supply the Windows PowerShell drive name.</span></span>

<span data-ttu-id="5b228-143">例如，如果你添加了 Office  ：Windows PowerShell 驱动器（如 New-PSDrive 主题中所示），则可以通过键入以下内容将其删除  ：</span><span class="sxs-lookup"><span data-stu-id="5b228-143">For example, if you added the **Office:** Windows PowerShell drive, as shown in the **New-PSDrive** topic, you can delete it by typing:</span></span>

```powershell
Remove-PSDrive -Name Office
```

<span data-ttu-id="5b228-144">若要删除 cvkey:  Windows PowerShell 驱动器（同样，如 New-PSDrive  主题中所示），请使用以下命令：·</span><span class="sxs-lookup"><span data-stu-id="5b228-144">To delete the **cvkey:** Windows PowerShell drive, also shown in the **New-PSDrive** topic, use the following command:</span></span>

```powershell
Remove-PSDrive -Name cvkey
```

<span data-ttu-id="5b228-145">可以轻松删除 Windows PowerShell 驱动器，但是如果你位于该驱动器中，则无法删除它。</span><span class="sxs-lookup"><span data-stu-id="5b228-145">It's easy to delete a Windows PowerShell drive, but you can't delete it while you are in the drive.</span></span> <span data-ttu-id="5b228-146">例如：</span><span class="sxs-lookup"><span data-stu-id="5b228-146">For example:</span></span>

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a><span data-ttu-id="5b228-147">添加和删除 Windows PowerShell 之外的驱动器</span><span class="sxs-lookup"><span data-stu-id="5b228-147">Adding and Removing Drives Outside Windows PowerShell</span></span>

<span data-ttu-id="5b228-148">Windows PowerShell 检测在 Windows 中添加或删除的文件系统驱动器，包括映射的网络驱动器、附加的 USB 驱动器，以及通过使用 **net use** 命令或来自 Windows 脚本宿主 (WSH) 脚本的 **WScript.NetworkMapNetworkDrive** 和 **RemoveNetworkDrive** 方法删除的驱动器。</span><span class="sxs-lookup"><span data-stu-id="5b228-148">Windows PowerShell detects file system drives that are added or removed in Windows, including network drives that are mapped, USB drives that are attached, and drives that are deleted by using either the **net use** command or the **WScript.NetworkMapNetworkDrive** and **RemoveNetworkDrive** methods from a Windows Script Host (WSH) script.</span></span>
