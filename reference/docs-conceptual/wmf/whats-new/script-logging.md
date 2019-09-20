---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
title: 脚本跟踪和日志记录
ms.openlocfilehash: 6b7e5022cb4c974da5ddb3d670b5808dc9fb7bdc
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147797"
---
# <a name="script-tracing-and-logging"></a><span data-ttu-id="3c9a2-103">脚本跟踪和日志记录</span><span class="sxs-lookup"><span data-stu-id="3c9a2-103">Script Tracing and Logging</span></span>

<span data-ttu-id="3c9a2-104">尽管 PowerShell 已经具有 LogPipelineExecutionDetails  组策略设置用以记录 cmdlet 的调用，但 PowerShell 的脚本语言仍有多个你可能想记录和审核的功能。</span><span class="sxs-lookup"><span data-stu-id="3c9a2-104">While PowerShell already has the **LogPipelineExecutionDetails** Group Policy setting to log the invocation of cmdlets, PowerShell's scripting language has several features that you might want to log and audit.</span></span> <span data-ttu-id="3c9a2-105">新的“详细脚本跟踪”功能提供系统上的 PowerShell 脚本活动的详细跟踪和分析。</span><span class="sxs-lookup"><span data-stu-id="3c9a2-105">The new Detailed Script Tracing feature provides detailed tracking and analysis of PowerShell script activity on a system.</span></span> <span data-ttu-id="3c9a2-106">在启用详细脚本跟踪后，PowerShell 会将所有脚本块记录到 Microsoft-Windows-PowerShell/Operational  的 ETW 事件日志中。</span><span class="sxs-lookup"><span data-stu-id="3c9a2-106">After enabling detailed script tracing, PowerShell logs all script blocks to the ETW event log, **Microsoft-Windows-PowerShell/Operational**.</span></span> <span data-ttu-id="3c9a2-107">如果脚本块创建另一个脚本块（例如，调用 `Invoke-Expression`），则也会记录调用的脚本块。</span><span class="sxs-lookup"><span data-stu-id="3c9a2-107">If a script block creates another script block, for example, by calling `Invoke-Expression`, the invoked script block also logged.</span></span>

<span data-ttu-id="3c9a2-108">可以通过“打开 PowerShell 脚本块日志记录”  组策略设置（位于“管理模板” -> “Windows 组件” -> “Windows PowerShell”中）来启用日志记录。   </span><span class="sxs-lookup"><span data-stu-id="3c9a2-108">Logging is enabled through the **Turn on PowerShell Script Block Logging** Group Policy setting in **Administrative Templates** -> **Windows Components** -> **Windows PowerShell**.</span></span>

<span data-ttu-id="3c9a2-109">这些事件是：</span><span class="sxs-lookup"><span data-stu-id="3c9a2-109">The events are:</span></span>

| <span data-ttu-id="3c9a2-110">通道</span><span class="sxs-lookup"><span data-stu-id="3c9a2-110">Channel</span></span> |                               <span data-ttu-id="3c9a2-111">操作</span><span class="sxs-lookup"><span data-stu-id="3c9a2-111">Operational</span></span>                               |
| ------- | ----------------------------------------------------------------------- |
| <span data-ttu-id="3c9a2-112">层次</span><span class="sxs-lookup"><span data-stu-id="3c9a2-112">Level</span></span>   | <span data-ttu-id="3c9a2-113">Verbose</span><span class="sxs-lookup"><span data-stu-id="3c9a2-113">Verbose</span></span>                                                                 |
| <span data-ttu-id="3c9a2-114">操作码</span><span class="sxs-lookup"><span data-stu-id="3c9a2-114">Opcode</span></span>  | <span data-ttu-id="3c9a2-115">创建</span><span class="sxs-lookup"><span data-stu-id="3c9a2-115">Create</span></span>                                                                  |
| <span data-ttu-id="3c9a2-116">任务</span><span class="sxs-lookup"><span data-stu-id="3c9a2-116">Task</span></span>    | <span data-ttu-id="3c9a2-117">CommandStart</span><span class="sxs-lookup"><span data-stu-id="3c9a2-117">CommandStart</span></span>                                                            |
| <span data-ttu-id="3c9a2-118">关键字</span><span class="sxs-lookup"><span data-stu-id="3c9a2-118">Keyword</span></span> | <span data-ttu-id="3c9a2-119">Runspace</span><span class="sxs-lookup"><span data-stu-id="3c9a2-119">Runspace</span></span>                                                                |
| <span data-ttu-id="3c9a2-120">EventId</span><span class="sxs-lookup"><span data-stu-id="3c9a2-120">EventId</span></span> | <span data-ttu-id="3c9a2-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span><span class="sxs-lookup"><span data-stu-id="3c9a2-121">Engine_ScriptBlockCompiled (0x1008 = 4104)</span></span>                              |
| <span data-ttu-id="3c9a2-122">消息</span><span class="sxs-lookup"><span data-stu-id="3c9a2-122">Message</span></span> | <span data-ttu-id="3c9a2-123">创建脚本块文本 (%1/%2)：</span><span class="sxs-lookup"><span data-stu-id="3c9a2-123">Creating Scriptblock text (%1 of %2):</span></span> </br> <span data-ttu-id="3c9a2-124">%3</span><span class="sxs-lookup"><span data-stu-id="3c9a2-124">%3</span></span> </br> <span data-ttu-id="3c9a2-125">ScriptBlock ID：%4</span><span class="sxs-lookup"><span data-stu-id="3c9a2-125">ScriptBlock ID: %4</span></span> |


<span data-ttu-id="3c9a2-126">消息中嵌入的文本是编译的脚本块的范围。</span><span class="sxs-lookup"><span data-stu-id="3c9a2-126">The text embedded in the message is the extent of the script block compiled.</span></span> <span data-ttu-id="3c9a2-127">该 ID 是脚本块生存期内保留的 GUID。</span><span class="sxs-lookup"><span data-stu-id="3c9a2-127">The ID is a GUID that is retained for the life of the script block.</span></span>

<span data-ttu-id="3c9a2-128">当启用 verbose 日志记录时，此功能将写入开始和结束标记：</span><span class="sxs-lookup"><span data-stu-id="3c9a2-128">When you enable verbose logging, the feature writes begin and end markers:</span></span>

| <span data-ttu-id="3c9a2-129">通道</span><span class="sxs-lookup"><span data-stu-id="3c9a2-129">Channel</span></span> |                                 <span data-ttu-id="3c9a2-130">操作</span><span class="sxs-lookup"><span data-stu-id="3c9a2-130">Operational</span></span>                                |
| ------- | -------------------------------------------------------------------------- |
| <span data-ttu-id="3c9a2-131">层次</span><span class="sxs-lookup"><span data-stu-id="3c9a2-131">Level</span></span>   | <span data-ttu-id="3c9a2-132">Verbose</span><span class="sxs-lookup"><span data-stu-id="3c9a2-132">Verbose</span></span>                                                                    |
| <span data-ttu-id="3c9a2-133">操作码</span><span class="sxs-lookup"><span data-stu-id="3c9a2-133">Opcode</span></span>  | <span data-ttu-id="3c9a2-134">打开/关闭</span><span class="sxs-lookup"><span data-stu-id="3c9a2-134">Open / Close</span></span>                                                               |
| <span data-ttu-id="3c9a2-135">任务</span><span class="sxs-lookup"><span data-stu-id="3c9a2-135">Task</span></span>    | <span data-ttu-id="3c9a2-136">CommandStart/CommandStop</span><span class="sxs-lookup"><span data-stu-id="3c9a2-136">CommandStart / CommandStop</span></span>                                                 |
| <span data-ttu-id="3c9a2-137">关键字</span><span class="sxs-lookup"><span data-stu-id="3c9a2-137">Keyword</span></span> | <span data-ttu-id="3c9a2-138">Runspace</span><span class="sxs-lookup"><span data-stu-id="3c9a2-138">Runspace</span></span>                                                                   |
| <span data-ttu-id="3c9a2-139">EventId</span><span class="sxs-lookup"><span data-stu-id="3c9a2-139">EventId</span></span> | <span data-ttu-id="3c9a2-140">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span><span class="sxs-lookup"><span data-stu-id="3c9a2-140">ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) /</span></span> </br> <span data-ttu-id="3c9a2-141">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span><span class="sxs-lookup"><span data-stu-id="3c9a2-141">ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106)</span></span> |
| <span data-ttu-id="3c9a2-142">消息</span><span class="sxs-lookup"><span data-stu-id="3c9a2-142">Message</span></span> | <span data-ttu-id="3c9a2-143">已开始/已完成对 ScriptBlock ID 的调用：%1</span><span class="sxs-lookup"><span data-stu-id="3c9a2-143">Started / Completed invocation of ScriptBlock ID: %1</span></span> </br> <span data-ttu-id="3c9a2-144">Runspace ID：%2</span><span class="sxs-lookup"><span data-stu-id="3c9a2-144">Runspace ID: %2</span></span> |

<span data-ttu-id="3c9a2-145">该 ID 是表示脚本块的 GUID（可以与事件 ID 0x1008 相关联），且 Runspace ID 表示该脚本块在其中运行的运行空间。</span><span class="sxs-lookup"><span data-stu-id="3c9a2-145">The ID is the GUID representing the script block (that can be correlated with event ID 0x1008), and the Runspace ID represents the runspace in which this script block was run.</span></span>

<span data-ttu-id="3c9a2-146">调用消息中的百分号表示结构化的 ETW 属性。</span><span class="sxs-lookup"><span data-stu-id="3c9a2-146">Percent signs in the invocation message represent structured ETW properties.</span></span> <span data-ttu-id="3c9a2-147">虽然它们会被消息文本中的实际值替换，但访问它们更可靠的的方式是，使用 Get-WinEvent cmdlet 检索消息，然后使用消息的  “属性”数组。</span><span class="sxs-lookup"><span data-stu-id="3c9a2-147">While they are replaced with the actual values in the message text, a more robust way to access them is to retrieve the message with the Get-WinEvent cmdlet, and then use the **Properties** array of the message.</span></span>

<span data-ttu-id="3c9a2-148">下例描述了该功能如何帮助取消对脚本进行加密和模糊化的恶意尝试：</span><span class="sxs-lookup"><span data-stu-id="3c9a2-148">Here's an example of how this functionality can help unwrap a malicious attempt to encrypt and obfuscate a script:</span></span>

```powershell
## Malware
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

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

<span data-ttu-id="3c9a2-149">运行它将生成以下日志条目：</span><span class="sxs-lookup"><span data-stu-id="3c9a2-149">Running this generates the following log entries:</span></span>

```Output
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

如果脚本块的长度超出单个事件所能支持的长度，PowerShell 会将脚本分成多个部分。 <span data-ttu-id="3c9a2-151">下面是从其日志消息中重组脚本的示例代码：</span><span class="sxs-lookup"><span data-stu-id="3c9a2-151">Here is sample code to recombine a script from its log messages:</span></span>

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } |
  Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

<span data-ttu-id="3c9a2-152">正如所有日志系统都有一个有限的保留缓存区一样，攻击此基础结构的一种方式就是，用虚假事件充斥日志以隐藏早期的证据。</span><span class="sxs-lookup"><span data-stu-id="3c9a2-152">As with all logging systems that have a limited retention buffer, one way to attack this infrastructure is to flood the log with spurious events to hide earlier evidence.</span></span> <span data-ttu-id="3c9a2-153">若要避免这种攻击，请确保具有某种形式的事件日志集合设置（即 Windows 事件转发）。</span><span class="sxs-lookup"><span data-stu-id="3c9a2-153">To protect yourself from this attack, ensure that you have some form of event log collection set up Windows Event Forwarding.</span></span> <span data-ttu-id="3c9a2-154">有关详细信息，请参阅[通过 Windows 事件日志监视发现攻击者](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm)。</span><span class="sxs-lookup"><span data-stu-id="3c9a2-154">For more information, see [Spotting the Adversary with Windows Event Log Monitoring](https://apps.nsa.gov/iaarchive/library/reports/spotting-the-adversary-with-windows-event-log-monitoring.cfm).</span></span>