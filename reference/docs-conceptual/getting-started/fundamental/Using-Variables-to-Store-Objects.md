---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "使用变量存储对象"
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: 9a95d421fa2686608a565987c16fecc41c3c6d20
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/13/2017
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="63635-103">使用变量存储对象</span><span class="sxs-lookup"><span data-stu-id="63635-103">Using Variables to Store Objects</span></span>
<span data-ttu-id="63635-104">PowerShell 处理对象。</span><span class="sxs-lookup"><span data-stu-id="63635-104">PowerShell works with objects.</span></span> <span data-ttu-id="63635-105">PowerShell 允许创建实质上是命名对象的变量以保留输出以供以后使用。</span><span class="sxs-lookup"><span data-stu-id="63635-105">PowerShell lets you create variables, essentially named objects, to preserve output for later use.</span></span> <span data-ttu-id="63635-106">如果你习惯在其他 Shell 中处理变量，请记住，PowerShell 变量是对象，而非文本。</span><span class="sxs-lookup"><span data-stu-id="63635-106">If you are used to working with variables in other shells remember that PowerShell variables are objects, not text.</span></span>

<span data-ttu-id="63635-107">始终使用初始字符 $ 指定变量，并且可以在其名称中包含任何字母数字字符或下划线。</span><span class="sxs-lookup"><span data-stu-id="63635-107">Variables are always specified with the initial character $, and can include any alphanumeric characters or the underscore in their names.</span></span>

### <a name="creating-a-variable"></a><span data-ttu-id="63635-108">创建变量</span><span class="sxs-lookup"><span data-stu-id="63635-108">Creating a Variable</span></span>
<span data-ttu-id="63635-109">可以通过键入有效的变量名称来创建变量：</span><span class="sxs-lookup"><span data-stu-id="63635-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="63635-110">这将不返回任何结果，因为 **$loc** 不具有值。</span><span class="sxs-lookup"><span data-stu-id="63635-110">This returns no result because **$loc** does not have a value.</span></span> <span data-ttu-id="63635-111">你可以在同一步骤中创建变量并为其赋值。</span><span class="sxs-lookup"><span data-stu-id="63635-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="63635-112">PowerShell 仅当变量不存在时才创建变量；否则，它会将指定的值赋给现有变量。</span><span class="sxs-lookup"><span data-stu-id="63635-112">PowerShell only creates the variable if it does not exist; otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="63635-113">若要将你的当前位置存储在变量 **$loc**中，请键入：</span><span class="sxs-lookup"><span data-stu-id="63635-113">To store your current location in the variable **$loc**, type:</span></span>

```
$loc = Get-Location
```

<span data-ttu-id="63635-114">当你键入此命令时，不会显示任何输出，因为已将输出发送给 $loc。</span><span class="sxs-lookup"><span data-stu-id="63635-114">There is no output displayed when you type this command because the output is sent to $loc.</span></span> <span data-ttu-id="63635-115">在 PowerShell 中，未定向的数据将始终发送到屏幕，所显示的输出正是这一事实的副作用。</span><span class="sxs-lookup"><span data-stu-id="63635-115">In PowerShell, displayed output is a side effect of the fact that data, which is not otherwise directed, always gets sent to the screen.</span></span> <span data-ttu-id="63635-116">键入 $loc 将显示你的当前位置：</span><span class="sxs-lookup"><span data-stu-id="63635-116">Typing $loc will show your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="63635-117">你可以使用 **Get-Member** 来显示有关变量内容的信息。</span><span class="sxs-lookup"><span data-stu-id="63635-117">You can use **Get-Member** to display information about the contents of variables.</span></span> <span data-ttu-id="63635-118">通过管道将 $loc 传递至 Get-Member 会向你显示这是一个 **PathInfo** 对象，就像 Get-Location 的输出一样：</span><span class="sxs-lookup"><span data-stu-id="63635-118">Piping $loc to Get-Member will show you that it is a **PathInfo** object, just like the output from Get-Location:</span></span>

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### <a name="manipulating-variables"></a><span data-ttu-id="63635-119">操作变量</span><span class="sxs-lookup"><span data-stu-id="63635-119">Manipulating Variables</span></span>
<span data-ttu-id="63635-120">PowerShell 提供多个用以操作变量的命令。</span><span class="sxs-lookup"><span data-stu-id="63635-120">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="63635-121">你可以通过键入以下内容看到可读形式的完整列表：</span><span class="sxs-lookup"><span data-stu-id="63635-121">You can see a complete listing in a readable form by typing:</span></span>

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="63635-122">除了你在当前的 PowerShell 会话中创建的变量，还存在多个系统定义的变量。</span><span class="sxs-lookup"><span data-stu-id="63635-122">In addition to the variables you create in your current PowerShell session, there are several system-defined variables.</span></span> <span data-ttu-id="63635-123">可以使用 Remove-Variable cmdlet 来清除所有不受 PowerShell 控制的变量。</span><span class="sxs-lookup"><span data-stu-id="63635-123">You can use the **Remove-Variable** cmdlet to clear out all of the variables which are not controlled by PowerShell.</span></span> <span data-ttu-id="63635-124">键入以下命令来清除所有变量：</span><span class="sxs-lookup"><span data-stu-id="63635-124">Type the following command to clear all variables:</span></span>

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="63635-125">这将生成你在下方看到的确认提示。</span><span class="sxs-lookup"><span data-stu-id="63635-125">This will produce the confirmation prompt you see below.</span></span>

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

<span data-ttu-id="63635-126">然后，如果运行 Get-Variable cmdlet，则会看到其余的 PowerShell 变量。</span><span class="sxs-lookup"><span data-stu-id="63635-126">If you then run the **Get-Variable** cmdlet, you will see the remaining PowerShell variables.</span></span> <span data-ttu-id="63635-127">由于还存在一个变量 PowerShell 驱动器，也可以通过键入以下内容显示所有的 PowerShell 变量：</span><span class="sxs-lookup"><span data-stu-id="63635-127">Since there is also a variable PowerShell drive, you can also display all PowerShell variables by typing:</span></span>

```
Get-ChildItem variable:
```

### <a name="using-cmdexe-variables"></a><span data-ttu-id="63635-128">使用 Cmd.exe 变量</span><span class="sxs-lookup"><span data-stu-id="63635-128">Using Cmd.exe Variables</span></span>
<span data-ttu-id="63635-129">虽然 PowerShell 不是 Cmd.exe，但它在命令 Shell 环境中运行，并且可以在 Windows 的任何环境中使用相同的可用变量。</span><span class="sxs-lookup"><span data-stu-id="63635-129">Although PowerShell is not Cmd.exe, it runs in a command shell environment and can use the same variables available in any environment in Windows.</span></span> <span data-ttu-id="63635-130">这些变量通过名为 **env** 的驱动器进行公开：</span><span class="sxs-lookup"><span data-stu-id="63635-130">These variables are exposed through a drive named **env**:.</span></span> <span data-ttu-id="63635-131">你可以通过键入以下内容查看这些变量：</span><span class="sxs-lookup"><span data-stu-id="63635-131">You can view these variables by typing:</span></span>

```
Get-ChildItem env:
```

<span data-ttu-id="63635-132">虽然标准变量 cmdlet 并不用于处理 **env:** 变量，但你仍可以通过指定 **env:** 前缀来使用它们。</span><span class="sxs-lookup"><span data-stu-id="63635-132">Although the standard variable cmdlets are not designed to work with **env:** variables, you can still use them by specifying the **env:** prefix.</span></span> <span data-ttu-id="63635-133">例如，若要查看操作系统根目录，可以通过键入以下内容从 PowerShell 内部使用命令 Shell %SystemRoot% 变量：</span><span class="sxs-lookup"><span data-stu-id="63635-133">For example, to see the operating system root directory, you can use the command-shell **%SystemRoot%** variable from within PowerShell by typing:</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="63635-134">还可以从 PowerShell 内部创建和修改环境变量。</span><span class="sxs-lookup"><span data-stu-id="63635-134">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="63635-135">从 Windows PowerShell 访问的环境变量遵循针对 Windows 中其他环境变量的一般规则。</span><span class="sxs-lookup"><span data-stu-id="63635-135">Environment variables accessed from Windows PowerShell conform to the normal rules for environment variables elsewhere in Windows.</span></span>

