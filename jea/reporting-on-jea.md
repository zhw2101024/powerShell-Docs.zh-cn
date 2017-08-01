---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "jea 报告"
ms.technology: powershell
ms.openlocfilehash: 3e7bd2755281f491bba8a905df018fb2e1cac6ff
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-CN
---
# <a name="reporting-on-jea"></a><span data-ttu-id="4f085-103">JEA 报告</span><span class="sxs-lookup"><span data-stu-id="4f085-103">Reporting on JEA</span></span>
<span data-ttu-id="4f085-104">因为 JEA 允许非特权用户在特权上下文中运行，所以日志记录和审核尤为重要。</span><span class="sxs-lookup"><span data-stu-id="4f085-104">Because JEA allows non-privileged users to run in a privileged context, logging and auditing are extremely important.</span></span>
<span data-ttu-id="4f085-105">在本节中，我们将逐一运行可用于帮助进行行日志记录和报告的工具。</span><span class="sxs-lookup"><span data-stu-id="4f085-105">In this section, we'll run through the tools you can use to help you with logging and reporting.</span></span>

## <a name="reporting-on-jea-actions"></a><span data-ttu-id="4f085-106">报告 JEA 操作</span><span class="sxs-lookup"><span data-stu-id="4f085-106">Reporting on JEA Actions</span></span>
### <a name="over-the-shoulder-transcription"></a><span data-ttu-id="4f085-107">即时权限提升脚本</span><span class="sxs-lookup"><span data-stu-id="4f085-107">Over-the-Shoulder Transcription</span></span>
<span data-ttu-id="4f085-108">获取在 PowerShell 会话中所发生情况的摘要最快捷的方法之一，是通过即时权限提升查看进行键入的用户。</span><span class="sxs-lookup"><span data-stu-id="4f085-108">One of the quickest ways to get a summary of what's happening in a PowerShell session is to look over the shoulder of the person typing.</span></span>
<span data-ttu-id="4f085-109">查看其命令、这些命令的输出是否一切正常。</span><span class="sxs-lookup"><span data-stu-id="4f085-109">You see their commands, the output of those commands, and all is well.</span></span>
<span data-ttu-id="4f085-110">或者并非一切正常，但至少你了解情况。</span><span class="sxs-lookup"><span data-stu-id="4f085-110">Or it's not, but at least you'll know.</span></span>
<span data-ttu-id="4f085-111">PowerShell 脚本旨在出现问题后，给予你类似的视图。</span><span class="sxs-lookup"><span data-stu-id="4f085-111">PowerShell transcription is designed to give you a similar view after the fact.</span></span>

<span data-ttu-id="4f085-112">在会话配置中使用“TranscriptDirectory”字段时，PowerShell 将自动记录给定会话中执行的所有操作的脚本。</span><span class="sxs-lookup"><span data-stu-id="4f085-112">When using the "TranscriptDirectory" field in your Session Configuration, PowerShell will automatically record a transcript of all actions taken in a given session.</span></span>
<span data-ttu-id="4f085-113">可在以下位置找到你执行本文档中的会话所生成的脚本：“$env:ProgramData\JEAConfiguration\Transcripts”</span><span class="sxs-lookup"><span data-stu-id="4f085-113">You can find transcripts from your sessions in this document here: "$env:ProgramData\JEAConfiguration\Transcripts"</span></span>

<span data-ttu-id="4f085-114">显而易见，该脚本记录了有关“已连接的”用户、“运行方式”用户、会话中运行的命令等的信息。</span><span class="sxs-lookup"><span data-stu-id="4f085-114">As you can tell, the transcript records information about the "Connected" user, the "Run As" user, the commands run in the session, and more.</span></span>
<span data-ttu-id="4f085-115">有关 PowerShell 脚本的详细信息，请参阅这篇[博客文章](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4f085-115">For more information about PowerShell transcription, check out [this blog post](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span></span>

### <a name="powershell-event-logs"></a><span data-ttu-id="4f085-116">PowerShell 事件日志</span><span class="sxs-lookup"><span data-stu-id="4f085-116">PowerShell Event Logs</span></span>
<span data-ttu-id="4f085-117">在模块日志记录处于打开状态时，所有的 PowerShell 操作也会记录在常规的 Windows 事件日志中。</span><span class="sxs-lookup"><span data-stu-id="4f085-117">When you have module logging turned on, all PowerShell actions are also recorded in regular Windows Event logs.</span></span>
<span data-ttu-id="4f085-118">与脚本相比，处理这种日志稍显复杂，但是它提供的详细信息级别可能有用。</span><span class="sxs-lookup"><span data-stu-id="4f085-118">This is slightly messier to deal with when compared to transcripts, but the level of detail it gives you can be useful.</span></span>

<span data-ttu-id="4f085-119">在“PowerShell”运行日志中，如果你启用了模块日志记录，事件 ID 4104 将记录调用的每个命令。</span><span class="sxs-lookup"><span data-stu-id="4f085-119">In the "PowerShell" operational log, Event ID 4104 will record each command invoked if you have enabled module logging.</span></span>

### <a name="other-event-logs"></a><span data-ttu-id="4f085-120">其他事件日志</span><span class="sxs-lookup"><span data-stu-id="4f085-120">Other Event Logs</span></span>
<span data-ttu-id="4f085-121">与 PowerShell 日志和脚本不同，其他日志记录机制将不会捕获“已连接的用户”。</span><span class="sxs-lookup"><span data-stu-id="4f085-121">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the "Connected User".</span></span>
<span data-ttu-id="4f085-122">你需要在其他日志和 PowerShell 日志之间进行一些关联操作，以匹配所执行的操作。</span><span class="sxs-lookup"><span data-stu-id="4f085-122">You will need to do some correlation between other logs and PowerShell logs to match up actions taken.</span></span>

<span data-ttu-id="4f085-123">在“Windows 远程管理”运行日志中，事件 ID 193 将记录连接用户的 SID 和名称，以及运行方式虚拟帐户的 SID，来帮助进行此关联。</span><span class="sxs-lookup"><span data-stu-id="4f085-123">In the "Windows Remote Management" operational log, Event ID 193 will record the Connecting User's SID and Name, as well as the RunAs Virtual Account's SID to assist with this correlation.</span></span>
<span data-ttu-id="4f085-124">你可能也注意到了运行方式虚拟帐户末尾包含连接用户的域和用户名。</span><span class="sxs-lookup"><span data-stu-id="4f085-124">You may have also noticed that the name of the RunAs Virtual Account includes the connecting user's domain and username at the end.</span></span>

## <a name="reporting-on-jea-configuration"></a><span data-ttu-id="4f085-125">报告 JEA 配置</span><span class="sxs-lookup"><span data-stu-id="4f085-125">Reporting on JEA Configuration</span></span>
### <a name="get-pssessionconfiguration"></a><span data-ttu-id="4f085-126">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="4f085-126">Get-PSSessionConfiguration</span></span>
<span data-ttu-id="4f085-127">为了准确报告你的环境状态，了解在计算机上设置的 JEA 终结点数量很重要。</span><span class="sxs-lookup"><span data-stu-id="4f085-127">In order to accurately report on the state of your environment, it's important to know how many JEA endpoints you have set up on your machine.</span></span>
<span data-ttu-id="4f085-128">`Get-PSSessionConfiguration` 则可达到此目的。</span><span class="sxs-lookup"><span data-stu-id="4f085-128">`Get-PSSessionConfiguration` does just that.</span></span>

### <a name="get-pssessioncapability"></a><span data-ttu-id="4f085-129">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="4f085-129">Get-PSSessionCapability</span></span>
<span data-ttu-id="4f085-130">通过 JEA 终结点手动报告任意给定用户的功能可能相当复杂。</span><span class="sxs-lookup"><span data-stu-id="4f085-130">Manually reporting on the capabilities of any given user through a JEA endpoint can be quite complex.</span></span>
<span data-ttu-id="4f085-131">你可能需要检查多个角色功能。</span><span class="sxs-lookup"><span data-stu-id="4f085-131">You would potentially need to inspect several role capabilities.</span></span>
<span data-ttu-id="4f085-132">幸运的是，“Get-PSSessionCapability”cmdlet 可完成此操作。</span><span class="sxs-lookup"><span data-stu-id="4f085-132">Fortunately, the "Get-PSSessionCapability" cmdlet does this.</span></span>

<span data-ttu-id="4f085-133">若要进行验证，请从管理员 PowerShell 提示符运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="4f085-133">To test this out, run the following command from an administrator PowerShell prompt:</span></span>
```PowerShell
Get-PSSessionCapability -Username 'CONTOSO\OperatorUser' -ConfigurationName JEADemo
```

