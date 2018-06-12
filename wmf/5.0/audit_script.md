---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: b8f175cee0a1de501b64890fdc2798f4f6421a14
ms.sourcegitcommit: 2ffb9fa92129c2001379ca2c17646466721f7165
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251477"
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="e8da3-102">脚本跟踪和日志记录</span><span class="sxs-lookup"><span data-stu-id="e8da3-102">Script Tracing and Logging</span></span>

<span data-ttu-id="e8da3-103">尽管 Windows PowerShell 已经具有 **LogPipelineExecutionDetails** 组策略设置用以记录 cmdlet 的调用，但 PowerShell 的脚本语言仍有许多你可能想记录和/或审核的功能。</span><span class="sxs-lookup"><span data-stu-id="e8da3-103">While Windows PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell’s scripting language has plenty of features that you might want to log and/or audit.</span></span> <span data-ttu-id="e8da3-104">新的“详细脚本跟踪”功能让你能够启用系统上使用的 Windows PowerShell 脚本的详细跟踪和分析。</span><span class="sxs-lookup"><span data-stu-id="e8da3-104">The new Detailed Script Tracing feature lets you enable detailed tracking and analysis of Windows PowerShell scripting use on a system.</span></span> <span data-ttu-id="e8da3-105">在启用详细脚本跟踪后，Windows PowerShell 会将所有脚本块记录到 **Microsoft-Windows-PowerShell/Operational** 的 ETW 事件日志中。</span><span class="sxs-lookup"><span data-stu-id="e8da3-105">After you enable detailed script tracing, Windows PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="e8da3-106">如果一个脚本块创建了另一个脚本块（例如，一个在字符串上调用 Invoke-Expression cmdlet 的脚本），那么该结果脚本块也会被记录。</span><span class="sxs-lookup"><span data-stu-id="e8da3-106">If a script block creates another script block (for example, a script that calls the Invoke-Expression cmdlet on a string), that resulting script block is logged as well.</span></span>

<span data-ttu-id="e8da3-107">可以通过**打开 PowerShell 脚本块日志记录**组策略设置（位于“管理模板”->“Windows 组件”->“Windows PowerShell”中）来启用对这些事件的记录。</span><span class="sxs-lookup"><span data-stu-id="e8da3-107">Logging of these events can be enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting (in Administrative Templates -> Windows Components -> Windows PowerShell).</span></span>

<span data-ttu-id="e8da3-108">这些事件是：</span><span class="sxs-lookup"><span data-stu-id="e8da3-108">The events are:</span></span>

| <span data-ttu-id="e8da3-109">通道</span><span class="sxs-lookup"><span data-stu-id="e8da3-109">Channel</span></span> | <span data-ttu-id="e8da3-110">操作</span><span class="sxs-lookup"><span data-stu-id="e8da3-110">Operational</span></span>                                 |
|---------|---------------------------------------------|
| <span data-ttu-id="e8da3-111">层次</span><span class="sxs-lookup"><span data-stu-id="e8da3-111">Level</span></span>   | <span data-ttu-id="e8da3-112">Verbose</span><span class="sxs-lookup"><span data-stu-id="e8da3-112">Verbose</span></span>                                     |
| <span data-ttu-id="e8da3-113">操作码</span><span class="sxs-lookup"><span data-stu-id="e8da3-113">Opcode</span></span>  | <span data-ttu-id="e8da3-114">创建</span><span class="sxs-lookup"><span data-stu-id="e8da3-114">Create</span></span>                                      |
| <span data-ttu-id="e8da3-115">任务</span><span class="sxs-lookup"><span data-stu-id="e8da3-115">Task</span></span>    | <span data-ttu-id="e8da3-116">CommandStart</span><span class="sxs-lookup"><span data-stu-id="e8da3-116">CommandStart</span></span>                                |
| <span data-ttu-id="e8da3-117">关键字</span><span class="sxs-lookup"><span data-stu-id="e8da3-117">Keyword</span></span> | <span data-ttu-id="e8da3-118">Runspace</span><span class="sxs-lookup"><span data-stu-id="e8da3-118">Runspace</span></span>                                    |
| <span data-ttu-id="e8da3-119">EventId</span><span class="sxs-lookup"><span data-stu-id="e8da3-119">EventId</span></span> | <span data-ttu-id="e8da3-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="e8da3-120">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>  |
| <span data-ttu-id="e8da3-121">消息</span><span class="sxs-lookup"><span data-stu-id="e8da3-121">Message</span></span> | <span data-ttu-id="e8da3-122">创建脚本块文本 (%1/%2)：</span><span class="sxs-lookup"><span data-stu-id="e8da3-122">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="e8da3-123">%3</span><span class="sxs-lookup"><span data-stu-id="e8da3-123">%3</span></span> </br> <span data-ttu-id="e8da3-124">ScriptBlock ID：%4</span><span class="sxs-lookup"><span data-stu-id="e8da3-124">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="e8da3-125">消息中嵌入的文本是编译的脚本块的范围。</span><span class="sxs-lookup"><span data-stu-id="e8da3-125">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="e8da3-126">该 ID 是脚本块生存期内保留的 GUID。</span><span class="sxs-lookup"><span data-stu-id="e8da3-126">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="e8da3-127">当启用 verbose 日志记录时，此功能将写入开始和结束标记：</span><span class="sxs-lookup"><span data-stu-id="e8da3-127">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="e8da3-128">通道</span><span class="sxs-lookup"><span data-stu-id="e8da3-128">Channel</span></span> | <span data-ttu-id="e8da3-129">操作</span><span class="sxs-lookup"><span data-stu-id="e8da3-129">Operational</span></span>                                            |
|---------|--------------------------------------------------------|
| <span data-ttu-id="e8da3-130">层次</span><span class="sxs-lookup"><span data-stu-id="e8da3-130">Level</span></span>   | <span data-ttu-id="e8da3-131">Verbose</span><span class="sxs-lookup"><span data-stu-id="e8da3-131">Verbose</span></span>                                                |
| <span data-ttu-id="e8da3-132">操作码</span><span class="sxs-lookup"><span data-stu-id="e8da3-132">Opcode</span></span>  | <span data-ttu-id="e8da3-133">打开（/关闭）</span><span class="sxs-lookup"><span data-stu-id="e8da3-133">Open (/ Close)</span></span>                                         |
| <span data-ttu-id="e8da3-134">任务</span><span class="sxs-lookup"><span data-stu-id="e8da3-134">Task</span></span>    | <span data-ttu-id="e8da3-135">CommandStart (/ CommandStop)</span><span class="sxs-lookup"><span data-stu-id="e8da3-135">CommandStart (/ CommandStop)</span></span>                           |
| <span data-ttu-id="e8da3-136">关键字</span><span class="sxs-lookup"><span data-stu-id="e8da3-136">Keyword</span></span> | <span data-ttu-id="e8da3-137">Runspace</span><span class="sxs-lookup"><span data-stu-id="e8da3-137">Runspace</span></span>                                               |
| <span data-ttu-id="e8da3-138">EventId</span><span class="sxs-lookup"><span data-stu-id="e8da3-138">EventId</span></span> | <span data-ttu-id="e8da3-139">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="e8da3-139">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="e8da3-140">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="e8da3-140">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="e8da3-141">消息</span><span class="sxs-lookup"><span data-stu-id="e8da3-141">Message</span></span> | <span data-ttu-id="e8da3-142">已开始（/已完成）对 ScriptBlock ID 的调用：%1</span><span class="sxs-lookup"><span data-stu-id="e8da3-142">Started (/ Completed) invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="e8da3-143">Runspace ID：%2</span><span class="sxs-lookup"><span data-stu-id="e8da3-143">Runspace ID: %2</span></span> |

<span data-ttu-id="e8da3-144">该 ID 是表示脚本块的 GUID（可以与事件 ID 0x1008 相关联），且 Runspace ID 表示该脚本块在其中运行的运行空间。</span><span class="sxs-lookup"><span data-stu-id="e8da3-144">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="e8da3-145">调用消息中的百分号表示结构化的 ETW 属性。</span><span class="sxs-lookup"><span data-stu-id="e8da3-145">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="e8da3-146">虽然它们会被消息文本中的实际值替换，但访问它们更可靠的的方式是，使用 Get-WinEvent cmdlet 检索消息，然后使用消息的“属性”数组。</span><span class="sxs-lookup"><span data-stu-id="e8da3-146">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="e8da3-147">下例描述了该功能如何帮助取消对脚本进行加密和模糊化的恶意尝试：</span><span class="sxs-lookup"><span data-stu-id="e8da3-147">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)

    ## XOR “encryption”
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)
}

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

<span data-ttu-id="e8da3-148">运行它将生成以下日志条目：</span><span class="sxs-lookup"><span data-stu-id="e8da3-148">Running this generates the following log entries:</span></span>

```
Compiling Scriptblock text (1 of 1):
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)
    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)

}
ScriptBlock ID: ad8ae740-1f33-42aa-8dfc-1314411877e3

Compiling Scriptblock text (1 of 1):
$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
ScriptBlock ID: ba11c155-d34c-4004-88e3-6502ecb50f52

Compiling Scriptblock text (1 of 1):
Invoke-Expression $decrypted
ScriptBlock ID: 856c01ca-85d7-4989-b47f-e6a09ee4eeb3

Compiling Scriptblock text (1 of 1):
Write-Host 'Pwnd'
ScriptBlock ID: 5e618414-4e77-48e3-8f65-9a863f54b4c8
```

如果脚本块的长度超出 ETW 在单个事件中所能支持的长度，Windows PowerShell 会将脚本分成多个部分。 <span data-ttu-id="e8da3-150">下面是从其日志消息中重组脚本的示例代码：</span><span class="sxs-lookup"><span data-stu-id="e8da3-150">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="e8da3-151">正如所有日志系统都有一个有限的保留缓存区（即 ETW 日志）一样，针对此基础结构的一个攻击就是，用虚假事件充斥日志以隐藏早期的证据。</span><span class="sxs-lookup"><span data-stu-id="e8da3-151">As with all logging systems that have a limited retention buffer (i.e. ETW logs), one attack against this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="e8da3-152">若要避免这种攻击，请确保具有某种形式的事件日志集合设置（即 Windows 事件转发，[通过 Windows 事件日志监视发现攻击者](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)）以尽快将事件日志从计算机中移除。</span><span class="sxs-lookup"><span data-stu-id="e8da3-152">To protect yourself from this attack, ensure that you have some form of event log collection set up (i.e., Windows Event Forwarding, [Spotting the Adversary with Windows Event Log Monitoring](https://www.iad.gov/iad/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)) to move event logs off of the computer as soon as possible.</span></span>
