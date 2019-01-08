---
ms.date: 08/24/2018
keywords: dsc,powershell,配置,安装程序
title: DSC Script 资源
ms.openlocfilehash: ef84239820a44aab2a028f7f0fe17653a851b72e
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047191"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="274a2-103">DSC Script 资源</span><span class="sxs-lookup"><span data-stu-id="274a2-103">DSC Script Resource</span></span>

> <span data-ttu-id="274a2-104">适用于：Windows PowerShell 4.0 中，Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="274a2-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="274a2-105">Windows PowerShell Desired State Configuration (DSC) 中的 **Script** 资源提供了在目标节点上运行 Windows PowerShell 脚本的机制。</span><span class="sxs-lookup"><span data-stu-id="274a2-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="274a2-106">脚本资源使用 `GetScript``SetScript` 和 `TestScript` 属性，这些属性包含定义以执行相应的 DSC 状态操作的脚本块。</span><span class="sxs-lookup"><span data-stu-id="274a2-106">The **Script** resource uses `GetScript`, `SetScript`, and `TestScript` properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

## <a name="syntax"></a><span data-ttu-id="274a2-107">语法</span><span class="sxs-lookup"><span data-stu-id="274a2-107">Syntax</span></span>

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

> [!NOTE]
> <span data-ttu-id="274a2-108">将 `GetScript`、`TestScript` 和 `SetScript` 块存储为字符串。</span><span class="sxs-lookup"><span data-stu-id="274a2-108">The `GetScript`, `TestScript`, and `SetScript` blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="274a2-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="274a2-109">Properties</span></span>

|<span data-ttu-id="274a2-110">属性</span><span class="sxs-lookup"><span data-stu-id="274a2-110">Property</span></span>|<span data-ttu-id="274a2-111">说明</span><span class="sxs-lookup"><span data-stu-id="274a2-111">Description</span></span>|
|--------|-----------|
|<span data-ttu-id="274a2-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="274a2-112">GetScript</span></span>|<span data-ttu-id="274a2-113">一个返回节点当前状态的脚本块。</span><span class="sxs-lookup"><span data-stu-id="274a2-113">A script block that returns the current state of the Node.</span></span>|
|<span data-ttu-id="274a2-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="274a2-114">SetScript</span></span>|<span data-ttu-id="274a2-115">DSC 在节点未处于所需状态时用于强制执行符合性的脚本块。</span><span class="sxs-lookup"><span data-stu-id="274a2-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span>|
|<span data-ttu-id="274a2-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="274a2-116">TestScript</span></span>|<span data-ttu-id="274a2-117">一个用于确定节点是否处于所需状态的脚本块。</span><span class="sxs-lookup"><span data-stu-id="274a2-117">A script block that determines if the Node is in the desired state.</span></span>|
|<span data-ttu-id="274a2-118">凭据</span><span class="sxs-lookup"><span data-stu-id="274a2-118">Credential</span></span>| <span data-ttu-id="274a2-119">指示要用于运行此脚本的凭据（如果需要凭据）。</span><span class="sxs-lookup"><span data-stu-id="274a2-119">Indicates the credentials to use for running this script, if credentials are required.</span></span>|
|<span data-ttu-id="274a2-120">DependsOn</span><span class="sxs-lookup"><span data-stu-id="274a2-120">DependsOn</span></span>| <span data-ttu-id="274a2-121">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="274a2-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="274a2-122">例如，如果你想要首先运行 ID 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="274a2-122">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

### <a name="getscript"></a><span data-ttu-id="274a2-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="274a2-123">GetScript</span></span>

<span data-ttu-id="274a2-124">DSC 不使用来自 `GetScript` 的输出。</span><span class="sxs-lookup"><span data-stu-id="274a2-124">DSC does not use the output from `GetScript`.</span></span> <span data-ttu-id="274a2-125">[Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet 执行 `GetScript` 以检索节点的当前状态。</span><span class="sxs-lookup"><span data-stu-id="274a2-125">The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes the `GetScript` to retrieve a node's current state.</span></span> <span data-ttu-id="274a2-126">`GetScript` 不需要返回值。</span><span class="sxs-lookup"><span data-stu-id="274a2-126">A return value is not required from `GetScript`.</span></span> <span data-ttu-id="274a2-127">如果指定返回值，则它必须是包含值为 `String` 的 Result 键的 `hashtable`。</span><span class="sxs-lookup"><span data-stu-id="274a2-127">If you specify a return value, it must be a `hashtable` containing a **Result** key whose value is a `String`.</span></span>

### <a name="testscript"></a><span data-ttu-id="274a2-128">TestScript</span><span class="sxs-lookup"><span data-stu-id="274a2-128">TestScript</span></span>

<span data-ttu-id="274a2-129">DSC 执行 `TestScript` 以确定是否应运行 `SetScript`。</span><span class="sxs-lookup"><span data-stu-id="274a2-129">The `TestScript` is executed by DSC to determine if the `SetScript` should be run.</span></span> <span data-ttu-id="274a2-130">如果 `TestScript` 返回 `$false`，则 DSC 执行 `SetScript` 以使节点恢复到所需状态。</span><span class="sxs-lookup"><span data-stu-id="274a2-130">If the `TestScript` returns `$false`, DSC executes the `SetScript` to bring the node back to the desired state.</span></span> <span data-ttu-id="274a2-131">它必须返回一个 `boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="274a2-131">It must return a `boolean` value.</span></span> <span data-ttu-id="274a2-132">`$true` 的结果表示节点是符合的，不应执行 `SetScript`。</span><span class="sxs-lookup"><span data-stu-id="274a2-132">A result of `$true` indicates that the node is compliant and `SetScript` should not executed.</span></span>

<span data-ttu-id="274a2-133">[Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet 执行 `TestScript` 以检索节点是否符合脚本资源。</span><span class="sxs-lookup"><span data-stu-id="274a2-133">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes the `TestScript` to retrieve the nodes compliance with the  **Script** resources.</span></span> <span data-ttu-id="274a2-134">但是，在这种情况下，无论 `TestScript` 块返回什么，`SetScript` 都不会运行。</span><span class="sxs-lookup"><span data-stu-id="274a2-134">However, in this case, the `SetScript` does not run, no matter what the `TestScript` block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="274a2-135">`TestScript` 的所有输出都是其返回值的一部分。</span><span class="sxs-lookup"><span data-stu-id="274a2-135">All output from your `TestScript` is part of its return value.</span></span> <span data-ttu-id="274a2-136">PowerShell 将未压缩的输出视为非零，这意味着无论节点的状态如何，`TestScript` 都将返回 `$true`。</span><span class="sxs-lookup"><span data-stu-id="274a2-136">PowerShell interprets unsuppressed output as non-zero, which means that your `TestScript` will return `$true` regardless of your node's state.</span></span>
> <span data-ttu-id="274a2-137">这会导致不可预测的结果和误报，并导致在故障排除时出现问题。</span><span class="sxs-lookup"><span data-stu-id="274a2-137">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

### <a name="setscript"></a><span data-ttu-id="274a2-138">SetScript</span><span class="sxs-lookup"><span data-stu-id="274a2-138">SetScript</span></span>

<span data-ttu-id="274a2-139">`SetScript` 修改节点以强制执行所需的状态。</span><span class="sxs-lookup"><span data-stu-id="274a2-139">The `SetScript` modifies the node to enfore the desired state.</span></span> <span data-ttu-id="274a2-140">如果 `TestScript` 脚本块返回 `$false`，则其由 DSC 调用。</span><span class="sxs-lookup"><span data-stu-id="274a2-140">It is called by DSC if the `TestScript` script block returns `$false`.</span></span> <span data-ttu-id="274a2-141">`SetScript` 应该没有返回值。</span><span class="sxs-lookup"><span data-stu-id="274a2-141">The `SetScript` should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="274a2-142">示例</span><span class="sxs-lookup"><span data-stu-id="274a2-142">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="274a2-143">示例 1：编写使用脚本资源的示例文本</span><span class="sxs-lookup"><span data-stu-id="274a2-143">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="274a2-144">此示例测试每个节点上是否存在 `C:\TempFolder\TestFile.txt`。</span><span class="sxs-lookup"><span data-stu-id="274a2-144">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="274a2-145">如果它不存在，则使用 `SetScript` 创建它。</span><span class="sxs-lookup"><span data-stu-id="274a2-145">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="274a2-146">`GetScript` 返回文件的内容，并且不使用其返回值。</span><span class="sxs-lookup"><span data-stu-id="274a2-146">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

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

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="274a2-147">示例 2：使用脚本资源的版本信息进行比较</span><span class="sxs-lookup"><span data-stu-id="274a2-147">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="274a2-148">此示例从创作计算机上的文本文件中检索符合的版本信息，并将其存储在 `$version` 变量中。</span><span class="sxs-lookup"><span data-stu-id="274a2-148">This example retrieves the *compliant* version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="274a2-149">在生成节点的 MOF 文件时，DSC 将每个脚本块中的 `$using:version` 变量替换为 `$version` 变量的值。</span><span class="sxs-lookup"><span data-stu-id="274a2-149">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span> <span data-ttu-id="274a2-150">在执行期间，符合的版本存储在每个节点上的文本文件中，并在后续执行时进行比较和更新。</span><span class="sxs-lookup"><span data-stu-id="274a2-150">During execution, the *compliant* version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

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