---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "关于列入黑名单"
ms.technology: powershell
ms.openlocfilehash: e823cc0b130500fb7ea60e65acf27f90ad3f3802
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-CN
---
### <a name="on-blacklisting"></a><span data-ttu-id="78609-103">关于列入黑名单</span><span class="sxs-lookup"><span data-stu-id="78609-103">On Blacklisting</span></span>
<span data-ttu-id="78609-104">在体验了一番 JEA 后，你可能会想知道是否可以将命令列入黑名单。</span><span class="sxs-lookup"><span data-stu-id="78609-104">After playing around with JEA, you may be wondering if it is possible to blacklist commands.</span></span>
<span data-ttu-id="78609-105">这一请求可以理解，但由于以下原因，目前未计划为 JEA 提供此功能：</span><span class="sxs-lookup"><span data-stu-id="78609-105">This is an understandable request, but it is not currently planned for JEA for the following reasons:</span></span>

1.  <span data-ttu-id="78609-106">我们对 JEA 的设计是，将操作员限制为仅能执行其所需执行的操作。</span><span class="sxs-lookup"><span data-stu-id="78609-106">We designed JEA to limit operators to only the actions they need to do.</span></span>
<span data-ttu-id="78609-107">黑名单则相反。</span><span class="sxs-lookup"><span data-stu-id="78609-107">A blacklist is the opposite.</span></span>

2.  <span data-ttu-id="78609-108">PowerShell 命令的作者在设计 PowerShell 时未考虑 JEA。</span><span class="sxs-lookup"><span data-stu-id="78609-108">PowerShell command authors did not design PowerShell commands with the JEA in mind.</span></span>
<span data-ttu-id="78609-109">在全新安装的 Windows Server 2016 上，有大约 1520 条命令立即可用。</span><span class="sxs-lookup"><span data-stu-id="78609-109">On a fresh install of Windows Server 2016, there are about 1520 commands immediately available.</span></span>
<span data-ttu-id="78609-110">这些命令的威胁模型未包括这种可能性，即用户将以更高权限的帐户身份运行命令。</span><span class="sxs-lookup"><span data-stu-id="78609-110">The threat models for these commands did not include the possibility that a user would be running commands as a more privileged account.</span></span>
<span data-ttu-id="78609-111">例如，某些命令允许通过设计注入代码（例如核心 PowerShell 模块中的 Add-Type 和 Invoke-Command）。</span><span class="sxs-lookup"><span data-stu-id="78609-111">For example, certain commands allow for code injection by design (e.g. Add-Type and Invoke-Command in the core PowerShell module).</span></span>
<span data-ttu-id="78609-112">JEA 在你公开已知特定命令时可发出警告，但是我们尚未根据新的威胁模型重新评估 Windows 中的每条命令。</span><span class="sxs-lookup"><span data-stu-id="78609-112">JEA can warn you when you expose the specific commands we know about, but we have not re-assessed every other command in Windows based on the new threat model.</span></span>
<span data-ttu-id="78609-113">请务必了解你通过 JEA 公开的命令的功能。</span><span class="sxs-lookup"><span data-stu-id="78609-113">You must understand the capabilities of the commands you exposing through JEA.</span></span>  

3.  <span data-ttu-id="78609-114">此外，即使 JEA 阻止了具有代码注入漏洞的所有命令，也不能保证恶意用户不能使用其他相关命令执行已列入黑名单的操作。</span><span class="sxs-lookup"><span data-stu-id="78609-114">Furthermore, even if JEA blocked all commands with code-injection vulnerabilities, there is no guarantee that a malicious user would not be able to carry out a blacklisted action with another related command.</span></span>
<span data-ttu-id="78609-115">如果你不了解你公开的所有命令，你将无法保证某些操作是不可能的。</span><span class="sxs-lookup"><span data-stu-id="78609-115">Unless you understand all of the commands that you are exposing, it is impossible for you to guarantee that a certain action is not possible.</span></span>
<span data-ttu-id="78609-116">你肩负了解你所公开的命令的重任，无论这些命令使用白名单还是黑名单。</span><span class="sxs-lookup"><span data-stu-id="78609-116">The burden is on you to understand what commands you are exposing, whether they are using a whitelist or a blacklist.</span></span>
<span data-ttu-id="78609-117">无法管理黑名单将公开的命令数量，因此改用白名单实现 JEA。</span><span class="sxs-lookup"><span data-stu-id="78609-117">The number of commands a blacklist would expose is unmanageable, so JEA is implemented using whitelists instead.</span></span>

