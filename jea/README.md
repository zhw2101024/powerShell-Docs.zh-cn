---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "自述文件"
ms.technology: powershell
ms.openlocfilehash: b0ef4ff685b82e1a4e9ab83a45736720df7b39a2
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-CN
---
# <a name="just-enough-administration"></a><span data-ttu-id="be0cd-103">Just Enough Administration</span><span class="sxs-lookup"><span data-stu-id="be0cd-103">Just Enough Administration</span></span>
<span data-ttu-id="be0cd-104">Just Enough Administration (JEA) 是一项安全技术，委派的管理员可通过它执行可通过 PowerShell 处理的任意操作。</span><span class="sxs-lookup"><span data-stu-id="be0cd-104">Just Enough Administration (JEA) is a security technology that enables delegated administration for anything that can be managed with PowerShell.</span></span>
<span data-ttu-id="be0cd-105">使用 JEA，你可以：</span><span class="sxs-lookup"><span data-stu-id="be0cd-105">With JEA, you can:</span></span>
- <span data-ttu-id="be0cd-106">通过利用代表普通用户执行特权操作的虚拟帐户，**减少你计算机上的管理员数量**。</span><span class="sxs-lookup"><span data-stu-id="be0cd-106">**Reduce the number of administrators on your machines** by leveraging virtual accounts that perform privileged actions on behalf of regular users.</span></span>
- <span data-ttu-id="be0cd-107">通过指定用户可运行的 cmdlet、函数和外部命令，**限制用户可执行的操作**。</span><span class="sxs-lookup"><span data-stu-id="be0cd-107">**Limit what users can do** by specifying which cmdlets, functions, and external commands they can run.</span></span>
- <span data-ttu-id="be0cd-108">使用准确显示用户在会话中所执行命令的“即时权限提升”脚本，**更好地了解你的用户进行的操作**。</span><span class="sxs-lookup"><span data-stu-id="be0cd-108">**Better understand what your users are doing** with "over the shoulder" transcriptions that show you exactly what commands a user executed during a session.</span></span>

<span data-ttu-id="be0cd-109">**为什么这很重要？**</span><span class="sxs-lookup"><span data-stu-id="be0cd-109">**Why is this important?**</span></span>  
<span data-ttu-id="be0cd-110">请考虑你的 DNS 服务器与 Active Directory 域控制器位于同一位置这样的常见场景。</span><span class="sxs-lookup"><span data-stu-id="be0cd-110">Consider the common scenario where your DNS servers are co-located with your Active Directory Domain Controllers.</span></span>
<span data-ttu-id="be0cd-111">你的 DNS 管理员需要拥有本地管理员特权才能解决有关 DNS 服务器的问题，但是为了实现这一点，必须使其成为拥有高度特权的“域管理员”组的成员。</span><span class="sxs-lookup"><span data-stu-id="be0cd-111">Your DNS administrators need to have local administrator privileges to fix issues with the DNS server, but in order to do so you have to make them members of the highly privileged "Domain Admins" security group.</span></span>
<span data-ttu-id="be0cd-112">该方法将有效地给予 DNS 管理员对整个域的控制全以及对该计算机上所有资源的访问权。</span><span class="sxs-lookup"><span data-stu-id="be0cd-112">This approach effectively gives DNS Administrators control over your whole domain and access to all resources on that machine.</span></span>

<span data-ttu-id="be0cd-113">而有了 JEA，你就可以为 DNS 管理员配置角色，使其能够并且仅能够访问完成工作所需的所有命令。</span><span class="sxs-lookup"><span data-stu-id="be0cd-113">With JEA in place, you can configure a role for your DNS administrators that gives them access to all the commands they need to get their job done, but nothing more.</span></span>
<span data-ttu-id="be0cd-114">这意味着你可以提供适当的访问权限以修复中毒的 DNS 缓存，而无需无意间授予他们对 Active Directory 的权限，或授予他们浏览文件系统、运行具有潜在危险的脚本的权限。</span><span class="sxs-lookup"><span data-stu-id="be0cd-114">This means you can provide the appropriate access to repair a poisoned DNS cache without unintentionally giving them rights to Active Directory, or to browse the file system, or run potentially dangerous scripts.</span></span>
<span data-ttu-id="be0cd-115">更棒的是，将 JEA 会话配置为使用具有一次性特权的虚拟帐户时，你的 DNS 管理员可以使用*无特权*凭据连接到服务器并仍可运行特权命令。</span><span class="sxs-lookup"><span data-stu-id="be0cd-115">Better yet, when the JEA session is configured to use one-time privileged virtual accounts, your DNS administrators can connect to the server using *unprivileged* credentials and still be able to run privileged commands.</span></span>

## <a name="availability"></a><span data-ttu-id="be0cd-116">可用性</span><span class="sxs-lookup"><span data-stu-id="be0cd-116">Availability</span></span>
<span data-ttu-id="be0cd-117">JEA 正与 Windows Server 2016 同步开发，并可通过 Windows Management Framework 更新在旧版 Windows 上使用。</span><span class="sxs-lookup"><span data-stu-id="be0cd-117">JEA is being developed in parallel to Windows Server 2016, and is available on older versions of Windows through Windows Management Framework updates.</span></span>
<span data-ttu-id="be0cd-118">当前版本的 JEA 在以下平台上可用：</span><span class="sxs-lookup"><span data-stu-id="be0cd-118">The current release of JEA is available on the following platforms:</span></span>

<span data-ttu-id="be0cd-119">**Windows Server**</span><span class="sxs-lookup"><span data-stu-id="be0cd-119">**Windows Server**</span></span>
- <span data-ttu-id="be0cd-120">Windows Server 2016 Technical Preview 4 及更高版本</span><span class="sxs-lookup"><span data-stu-id="be0cd-120">Windows Server 2016 Technical Preview 4 and higher</span></span>
- <span data-ttu-id="be0cd-121">\*安装了[ Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 的 Windows Server 2012 R2、2012 和 2008 R2</span><span class="sxs-lookup"><span data-stu-id="be0cd-121">Windows Server 2012 R2, 2012, and 2008 R2\* with [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installed</span></span>

<span data-ttu-id="be0cd-122">**Windows 客户端**</span><span class="sxs-lookup"><span data-stu-id="be0cd-122">**Windows Client**</span></span>
- <span data-ttu-id="be0cd-123">安装了 11 月更新 (1511) 的 Windows 10</span><span class="sxs-lookup"><span data-stu-id="be0cd-123">Windows 10 with the November Update (1511) installed</span></span>
- <span data-ttu-id="be0cd-124">\*安装了[ Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 的 Windows 8.1、8 和 7</span><span class="sxs-lookup"><span data-stu-id="be0cd-124">Windows 8.1, 8, and 7\* with [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installed</span></span>

<span data-ttu-id="be0cd-125">\* Windows Server 2008 R2 或 Windows 7 上目前不支持在 JEA 会话中使用虚拟帐户。</span><span class="sxs-lookup"><span data-stu-id="be0cd-125">\* Support for virtual accounts in JEA sessions is currently not available on Windows Server 2008 R2 or Windows 7.</span></span>


## <a name="explore-the-experience-guide"></a><span data-ttu-id="be0cd-126">浏览体验指南</span><span class="sxs-lookup"><span data-stu-id="be0cd-126">Explore the experience guide</span></span>
<span data-ttu-id="be0cd-127">准备好了解如何创作、部署和使用你自己的 JEA 终结点了吗？</span><span class="sxs-lookup"><span data-stu-id="be0cd-127">Ready to learn how to author, deploy, and use your own JEA endpoint?</span></span>

<span data-ttu-id="be0cd-128">该指南允许你使用预构建的 JEA 终结点快速开始，让你大概了解最终用户体验；然后引导你从头重新创建终结点，以帮助解释诸如会话配置和角色功能的概念。</span><span class="sxs-lookup"><span data-stu-id="be0cd-128">This guide gets you started quickly with a pre-built JEA endpoint to get an idea of what the end-user experience is like, then walks you through recreating an endpoint from scratch to help demonstrate concepts like session configurations and Role Capabilities.</span></span>

1.  <span data-ttu-id="be0cd-129">[简介](introduction.md) </span><span class="sxs-lookup"><span data-stu-id="be0cd-129">[Introduction](introduction.md) </span></span>  
<span data-ttu-id="be0cd-130">简要了解为何应关心 JEA</span><span class="sxs-lookup"><span data-stu-id="be0cd-130">Briefly review why you should care about JEA</span></span>

2.  [<span data-ttu-id="be0cd-131">必备条件</span><span class="sxs-lookup"><span data-stu-id="be0cd-131">Prerequisites</span></span>](prerequisites.md)  
<span data-ttu-id="be0cd-132">说明如何设置你的环境</span><span class="sxs-lookup"><span data-stu-id="be0cd-132">Explains how to set up your environment</span></span>

3.  [<span data-ttu-id="be0cd-133">使用 JEA</span><span class="sxs-lookup"><span data-stu-id="be0cd-133">Using JEA</span></span>](using-jea.md)  
<span data-ttu-id="be0cd-134">帮助你从了解使用 JEA 的操作员体验开始</span><span class="sxs-lookup"><span data-stu-id="be0cd-134">Helps you start by understanding the operator experience of using JEA</span></span>

4.  [<span data-ttu-id="be0cd-135">重新创建演示</span><span class="sxs-lookup"><span data-stu-id="be0cd-135">Remake the Demo</span></span>](remake-the-demo-endpoint.md)  
<span data-ttu-id="be0cd-136">从头开始创建 JEA 会话配置</span><span class="sxs-lookup"><span data-stu-id="be0cd-136">Create a JEA Session Configuration from scratch</span></span>

5.  [<span data-ttu-id="be0cd-137">角色功能</span><span class="sxs-lookup"><span data-stu-id="be0cd-137">Role Capabilities</span></span>](role-capabilities.md)  
<span data-ttu-id="be0cd-138">了解如何使用角色功能文件自定义 JEA 功能</span><span class="sxs-lookup"><span data-stu-id="be0cd-138">Learn about how to customize JEA capabilities with Role Capability Files</span></span>

6.  [<span data-ttu-id="be0cd-139">端到端 - Active Directory</span><span class="sxs-lookup"><span data-stu-id="be0cd-139">End to End - Active Directory</span></span>](end-to-end---active-directory.md)  
<span data-ttu-id="be0cd-140">创建用于管理 Active Directory 的全新的终结点</span><span class="sxs-lookup"><span data-stu-id="be0cd-140">Make a whole new endpoint for managing Active Directory</span></span>

7.  [<span data-ttu-id="be0cd-141">多计算机部署和维护</span><span class="sxs-lookup"><span data-stu-id="be0cd-141">Multi-machine Deployment and Maintenance</span></span>](multi-machine-deployment-and-maintenance.md)  
<span data-ttu-id="be0cd-142">了解部署和创作如何随缩放进行更改</span><span class="sxs-lookup"><span data-stu-id="be0cd-142">Discover how deployment and authoring changes with scale</span></span>

8.  [<span data-ttu-id="be0cd-143">JEA 报告</span><span class="sxs-lookup"><span data-stu-id="be0cd-143">Reporting on JEA</span></span>](reporting-on-jea.md)  
<span data-ttu-id="be0cd-144">了解如何审核和报告所有 JEA 操作和基础结构</span><span class="sxs-lookup"><span data-stu-id="be0cd-144">Discover how to audit and report on all JEA actions and infrastructure</span></span>

9.  <span data-ttu-id="be0cd-145">附录</span><span class="sxs-lookup"><span data-stu-id="be0cd-145">Appendixes</span></span>
  - [<span data-ttu-id="be0cd-146">本指南中使用的主要概念</span><span class="sxs-lookup"><span data-stu-id="be0cd-146">Key Concepts Used Throughout This Guide</span></span>](key-concepts-used-throughout-this-guide.md)  
  -  [<span data-ttu-id="be0cd-147">创建域控制器</span><span class="sxs-lookup"><span data-stu-id="be0cd-147">Creating a Domain Controller</span></span>](creating-a-domain-controller.md)  
  -  [<span data-ttu-id="be0cd-148">关于列入黑名单</span><span class="sxs-lookup"><span data-stu-id="be0cd-148">On Blacklisting</span></span>](on-blacklisting.md)  
  -  [<span data-ttu-id="be0cd-149">限制命令时的注意事项</span><span class="sxs-lookup"><span data-stu-id="be0cd-149">Considerations When Limiting Commands</span></span>](considerations-when-limiting-commands.md)  
  -  [<span data-ttu-id="be0cd-150">角色功能的常见问题</span><span class="sxs-lookup"><span data-stu-id="be0cd-150">Common Role Capability Pitfalls</span></span>](common-role-capability-pitfalls.md)

## <a name="start-authoring-your-own-jea-endpoints"></a><span data-ttu-id="be0cd-151">开始创作你自己的 JEA 终结点</span><span class="sxs-lookup"><span data-stu-id="be0cd-151">Start authoring your own JEA endpoints</span></span>
<span data-ttu-id="be0cd-152">创作 JEA 终结点很容易 -- 仅需启用了 JEA 的系统和文件编辑器（如 PowerShell ISE）。</span><span class="sxs-lookup"><span data-stu-id="be0cd-152">It's easy to author a JEA endpoint -- all you need is a JEA-enabled system and a text editor (like PowerShell ISE).</span></span>
<span data-ttu-id="be0cd-153">使用不带任何其他参数的 [`New-PSRoleCapabilityFile -Path <path>`](https://technet.microsoft.com/library/mt631422.aspx) 和 [`New-PSSessionConfigurationFile -Path <Path>`](https://technet.microsoft.com/library/mt631422.aspx) 创建主干文件，此技巧对于初学者而言尤为有用。</span><span class="sxs-lookup"><span data-stu-id="be0cd-153">One helpful tip to get started is to create skeleton files using [`New-PSRoleCapabilityFile -Path <path>`](https://technet.microsoft.com/library/mt631422.aspx) and [`New-PSSessionConfigurationFile -Path <Path>`](https://technet.microsoft.com/library/mt631422.aspx) without any other arguments.</span></span>
<span data-ttu-id="be0cd-154">这些主干文件包含所有适用的配置字段，以及解释每个字段用途的有益注释。</span><span class="sxs-lookup"><span data-stu-id="be0cd-154">These skeleton files contain all of the applicable configuration fields along with helpful comments to explain what each field can be used for.</span></span>

<span data-ttu-id="be0cd-155">若要更轻松地创作 JEA 终结点，请参阅 [JEA 工具包帮助程序](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx)，它提供可以用于创作会话配置文件和角色功能文件的 GUI。</span><span class="sxs-lookup"><span data-stu-id="be0cd-155">To make authoring JEA endpoints even easier, check out the [JEA Toolkit Helper](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx) which provides a GUI with which you can author Session Configuration and Role Capability files.</span></span>
<span data-ttu-id="be0cd-156">它甚至支持生成基于 PowerShell 日志的角色功能，直接为你提供你的用户定期运行完成其工作的命令。</span><span class="sxs-lookup"><span data-stu-id="be0cd-156">It even supports generating Role Capabilities based on PowerShell logs to start you off with the commands your users regularly run to get their jobs done.</span></span>

