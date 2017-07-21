---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "DSC Script 资源"
ms.openlocfilehash: 81718de0b0c8463189e33e565dc9ff39692dbe8b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-script-resource"></a><span data-ttu-id="5cfd6-103">DSC Script 资源</span><span class="sxs-lookup"><span data-stu-id="5cfd6-103">DSC Script Resource</span></span>

 
> <span data-ttu-id="5cfd6-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5cfd6-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="5cfd6-105">Windows PowerShell Desired State Configuration (DSC) 中的 **Script** 资源提供了在目标节点上运行 Windows PowerShell 脚本的机制。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="5cfd6-106">`Script` 资源具有 `GetScript`、`SetScript` 和 `TestScript` 属性。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-106">The `Script` resource has `GetScript`, `SetScript`, and `TestScript` properties.</span></span> <span data-ttu-id="5cfd6-107">应将这些属性设置为将在每个目标节点上运行的脚本块。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-107">These properties should be set to script blocks that will run on each target node.</span></span> 

<span data-ttu-id="5cfd6-108">`GetScript` 脚本块应返回表示当前节点状态的哈希表。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-108">The `GetScript` script block should return a hashtable representing the state of the current node.</span></span> <span data-ttu-id="5cfd6-109">哈希表必须只包含一个键 `Result`，并且值必须属于 `String` 类型。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-109">The hashtable must only contain one key `Result` and the value must be of type `String`.</span></span> <span data-ttu-id="5cfd6-110">它不需要返回任何内容。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-110">It is not required to return anything.</span></span> <span data-ttu-id="5cfd6-111">DSC 不与此脚本块的输出执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-111">DSC doesn't do anything with the output of this script block.</span></span>

<span data-ttu-id="5cfd6-112">`TestScript` 脚本块应确定当前节点是否需要进行修改。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-112">The `TestScript` script block should determine if the current node needs to be modified.</span></span> <span data-ttu-id="5cfd6-113">如果节点是最新的，它应返回 `$true`。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-113">It should return `$true` if the node is up-to-date.</span></span> <span data-ttu-id="5cfd6-114">如果节点的配置已过期，它应返回 `$false`，并且应使用 `SetScript` 脚本块进行更新。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-114">It should return `$false` if the node's configuration is out-of-date and should be updated by the `SetScript` script block.</span></span> <span data-ttu-id="5cfd6-115">`TestScript` 脚本块由 DSC 调用。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-115">The `TestScript` script block is called by DSC.</span></span>

<span data-ttu-id="5cfd6-116">`SetScript` 脚本块应修改该节点。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-116">The `SetScript` script block should modify the node.</span></span> <span data-ttu-id="5cfd6-117">如果 `TestScript` 块返回 `$false`，则其由 DSC 调用。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-117">It is called by DSC if the `TestScript` block return `$false`.</span></span>

<span data-ttu-id="5cfd6-118">如果需要从 `GetScript`、`TestScript` 或者 `SetScript` 脚本块内的配置脚本使用变量，请使用 `$using:` 作用域（参见以下内容为例）。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-118">If you need to use variables from your configuration script in the `GetScript`, `TestScript`, or `SetScript` script blocks, use the `$using:` scope (see below for an example).</span></span>


## <a name="syntax"></a><span data-ttu-id="5cfd6-119">语法</span><span class="sxs-lookup"><span data-stu-id="5cfd6-119">Syntax</span></span>

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="5cfd6-120">“属性”</span><span class="sxs-lookup"><span data-stu-id="5cfd6-120">Properties</span></span>

|  <span data-ttu-id="5cfd6-121">属性</span><span class="sxs-lookup"><span data-stu-id="5cfd6-121">Property</span></span>  |  <span data-ttu-id="5cfd6-122">说明</span><span class="sxs-lookup"><span data-stu-id="5cfd6-122">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="5cfd6-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="5cfd6-123">GetScript</span></span>| <span data-ttu-id="5cfd6-124">提供调用 [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) cmdlet 时运行的 Windows PowerShell 脚本块。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-124">Provides a block of Windows PowerShell script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) cmdlet.</span></span> <span data-ttu-id="5cfd6-125">此块必须返回一个哈希表。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-125">This block must return a hashtable.</span></span> <span data-ttu-id="5cfd6-126">哈希表必须只包含一个键 **Result**，并且值必须属于 **String** 类型。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-126">The hashtable must only contain one key **Result** and the value must be of type **String**.</span></span>| 
| <span data-ttu-id="5cfd6-127">SetScript</span><span class="sxs-lookup"><span data-stu-id="5cfd6-127">SetScript</span></span>| <span data-ttu-id="5cfd6-128">提供 Windows PowerShell 脚本块。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-128">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="5cfd6-129">调用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet 时，将首先运行 **TestScript** 块。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-129">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** block runs first.</span></span> <span data-ttu-id="5cfd6-130">如果 **TestScript** 块返回 **$false**，则将运行 **SetScript** 块。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-130">If the **TestScript** block returns **$false**, the **SetScript** block will run.</span></span> <span data-ttu-id="5cfd6-131">如果 **TestScript** 块返回 **$true**，**SetScript** 块将不会运行。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-131">If the **TestScript** block returns **$true**, the **SetScript** block will not run.</span></span>| 
| <span data-ttu-id="5cfd6-132">TestScript</span><span class="sxs-lookup"><span data-stu-id="5cfd6-132">TestScript</span></span>| <span data-ttu-id="5cfd6-133">提供 Windows PowerShell 脚本块。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-133">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="5cfd6-134">调用 [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet 时，将运行此块。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-134">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this block runs.</span></span> <span data-ttu-id="5cfd6-135">如果它返回 **$false**，将运行 SetScript 块。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-135">If it returns **$false**, the SetScript block will run.</span></span> <span data-ttu-id="5cfd6-136">如果它返回 **$true**，将不运行 SetScript 块。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-136">If it returns **$true**, the SetScript block will not run.</span></span> <span data-ttu-id="5cfd6-137">调用 [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet 时，也将运行 **TestScript** 块。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-137">The **TestScript** block also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="5cfd6-138">但是，在这种情况下，无论 TestScript 返回何值，都不会运行 **SetScript**。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-138">However, in this case, the **SetScript** block will not run, no matter what value the TestScript block returns.</span></span> <span data-ttu-id="5cfd6-139">如果实际配置与当前所需状态配置相匹配，**TestScript** 块必返回 True，如果不匹配，则返回 False。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-139">The **TestScript** block must return True if the actual configuration matches the current desired state configuration, and False if it does not match.</span></span> <span data-ttu-id="5cfd6-140">（当前所需状态配置是在使用 DSC 的节点上执行的最后一个配置。）</span><span class="sxs-lookup"><span data-stu-id="5cfd6-140">(The current desired state configuration is the last configuration enacted on the node that is using DSC.)</span></span>| 
| <span data-ttu-id="5cfd6-141">凭据</span><span class="sxs-lookup"><span data-stu-id="5cfd6-141">Credential</span></span>| <span data-ttu-id="5cfd6-142">指示要用于运行此脚本的凭据（如果需要凭据）。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-142">Indicates the credentials to use for running this script, if credentials are required.</span></span>| 
| <span data-ttu-id="5cfd6-143">DependsOn</span><span class="sxs-lookup"><span data-stu-id="5cfd6-143">DependsOn</span></span>| <span data-ttu-id="5cfd6-144">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-144">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5cfd6-145">例如，如果你想要首先运行 ID 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-145">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

## <a name="example-1"></a><span data-ttu-id="5cfd6-146">示例 1</span><span class="sxs-lookup"><span data-stu-id="5cfd6-146">Example 1</span></span>
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script ScriptExample
    {
        SetScript = 
        { 
            $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
            $sw.WriteLine("Some sample string")
            $sw.Close()
        }
        TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
        GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }          
    }
}
```

## <a name="example-2"></a><span data-ttu-id="5cfd6-147">示例 2</span><span class="sxs-lookup"><span data-stu-id="5cfd6-147">Example 2</span></span>
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script UpdateConfigurationVersion
    {
        GetScript = { 
            $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            return @{ 'Version' = "$currentVersion" }
        }          
        TestScript = { 
            $state = $GetScript
            if( $state['Version'] -eq $using:version )
            {
                Write-Verbose -Message ('{0} -eq {1}' -f $state['Version'],$using:version)
                return $true
            }
            Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
            return $false
        }
        SetScript = { 
            $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
        }
    }
}
```

<span data-ttu-id="5cfd6-148">此资源正在将配置的版本写入文本文件。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-148">This resource is writing the configuration's version to a text file.</span></span> <span data-ttu-id="5cfd6-149">此版本在客户端计算机上可用，但不在任何节点上，因此必须通过 PowerShell 的 `using` 作用域将其传递到每个 `Script` 资源的脚本块。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-149">This version is available on the client computer, but isn't on any of the nodes, so it has to be passed to each of the `Script` resource's script blocks with PowerShell's `using` scope.</span></span> <span data-ttu-id="5cfd6-150">生成节点的 MOF 文件时，将从客户端计算机上的文本文件读取 `$version` 变量的值。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-150">When generating the node's MOF file, the value of the `$version` variable is read from a text file on the client computer.</span></span> <span data-ttu-id="5cfd6-151">DSC 将每个脚本块中的 `$using:version` 变量替换为 `$version` 变量的值。</span><span class="sxs-lookup"><span data-stu-id="5cfd6-151">DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>

