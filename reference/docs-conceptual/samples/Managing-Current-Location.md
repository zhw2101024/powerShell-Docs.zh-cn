---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 管理当前位置
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
ms.openlocfilehash: f5e0653b2c3bbc9d2526c7a1c2ff88a8a6641695
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086249"
---
# <a name="managing-current-location"></a><span data-ttu-id="c3df1-103">管理当前位置</span><span class="sxs-lookup"><span data-stu-id="c3df1-103">Managing Current Location</span></span>

<span data-ttu-id="c3df1-104">在文件资源管理器中导航文件夹系统时，你通常具有一个特定的工作位置（即当前打开的文件夹）。</span><span class="sxs-lookup"><span data-stu-id="c3df1-104">When navigating folder systems in File Explorer, you usually have a specific working location - namely, the current open folder.</span></span> <span data-ttu-id="c3df1-105">通过单击当前文件夹中的项，可轻松对其进行操作。</span><span class="sxs-lookup"><span data-stu-id="c3df1-105">Items in the current folder can be manipulated easily by clicking them.</span></span> <span data-ttu-id="c3df1-106">对于命令行接口（例如 Cmd.exe），当你位于特定文件所在的相同文件夹中时，你可以通过指定一个相对较短的名称来访问它，而无需指定该文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="c3df1-106">For command-line interfaces such as Cmd.exe, when you are in the same folder as a particular file, you can access it by specifying a relatively short name, rather than needing to specify the entire path to the file.</span></span> <span data-ttu-id="c3df1-107">当前目录称为工作目录。</span><span class="sxs-lookup"><span data-stu-id="c3df1-107">The current directory is called the working directory.</span></span>

<span data-ttu-id="c3df1-108">Windows PowerShell 使用名词 **Location** 来引用工作目录，并实现一系列 cmdlet 以检查你的位置并对其进行操作。</span><span class="sxs-lookup"><span data-stu-id="c3df1-108">Windows PowerShell uses the noun **Location** to refer to the working directory, and implements a family of cmdlets to examine and manipulate your location.</span></span>

## <a name="getting-your-current-location-get-location"></a><span data-ttu-id="c3df1-109">获取你的当前位置 (Get-Location)</span><span class="sxs-lookup"><span data-stu-id="c3df1-109">Getting Your Current Location (Get-Location)</span></span>

<span data-ttu-id="c3df1-110">若要确定你的当前目录位置的路径，请输入 **Get-Location** 命令：</span><span class="sxs-lookup"><span data-stu-id="c3df1-110">To determine the path of your current directory location, enter the **Get-Location** command:</span></span>

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="c3df1-111">Get-Location cmdlet 类似于 BASH shell 中的 **pwd** 命令。</span><span class="sxs-lookup"><span data-stu-id="c3df1-111">The Get-Location cmdlet is similar to the **pwd** command in the BASH shell.</span></span> <span data-ttu-id="c3df1-112">Set-Location cmdlet 类似于 Cmd.exe 中的 **cd** 命令。</span><span class="sxs-lookup"><span data-stu-id="c3df1-112">The Set-Location cmdlet is similar to the **cd** command in Cmd.exe.</span></span>

## <a name="setting-your-current-location-set-location"></a><span data-ttu-id="c3df1-113">设置你的当前位置 (Set-Location)</span><span class="sxs-lookup"><span data-stu-id="c3df1-113">Setting Your Current Location (Set-Location)</span></span>

<span data-ttu-id="c3df1-114">**Get-Location** 命令与 **Set-Location** 命令结合使用。</span><span class="sxs-lookup"><span data-stu-id="c3df1-114">The **Get-Location** command is used with the **Set-Location** command.</span></span> <span data-ttu-id="c3df1-115">**Set-Location** 命令允许你指定当前目录位置。</span><span class="sxs-lookup"><span data-stu-id="c3df1-115">The **Set-Location** command allows you to specify your current directory location.</span></span>

```powershell
Set-Location -Path C:\Windows
```

<span data-ttu-id="c3df1-116">输入命令后，你将注意到你不会收到任何有关该命令影响的直接反馈。</span><span class="sxs-lookup"><span data-stu-id="c3df1-116">After you enter the command, you will notice that you do not receive any direct feedback about the effect of the command.</span></span> <span data-ttu-id="c3df1-117">执行某项操作的大多数 Windows PowerShell 命令可生成很少的输出或根本不会生成输出，因为该输出并不总是有用。</span><span class="sxs-lookup"><span data-stu-id="c3df1-117">Most Windows PowerShell commands that perform an action produce little or no output because the output is not always useful.</span></span> <span data-ttu-id="c3df1-118">若要验证在你输入 **Set-Location** 命令时是否已成功更改目录，请在输入 **Set-Location** 命令时包括 **-PassThru** 参数：</span><span class="sxs-lookup"><span data-stu-id="c3df1-118">To verify that a successful directory change has occurred when you enter the **Set-Location** command, include the **-PassThru** parameter when you enter the **Set-Location** command:</span></span>

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

<span data-ttu-id="c3df1-119">可将 **-PassThru** 参数与 Windows PowerShell 中的许多 Set 命令结合使用，以在没有默认输出的情况下返回有关结果的信息。</span><span class="sxs-lookup"><span data-stu-id="c3df1-119">The **-PassThru** parameter can be used with many Set commands in Windows PowerShell to return information about the result in cases in which there is no default output.</span></span>

<span data-ttu-id="c3df1-120">采用在大多数 UNIX 和 Windows 命令 shell 中指定路径的相同方式，指定相对于当前位置的路径。</span><span class="sxs-lookup"><span data-stu-id="c3df1-120">You can specify paths relative to your current location in the same way as you would in most UNIX and Windows command shells.</span></span> <span data-ttu-id="c3df1-121">在相对路径的标准表示法中，句点 (**.**) 表示当前文件夹，而双句点 (**..**) 表示当前位置的父目录。</span><span class="sxs-lookup"><span data-stu-id="c3df1-121">In standard notation for relative paths, a period (**.**)represents your current folder, and a doubled period (**..**) represents the parent directory of your current location.</span></span>

<span data-ttu-id="c3df1-122">例如，如果你位于 **C:\\Windows** 文件夹中，则句点 (**.**) 表示 **C:\\Windows**，而双句点 (**..**) 表示 **C:**。</span><span class="sxs-lookup"><span data-stu-id="c3df1-122">For example, if you are in the **C:\\Windows** folder, a period (**.**)represents **C:\\Windows** and double periods (**..**) represent **C:**.</span></span> <span data-ttu-id="c3df1-123">你可以从当前位置更改到 C: 驱动器的根目录，方法是键入：</span><span class="sxs-lookup"><span data-stu-id="c3df1-123">You can change from your current location to the root of the C: drive by typing:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

<span data-ttu-id="c3df1-124">相同的技术适用于非文件系统驱动器（例如 **HKLM:**）的 Windows PowerShell 驱动器。</span><span class="sxs-lookup"><span data-stu-id="c3df1-124">The same technique works on Windows PowerShell drives that are not file system drives, such as **HKLM:**.</span></span> <span data-ttu-id="c3df1-125">可以在注册表中将你的位置设置为 HKLM\\Software 项，方法是键入：</span><span class="sxs-lookup"><span data-stu-id="c3df1-125">You can set your location to the HKLM\\Software key in the registry by typing:</span></span>

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

<span data-ttu-id="c3df1-126">然后，可以通过使用相对路径将目录位置更改为父目录，它是 Windows PowerShell HKLM: 驱动器的根目录：</span><span class="sxs-lookup"><span data-stu-id="c3df1-126">You can then change the directory location to the parent directory, which is the root of the Windows PowerShell HKLM: drive, by using a relative path:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

<span data-ttu-id="c3df1-127">你可以键入 Set-Location，或使用任何用于 Set-Location（cd、chdir、sl）的内置 Windows PowerShell 别名。</span><span class="sxs-lookup"><span data-stu-id="c3df1-127">You can type Set-Location or use any of the built-in Windows PowerShell aliases for Set-Location (cd, chdir, sl).</span></span> <span data-ttu-id="c3df1-128">例如：</span><span class="sxs-lookup"><span data-stu-id="c3df1-128">For example:</span></span>

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

## <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a><span data-ttu-id="c3df1-129">保存和重新调用最近的位置（Push-Location 和 Pop-Location）</span><span class="sxs-lookup"><span data-stu-id="c3df1-129">Saving and Recalling Recent Locations (Push-Location and Pop-Location)</span></span>

<span data-ttu-id="c3df1-130">当更改位置时，它有助于跟踪你访问过的位置并使你能够返回到之前的位置。</span><span class="sxs-lookup"><span data-stu-id="c3df1-130">When changing locations, it is helpful to keep track of where you have been and to be able to return to your previous location.</span></span> <span data-ttu-id="c3df1-131">Windows PowerShell 中的 **Push-Location** cmdlet 将创建一个你访问过的目录路径的有序历史记录（“堆栈”），你可以通过使用补充的 **Pop-Location** cmdlet 在目录路径历史记录上返回到之前位置。</span><span class="sxs-lookup"><span data-stu-id="c3df1-131">The **Push-Location** cmdlet in Windows PowerShell creates a ordered history (a "stack") of directory paths where you have been, and you can step back through the history of directory paths by using the complementary **Pop-Location** cmdlet.</span></span>

<span data-ttu-id="c3df1-132">例如，Windows PowerShell 通常在用户的主目录中启动。</span><span class="sxs-lookup"><span data-stu-id="c3df1-132">For example, Windows PowerShell typically starts in the user's home directory.</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="c3df1-133">字词 *stack* 在许多编程设置（包括 .NET Framework）中具有特殊含义。</span><span class="sxs-lookup"><span data-stu-id="c3df1-133">The word *stack* has a special meaning in many programming settings, including .NET Framework.</span></span> <span data-ttu-id="c3df1-134">例如项的物理堆栈，你放置在堆栈上的最后一项是可以从堆栈中提取的第一个项。</span><span class="sxs-lookup"><span data-stu-id="c3df1-134">Like a physical stack of items, the last item you put onto the stack is the first item that you can pull off the stack.</span></span> <span data-ttu-id="c3df1-135">将项添加到堆栈俗称为将项“推送”到堆栈上。</span><span class="sxs-lookup"><span data-stu-id="c3df1-135">Adding an item to a stack is colloquially known as "pushing" the item onto the stack.</span></span> <span data-ttu-id="c3df1-136">从堆栈中提取项俗称为将项从堆栈中“弹出”。</span><span class="sxs-lookup"><span data-stu-id="c3df1-136">Pulling an item off the stack is colloquially known as "popping" the item off the stack.</span></span>

<span data-ttu-id="c3df1-137">若要将当前位置推送到堆栈上，然后将其移动到“本地设置”文件夹，请键入：</span><span class="sxs-lookup"><span data-stu-id="c3df1-137">To push the current location onto the stack, and then move to the Local Settings folder, type:</span></span>

```powershell
Push-Location -Path "Local Settings"
```

<span data-ttu-id="c3df1-138">然后，可以将“本地设置”位置推送到堆栈上，并将其移动到临时文件夹，方法是通过键入：</span><span class="sxs-lookup"><span data-stu-id="c3df1-138">You can then push the Local Settings location onto the stack and move to the Temp folder by typing:</span></span>

```powershell
Push-Location -Path Temp
```

<span data-ttu-id="c3df1-139">你可以验证是否通过输入 **Get-Location** 命令更改了目录：</span><span class="sxs-lookup"><span data-stu-id="c3df1-139">You can verify that you changed directories by entering the **Get-Location** command:</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

<span data-ttu-id="c3df1-140">然后，你可以通过输入 **Pop-Location** 命令弹回到最近访问的目录中，并且通过输入 **Get-Location** 命令验证该更改：</span><span class="sxs-lookup"><span data-stu-id="c3df1-140">You can then pop back into the most recently visited directory by entering the **Pop-Location** command, and verify the change by entering the **Get-Location** command:</span></span>

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

<span data-ttu-id="c3df1-141">像 **Set-Location** cmdlet 一样，当你输入 **Pop-Location** cmdlet 来显示输入的目录时，你可以包含 **-PassThru** 参数：</span><span class="sxs-lookup"><span data-stu-id="c3df1-141">Just as with the **Set-Location** cmdlet, you can include the **-PassThru** parameter when you enter the **Pop-Location** cmdlet to display the directory that you entered:</span></span>

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

<span data-ttu-id="c3df1-142">还可以将 Location cmdlet 与网络路径结合使用。</span><span class="sxs-lookup"><span data-stu-id="c3df1-142">You can also use the Location cmdlets with network paths.</span></span> <span data-ttu-id="c3df1-143">如果你有一个名为 FS01 并且共享名为 Public 的服务器，你可以通过键入以下内容更改你的位置</span><span class="sxs-lookup"><span data-stu-id="c3df1-143">If you have a server named FS01 with an share named Public, you can change your location by typing</span></span>

```powershell
Set-Location \\FS01\Public
```

<span data-ttu-id="c3df1-144">或</span><span class="sxs-lookup"><span data-stu-id="c3df1-144">or</span></span>

```powershell
Push-Location \\FS01\Public
```

<span data-ttu-id="c3df1-145">你可以使用 **Push-Location** 和 **Set-Location** 命令将位置更改为任何可用的驱动器。</span><span class="sxs-lookup"><span data-stu-id="c3df1-145">You can use the **Push-Location** and **Set-Location** commands to change the location to any available drive.</span></span> <span data-ttu-id="c3df1-146">例如，如果你有驱动号为 D 且包含数据 CD 的本地 CD-ROM 驱动器，你可以通过输入 **Set-Location D:** 命令将该位置更改为 CD 驱动器。</span><span class="sxs-lookup"><span data-stu-id="c3df1-146">For example, if you have a local CD-ROM drive with drive letter D that contains a data CD, you can change the location to the CD drive by entering the **Set-Location D:** command.</span></span>

<span data-ttu-id="c3df1-147">如果驱动器是空的，你将获得以下错误消息：</span><span class="sxs-lookup"><span data-stu-id="c3df1-147">If the drive is empty, you will get the following error message:</span></span>

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

<span data-ttu-id="c3df1-148">当你使用命令行接口时，使用文件资源管理器检查可用的物理驱动器会很不方便。</span><span class="sxs-lookup"><span data-stu-id="c3df1-148">When you are using a command-line interface, it is not convenient to use File Explorer to examine the available physical drives.</span></span> <span data-ttu-id="c3df1-149">此外，文件资源管理器不会向你显示所有 Windows PowerShell 驱动器。</span><span class="sxs-lookup"><span data-stu-id="c3df1-149">Also, File Explorer would not show you the all of the Windows PowerShell drives.</span></span> <span data-ttu-id="c3df1-150">Windows PowerShell 提供一组命令，用于对 Windows PowerShell 驱动器进行操作，我们将在下一步讨论这些命令。</span><span class="sxs-lookup"><span data-stu-id="c3df1-150">Windows PowerShell provides a set of commands for manipulating Windows PowerShell drives, and we will talk about these next.</span></span>
