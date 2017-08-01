---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "本指南中使用的主要概念"
ms.technology: powershell
ms.openlocfilehash: 873ab19fdf43ec4ac41cc546aa94b64fbc607984
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-CN
---
# <a name="key-concepts-used-throughout-this-guide"></a><span data-ttu-id="439de-103">本指南中使用的主要概念</span><span class="sxs-lookup"><span data-stu-id="439de-103">Key Concepts Used Throughout This Guide</span></span>
<span data-ttu-id="439de-104">**JEA 具体是什么？**</span><span class="sxs-lookup"><span data-stu-id="439de-104">**What exactly is JEA?**</span></span>

<span data-ttu-id="439de-105">JEA 是 PowerShell [受约束的终结点](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx)的扩展，它添加了角色定义、虚拟帐户和多项其他改进，让你能够更轻松地锁定管理终结点。</span><span class="sxs-lookup"><span data-stu-id="439de-105">JEA is an extension of PowerShell [constrained endpoints](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx) that adds in role definitions, virtual accounts, and several other improvements to make it even easier to lock down your management endpoints.</span></span>
<span data-ttu-id="439de-106">JEA 终结点由一个 PowerShell 会话配置文件和一个或多个角色功能文件组成。</span><span class="sxs-lookup"><span data-stu-id="439de-106">A JEA endpoint consists of a PowerShell Session Configuration file and one or more Role Capability files.</span></span>

<span data-ttu-id="439de-107">**会话配置文件和角色功能文件是什么？**</span><span class="sxs-lookup"><span data-stu-id="439de-107">**What are Session Configuration and Role Capability files?**</span></span>

<span data-ttu-id="439de-108">PowerShell 会话配置文件 (.pssc) 定义可连接到 PowerShell 终结点的*人员*及其配置*方式*。</span><span class="sxs-lookup"><span data-stu-id="439de-108">PowerShell Session Configuration files (.pssc) define *who* can connect to a PowerShell endpoint and *how* it is configured.</span></span>
<span data-ttu-id="439de-109">在该文件中，你可以将用户和安全组映射到特定管理角色，并配置虚拟帐户和脚本策略等全局设置。</span><span class="sxs-lookup"><span data-stu-id="439de-109">This is where you would map users and security groups to specific management roles and configure global settings like virtual accounts and transcription policies.</span></span>
<span data-ttu-id="439de-110">会话配置文件特定于每台计算机，让你能够根据需要按计算机控制访问权限。</span><span class="sxs-lookup"><span data-stu-id="439de-110">Session configuration files are specific to each machine, which allows you to control access on a per-machine basis if desired.</span></span>

<span data-ttu-id="439de-111">PowerShell 角色功能文件 (.psrc) 定义属于某个角色的用户能够在系统上执行的*操作*。</span><span class="sxs-lookup"><span data-stu-id="439de-111">PowerShell Role Capability files (.psrc) define *what* users belonging to a role are able to do on the system.</span></span>
<span data-ttu-id="439de-112">在该文件中，你可以限制用户在其 JEA 会话中使用的 cmdlet、函数、提供程序和外部提供程序。</span><span class="sxs-lookup"><span data-stu-id="439de-112">Here, you can restrict which cmdlets, functions, providers, and external programs a user may use in their JEA session.</span></span>
<span data-ttu-id="439de-113">角色功能文件对于身为服务对象的角色（DNS 域、1 级技术支持人员、只读清单审核等）常是通用的，这些文件属于 PowerShell 模块，让你能够在你的环境中以及与他人进行共享。</span><span class="sxs-lookup"><span data-stu-id="439de-113">Role Capability files are often generic for the role being served (DNS admin, level 1 helpdesk, read-only inventory auditing, etc.) and belong to PowerShell modules, making it easy to share them across your environment and with others.</span></span>

<span data-ttu-id="439de-114">**JEA 如何利用虚拟帐户？**</span><span class="sxs-lookup"><span data-stu-id="439de-114">**How does JEA leverage virtual accounts?**</span></span>

<span data-ttu-id="439de-115">在 PowerShell 会话配置文件中，你可以将 JEA 会话配置为使用虚拟的“运行方式”帐户。</span><span class="sxs-lookup"><span data-stu-id="439de-115">In the PowerShell Session Configuration file, you can configure JEA sessions to use virtual "run as" accounts.</span></span>
<span data-ttu-id="439de-116">虚拟帐户是一次性特权帐户，在执行用户命令的上下文中，针对特定会话中的特定连接用户而生成。</span><span class="sxs-lookup"><span data-stu-id="439de-116">Virtual accounts are one-time privileged accounts spun up for the specific connecting user in that specific session under which context the user's commands are executed.</span></span>
<span data-ttu-id="439de-117">默认情况下，虚拟帐户属于本地“管理员”安全组，但可以选择将其配置为仅属于你指定的安全组。</span><span class="sxs-lookup"><span data-stu-id="439de-117">Virtual accounts belong to the local "Administrators" security group by default, but can optionally be configured to only belong to security groups you specify.</span></span>

<span data-ttu-id="439de-118">**PowerShell 远程处理**：通过 PowerShell 远程处理，你可以针对远程计算机运行 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="439de-118">**PowerShell Remoting**: PowerShell remoting allows you to run PowerShell commands against remote machines.</span></span>
<span data-ttu-id="439de-119">你可以针对一台或多台计算机进行操作，并可使用临时或永久连接。</span><span class="sxs-lookup"><span data-stu-id="439de-119">You can operate against one or many computers, and use either temporary or persistent connections.</span></span>
<span data-ttu-id="439de-120">在此演示中，你使用交互式会话远程到本地计算机。</span><span class="sxs-lookup"><span data-stu-id="439de-120">In this demo, you remoted into your local machine with an interactive session.</span></span>
<span data-ttu-id="439de-121">JEA 通过 PowerShell 远程处理限制可用的功能。</span><span class="sxs-lookup"><span data-stu-id="439de-121">JEA restricts the functionality available through PowerShell remoting.</span></span>
<span data-ttu-id="439de-122">有关 PowerShell 远程处理的详细信息，请运行 `Get-Help about_Remote`。</span><span class="sxs-lookup"><span data-stu-id="439de-122">For more information about PowerShell remoting, run `Get-Help about_Remote`.</span></span>

<span data-ttu-id="439de-123">**“运行方式”用户**：使用 JEA 时，非管理员的“运行方式”有为特权的“虚拟帐户”。</span><span class="sxs-lookup"><span data-stu-id="439de-123">**"RunAs" User**: When using JEA, a non-administrator "runs as" a privileged "Virtual Account."</span></span>
<span data-ttu-id="439de-124">虚拟帐户仅在远程会话期间存在。</span><span class="sxs-lookup"><span data-stu-id="439de-124">The Virtual Account only lasts the duration of the remote session.</span></span>
<span data-ttu-id="439de-125">也就是说，用户连接到终结点时创建此用户，用户结束会话时销毁它。</span><span class="sxs-lookup"><span data-stu-id="439de-125">That is to say, it is created when a user connects to the endpoint, and destroyed when the user ends the session.</span></span>
<span data-ttu-id="439de-126">默认情况下，虚拟帐户是本地“管理员”组的成员。</span><span class="sxs-lookup"><span data-stu-id="439de-126">By default, the Virtual Account is a member of the local Administrators group.</span></span>
<span data-ttu-id="439de-127">在域控制器上，它是“域管理员”组的成员。</span><span class="sxs-lookup"><span data-stu-id="439de-127">On a domain controller, it is a member of Domain Admins.</span></span>
<span data-ttu-id="439de-128">虚拟帐户对于在其上创建这些帐户的计算机来说是本地的，并且不拥有该计算机之外的权限。</span><span class="sxs-lookup"><span data-stu-id="439de-128">Virtual Accounts are local to the machine on which they are created, and do not have permissions outside of that machine.</span></span>
<span data-ttu-id="439de-129">这意味着它们没有在 Active Directory 中进行注册（未分配 RID）。</span><span class="sxs-lookup"><span data-stu-id="439de-129">This means that they are not registered in Active Directory (no RID is assigned).</span></span>
<span data-ttu-id="439de-130">此外，如果允许的命令/脚本尝试访问本地计算机外部的资源，它将在计算机标识（而不是虚拟帐户标识）下访问这些资源。</span><span class="sxs-lookup"><span data-stu-id="439de-130">Additionally, if an allowed command/script tries to access resources outside of the local machine, it will be accessing those resources under the machine's identity, not the Virtual Account identity.</span></span>

<span data-ttu-id="439de-131">**“已连接的”用户**：连接到 JEA 终结点并向其分配了角色的非管理员用户。</span><span class="sxs-lookup"><span data-stu-id="439de-131">**"Connected" User**: The non-administrator user who connects to the JEA endpoint and to whom roles are assigned.</span></span>
<span data-ttu-id="439de-132">此用户运行的任何命令都在运行方式用户或虚拟帐户的上下文之下运行。</span><span class="sxs-lookup"><span data-stu-id="439de-132">Any commands this user runs are run under the context of the RunAs User or virtual account.</span></span>

