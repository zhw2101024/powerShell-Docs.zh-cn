---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 使用变量存储对象
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: f4254199facb914c68a487b281b30070c35550a1
ms.sourcegitcommit: c170a1608d20d3c925d79c35fa208f650d014146
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2018
ms.locfileid: "43353212"
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="91c42-103">使用变量存储对象</span><span class="sxs-lookup"><span data-stu-id="91c42-103">Using variables to store objects</span></span>

<span data-ttu-id="91c42-104">PowerShell 处理对象。</span><span class="sxs-lookup"><span data-stu-id="91c42-104">PowerShell works with objects.</span></span> <span data-ttu-id="91c42-105">使用 PowerShell 可以创建称为“变量”的命名对象。</span><span class="sxs-lookup"><span data-stu-id="91c42-105">PowerShell lets you create named objects known as variables.</span></span>
<span data-ttu-id="91c42-106">变量名称可以包含下划线字符，也可以是任何字母数字字符。</span><span class="sxs-lookup"><span data-stu-id="91c42-106">Variables names can include the underscore character can any alphanumeric characters.</span></span> <span data-ttu-id="91c42-107">在 PowerShell 中使用时，始终使用变量名称后跟的 \$ 字符指定变量。</span><span class="sxs-lookup"><span data-stu-id="91c42-107">When used in PowerShell, a variable is always specified using the \$ character followed by variable name.</span></span>

## <a name="creating-a-variable"></a><span data-ttu-id="91c42-108">创建变量</span><span class="sxs-lookup"><span data-stu-id="91c42-108">Creating a variable</span></span>

<span data-ttu-id="91c42-109">可以通过键入有效的变量名称来创建变量：</span><span class="sxs-lookup"><span data-stu-id="91c42-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="91c42-110">此示例不会返回任何结果，因为 `$loc` 不具有值。</span><span class="sxs-lookup"><span data-stu-id="91c42-110">This example returns no result because `$loc` doesn't have a value.</span></span> <span data-ttu-id="91c42-111">你可以在同一步骤中创建变量并为其赋值。</span><span class="sxs-lookup"><span data-stu-id="91c42-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="91c42-112">如果不存在，PowerShell 将仅创建变量。</span><span class="sxs-lookup"><span data-stu-id="91c42-112">PowerShell only creates the variable if it doesn't exist.</span></span>
<span data-ttu-id="91c42-113">否则，它将指定的值分配给现有变量。</span><span class="sxs-lookup"><span data-stu-id="91c42-113">Otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="91c42-114">下面的示例将当前位置存储在变量 `$loc` 中：</span><span class="sxs-lookup"><span data-stu-id="91c42-114">The following example stores the current location in the variable `$loc`:</span></span>

```powershell
$loc = Get-Location
```

<span data-ttu-id="91c42-115">键入此命令时，PowerShell 不会显示任何输出。</span><span class="sxs-lookup"><span data-stu-id="91c42-115">PowerShell displays no output when you type this command.</span></span> <span data-ttu-id="91c42-116">PowerShell 将“Get-Location”的输出发送到 `$loc`。</span><span class="sxs-lookup"><span data-stu-id="91c42-116">PowerShell sends the output of 'Get-Location' to `$loc`.</span></span> <span data-ttu-id="91c42-117">在 PowerShell 中，未分配或未重定向的数据将发送到屏幕。</span><span class="sxs-lookup"><span data-stu-id="91c42-117">In PowerShell, data that isn't assigned or redirected is sent to the screen.</span></span> <span data-ttu-id="91c42-118">键入 `$loc` 将显示当前位置：</span><span class="sxs-lookup"><span data-stu-id="91c42-118">Typing `$loc` shows your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="91c42-119">可以使用 `Get-Member` 显示有关变量内容的信息。</span><span class="sxs-lookup"><span data-stu-id="91c42-119">You can use `Get-Member` to display information about the contents of variables.</span></span> <span data-ttu-id="91c42-120">`Get-Member` 表示 `$loc` 是 PathInfo 对象，类似于来自 `Get-Location` 的输出：</span><span class="sxs-lookup"><span data-stu-id="91c42-120">`Get-Member` shows you that `$loc` is a **PathInfo** object, just like the output from `Get-Location`:</span></span>

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a><span data-ttu-id="91c42-121">操作变量</span><span class="sxs-lookup"><span data-stu-id="91c42-121">Manipulating variables</span></span>

<span data-ttu-id="91c42-122">PowerShell 提供多个用以操作变量的命令。</span><span class="sxs-lookup"><span data-stu-id="91c42-122">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="91c42-123">你可以通过键入以下内容看到可读形式的完整列表：</span><span class="sxs-lookup"><span data-stu-id="91c42-123">You can see a complete listing in a readable form by typing:</span></span>

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="91c42-124">PowerShell 还会创建系统定义的多个变量。</span><span class="sxs-lookup"><span data-stu-id="91c42-124">PowerShell also creates several system-defined variables.</span></span> <span data-ttu-id="91c42-125">可以使用 `Remove-Variable` cmdlet 来删除当前会话中所有不受 PowerShell 控制的变量。</span><span class="sxs-lookup"><span data-stu-id="91c42-125">You can use the `Remove-Variable` cmdlet to remove variables, which are not controlled by PowerShell, from the current session.</span></span> <span data-ttu-id="91c42-126">键入以下命令来清除所有变量：</span><span class="sxs-lookup"><span data-stu-id="91c42-126">Type the following command to clear all variables:</span></span>

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="91c42-127">运行上述命令后，`Get-Variable` cmdlet 显示 PowerShell 系统变量。</span><span class="sxs-lookup"><span data-stu-id="91c42-127">After running the previous command, the `Get-Variable` cmdlet shows the PowerShell system variables.</span></span>

<span data-ttu-id="91c42-128">PowerShell 还会创建一个变量驱动器。</span><span class="sxs-lookup"><span data-stu-id="91c42-128">PowerShell also creates a variable drive.</span></span> <span data-ttu-id="91c42-129">使用下面的示例显示使用变量驱动器的所有 PowerShell 变量：</span><span class="sxs-lookup"><span data-stu-id="91c42-129">Use the following example to display all PowerShell variables using the variable drive:</span></span>

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a><span data-ttu-id="91c42-130">使用 cmd.exe 变量</span><span class="sxs-lookup"><span data-stu-id="91c42-130">Using cmd.exe variables</span></span>

<span data-ttu-id="91c42-131">PowerShell 可以使用任何 Windows 进程可用的相同环境变量，其中包括 cmd.exe。</span><span class="sxs-lookup"><span data-stu-id="91c42-131">PowerShell can use the same environment variables available to any Windows process, including **cmd.exe**.</span></span> <span data-ttu-id="91c42-132">这些变量通过名为 `env:` 的驱动器公开。</span><span class="sxs-lookup"><span data-stu-id="91c42-132">These variables are exposed through a drive named `env:`.</span></span> <span data-ttu-id="91c42-133">可以通过键入以下命令查看这些变量：</span><span class="sxs-lookup"><span data-stu-id="91c42-133">You can view these variables by typing the following command:</span></span>

```powershell
Get-ChildItem env:
```

<span data-ttu-id="91c42-134">标准 `*-Variable` cmdlet 未设计为使用环境变量。</span><span class="sxs-lookup"><span data-stu-id="91c42-134">The standard `*-Variable` cmdlets aren't designed to work with environment variables.</span></span> <span data-ttu-id="91c42-135">使用 `env:` 驱动器前缀访问环境变量。</span><span class="sxs-lookup"><span data-stu-id="91c42-135">Environment variables are accessed using the `env:` drive prefix.</span></span> <span data-ttu-id="91c42-136">例如，cmd.exe 中的 %SystemRoot% 变量包含操作系统的根目录名称。</span><span class="sxs-lookup"><span data-stu-id="91c42-136">For example, the **%SystemRoot%** variable in **cmd.exe** contains the operating system's root directory name.</span></span> <span data-ttu-id="91c42-137">在 PowerShell 中，使用 `$env:SystemRoot` 可访问相同的值。</span><span class="sxs-lookup"><span data-stu-id="91c42-137">In PowerShell, you use `$env:SystemRoot` to access the same value.</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="91c42-138">还可以从 PowerShell 内部创建和修改环境变量。</span><span class="sxs-lookup"><span data-stu-id="91c42-138">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="91c42-139">PowerShell 中的环境变量遵循操作系统中其他地方使用的环境变量的相同规则。</span><span class="sxs-lookup"><span data-stu-id="91c42-139">Environment variables in PowerShell follow the same rules for environment variables used elsewhere in the operating system.</span></span> <span data-ttu-id="91c42-140">下面的示例创建一个新的环境变量：</span><span class="sxs-lookup"><span data-stu-id="91c42-140">The following example creates a new environment variable:</span></span>

```powershell
$env:LIB_PATH='/usr/local/lib'
```

<span data-ttu-id="91c42-141">尽管没有要求，但环境变量名称通常使用全部大写字母。</span><span class="sxs-lookup"><span data-stu-id="91c42-141">Though not required, is it common for environment variable names to use all uppercase letters.</span></span>