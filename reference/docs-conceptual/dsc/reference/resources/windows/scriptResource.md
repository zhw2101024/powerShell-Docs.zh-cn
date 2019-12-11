---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC Script 资源
ms.openlocfilehash: e09e86011fa7dbb2a4d7f28b5032b4328b6f6ec2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953064"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="eebc0-103">DSC Script 资源</span><span class="sxs-lookup"><span data-stu-id="eebc0-103">DSC Script Resource</span></span>

> <span data-ttu-id="eebc0-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="eebc0-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="eebc0-105">Windows PowerShell Desired State Configuration (DSC) 中的 **Script** 资源提供了在目标节点上运行 Windows PowerShell 脚本的机制。</span><span class="sxs-lookup"><span data-stu-id="eebc0-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="eebc0-106">**Script** 资源使用 **GetScript**、**SetScript** 和 **TestScript** 属性，这些属性包含定义用于执行相应 DSC 状态操作的脚本块。</span><span class="sxs-lookup"><span data-stu-id="eebc0-106">The **Script** resource uses **GetScript**, **SetScript**, and **TestScript** properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

## <a name="syntax"></a><span data-ttu-id="eebc0-107">语法</span><span class="sxs-lookup"><span data-stu-id="eebc0-107">Syntax</span></span>

```Syntax
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> <span data-ttu-id="eebc0-108">**GetScript**、**TestScript** 和 **SetScript** 块作为字符串存储。</span><span class="sxs-lookup"><span data-stu-id="eebc0-108">**GetScript**, **TestScript**, and **SetScript** blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="eebc0-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="eebc0-109">Properties</span></span>

|<span data-ttu-id="eebc0-110">属性</span><span class="sxs-lookup"><span data-stu-id="eebc0-110">Property</span></span> |<span data-ttu-id="eebc0-111">说明</span><span class="sxs-lookup"><span data-stu-id="eebc0-111">Description</span></span> |
|---|---|
|<span data-ttu-id="eebc0-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="eebc0-112">GetScript</span></span> |<span data-ttu-id="eebc0-113">一个返回节点当前状态的脚本块。</span><span class="sxs-lookup"><span data-stu-id="eebc0-113">A script block that returns the current state of the Node.</span></span> |
|<span data-ttu-id="eebc0-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="eebc0-114">SetScript</span></span> |<span data-ttu-id="eebc0-115">DSC 在节点未处于所需状态时用于强制执行符合性的脚本块。</span><span class="sxs-lookup"><span data-stu-id="eebc0-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span> |
|<span data-ttu-id="eebc0-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="eebc0-116">TestScript</span></span> |<span data-ttu-id="eebc0-117">一个用于确定节点是否处于所需状态的脚本块。</span><span class="sxs-lookup"><span data-stu-id="eebc0-117">A script block that determines if the Node is in the desired state.</span></span> |
|<span data-ttu-id="eebc0-118">凭据</span><span class="sxs-lookup"><span data-stu-id="eebc0-118">Credential</span></span> |<span data-ttu-id="eebc0-119">指示要用于运行此脚本的凭据（如果需要凭据）。</span><span class="sxs-lookup"><span data-stu-id="eebc0-119">Indicates the credentials to use for running this script, if credentials are required.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="eebc0-120">公共属性</span><span class="sxs-lookup"><span data-stu-id="eebc0-120">Common properties</span></span>

|<span data-ttu-id="eebc0-121">属性</span><span class="sxs-lookup"><span data-stu-id="eebc0-121">Property</span></span> |<span data-ttu-id="eebc0-122">说明</span><span class="sxs-lookup"><span data-stu-id="eebc0-122">Description</span></span> |
|---|---|
|<span data-ttu-id="eebc0-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="eebc0-123">DependsOn</span></span> |<span data-ttu-id="eebc0-124">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="eebc0-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="eebc0-125">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="eebc0-125">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="eebc0-126">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="eebc0-126">PsDscRunAsCredential</span></span> |<span data-ttu-id="eebc0-127">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="eebc0-127">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="eebc0-128">在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="eebc0-128">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="eebc0-129">有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="eebc0-129">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

### <a name="additional-information"></a><span data-ttu-id="eebc0-130">附加信息</span><span class="sxs-lookup"><span data-stu-id="eebc0-130">Additional information</span></span>

#### <a name="getscript"></a><span data-ttu-id="eebc0-131">GetScript</span><span class="sxs-lookup"><span data-stu-id="eebc0-131">GetScript</span></span>

<span data-ttu-id="eebc0-132">DSC 不使用来自 **GetScript** 的输出。</span><span class="sxs-lookup"><span data-stu-id="eebc0-132">DSC does not use the output from **GetScript**.</span></span> <span data-ttu-id="eebc0-133">[Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet 执行 **GetScript** 以检索节点的当前状态。</span><span class="sxs-lookup"><span data-stu-id="eebc0-133">The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes **GetScript** to retrieve a node's current state.</span></span> <span data-ttu-id="eebc0-134">**GetScript** 不需要返回值。</span><span class="sxs-lookup"><span data-stu-id="eebc0-134">A return value is not required from **GetScript**.</span></span> <span data-ttu-id="eebc0-135">如果指定返回值，则它必须是包含值为字符串的 **Result** 键的哈希表。</span><span class="sxs-lookup"><span data-stu-id="eebc0-135">If you specify a return value, it must be a hashtable containing a **Result** key whose value is a String.</span></span>

#### <a name="testscript"></a><span data-ttu-id="eebc0-136">TestScript</span><span class="sxs-lookup"><span data-stu-id="eebc0-136">TestScript</span></span>

<span data-ttu-id="eebc0-137">DSC 执行 **TestScript** 以确定是否应运行 **SetScript**。</span><span class="sxs-lookup"><span data-stu-id="eebc0-137">**TestScript** is executed by DSC to determine if **SetScript** should be run.</span></span> <span data-ttu-id="eebc0-138">如果 **TestScript** 返回 `$false`，则 DSC 执行 **SetScript** 以使节点恢复到所需的状态。</span><span class="sxs-lookup"><span data-stu-id="eebc0-138">If **TestScript** returns `$false`, DSC executes **SetScript** to bring the node back to the desired state.</span></span> <span data-ttu-id="eebc0-139">它必须返回一个布尔值。</span><span class="sxs-lookup"><span data-stu-id="eebc0-139">It must return a boolean value.</span></span> <span data-ttu-id="eebc0-140">`$true` 的结果表示节点是符合的，不应执行 **SetScript**。</span><span class="sxs-lookup"><span data-stu-id="eebc0-140">A result of `$true` indicates that the node is compliant and **SetScript** should not executed.</span></span>

<span data-ttu-id="eebc0-141">[Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet 执行 **TestScript** 以检索节点是否符合 **Script** 资源。</span><span class="sxs-lookup"><span data-stu-id="eebc0-141">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes **TestScript** to retrieve the nodes compliance with the **Script** resources.</span></span>
<span data-ttu-id="eebc0-142">但是，在这种情况下，无论 **TestScript** 块返回什么，**SetScript** 都不会运行。</span><span class="sxs-lookup"><span data-stu-id="eebc0-142">However, in this case, **SetScript** does not run, no matter what **TestScript** block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="eebc0-143">**TestScript** 的所有输出都是其返回值的一部分。</span><span class="sxs-lookup"><span data-stu-id="eebc0-143">All output from your **TestScript** is part of its return value.</span></span> <span data-ttu-id="eebc0-144">PowerShell 将未压缩的输出视为非零，这意味着无论节点的状态如何，**TestScript** 都将返回 `$true`。</span><span class="sxs-lookup"><span data-stu-id="eebc0-144">PowerShell interprets unsuppressed output as non-zero, which means that your **TestScript** will return `$true` regardless of your node's state.</span></span> <span data-ttu-id="eebc0-145">这会导致不可预测的结果和误报，并导致在故障排除时出现问题。</span><span class="sxs-lookup"><span data-stu-id="eebc0-145">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

#### <a name="setscript"></a><span data-ttu-id="eebc0-146">SetScript</span><span class="sxs-lookup"><span data-stu-id="eebc0-146">SetScript</span></span>

<span data-ttu-id="eebc0-147">**SetScript** 修改节点以强制执行所需的状态。</span><span class="sxs-lookup"><span data-stu-id="eebc0-147">**SetScript** modifies the node to enforce the desired state.</span></span> <span data-ttu-id="eebc0-148">如果 **TestScript** 脚本块返回 `$false`，则其由 DSC 调用。</span><span class="sxs-lookup"><span data-stu-id="eebc0-148">It is called by DSC if the **TestScript** script block returns `$false`.</span></span> <span data-ttu-id="eebc0-149">**SetScript** 应该没有返回值。</span><span class="sxs-lookup"><span data-stu-id="eebc0-149">The **SetScript** should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="eebc0-150">示例</span><span class="sxs-lookup"><span data-stu-id="eebc0-150">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="eebc0-151">示例 1：使用脚本资源编写示例文本</span><span class="sxs-lookup"><span data-stu-id="eebc0-151">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="eebc0-152">此示例测试每个节点上是否存在 `C:\TempFolder\TestFile.txt`。</span><span class="sxs-lookup"><span data-stu-id="eebc0-152">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="eebc0-153">如果它不存在，则使用 `SetScript` 创建它。</span><span class="sxs-lookup"><span data-stu-id="eebc0-153">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="eebc0-154">`GetScript` 返回文件的内容，并且不使用其返回值。</span><span class="sxs-lookup"><span data-stu-id="eebc0-154">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

```powershell
Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="eebc0-155">示例 2：使用脚本资源比较版本信息</span><span class="sxs-lookup"><span data-stu-id="eebc0-155">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="eebc0-156">此示例从创作计算机上的文本文件中检索符合的  版本信息，并将其存储在 `$version` 变量中。</span><span class="sxs-lookup"><span data-stu-id="eebc0-156">This example retrieves the *compliant* version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="eebc0-157">在生成节点的 MOF 文件时，DSC 将每个脚本块中的 `$using:version` 变量替换为 `$version` 变量的值。</span><span class="sxs-lookup"><span data-stu-id="eebc0-157">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>
<span data-ttu-id="eebc0-158">在执行期间，符合的  版本存储在每个节点上的文本文件中，并在后续执行时进行比较和更新。</span><span class="sxs-lookup"><span data-stu-id="eebc0-158">During execution, the *compliant* version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state['Result'] -eq $using:version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
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
}
```