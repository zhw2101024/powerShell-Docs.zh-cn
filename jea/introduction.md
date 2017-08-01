---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "简介"
ms.technology: powershell
ms.openlocfilehash: 71264d1001228249d9f2bb0f72473e9761170bf0
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-CN
---
# <a name="introduction"></a><span data-ttu-id="0445c-103">简介</span><span class="sxs-lookup"><span data-stu-id="0445c-103">Introduction</span></span>

##  <a name="motivation"></a><span data-ttu-id="0445c-104">**动机**</span><span class="sxs-lookup"><span data-stu-id="0445c-104">**Motivation**</span></span>  
<span data-ttu-id="0445c-105">当对某人授予你系统的特许访问权时，即将信任边界扩展至此人。</span><span class="sxs-lookup"><span data-stu-id="0445c-105">When you grant someone privileged access to your systems, you extend your trust boundary to that person.</span></span>
<span data-ttu-id="0445c-106">这会带来风险 -- 管理员会成为受攻击面。</span><span class="sxs-lookup"><span data-stu-id="0445c-106">This is a risk -- administrators are an attack surface.</span></span>
<span data-ttu-id="0445c-107">内部攻击和凭据盗窃真实存在并且很常见。</span><span class="sxs-lookup"><span data-stu-id="0445c-107">Insider attacks and stolen credentials are both real and common.</span></span>

##  <a name="not-a-new-problem"></a><span data-ttu-id="0445c-108">**不是新问题**</span><span class="sxs-lookup"><span data-stu-id="0445c-108">**Not a new problem**</span></span>  
<span data-ttu-id="0445c-109">你可能非常熟悉最小特权的原则，并将某种形式的基于角色的访问控制 (RBAC) 用于提供最小特权的应用程序。</span><span class="sxs-lookup"><span data-stu-id="0445c-109">You are probably very familiar with the principle of least privilege, and you might use some form of role-based access control (RBAC) with applications that provide it.</span></span>
<span data-ttu-id="0445c-110">但是，这些解决方案的有效性和可管理性常受限于其广泛性和不精确性。</span><span class="sxs-lookup"><span data-stu-id="0445c-110">However, the effectiveness and manageability of these solutions are often limited by their broad scope and imprecision.</span></span>
<span data-ttu-id="0445c-111">此外，RBAC 作用范围中存在缺口。</span><span class="sxs-lookup"><span data-stu-id="0445c-111">Furthermore, there are gaps in RBAC coverage.</span></span>
<span data-ttu-id="0445c-112">例如，在 Windows 中，特许访问权很大程度上是一个二进制开关，在将用户添加到“管理员”组时会强制你授予其不必要的权限。</span><span class="sxs-lookup"><span data-stu-id="0445c-112">For example, in Windows, privileged access is largely a binary switch, forcing you to give unnecessary permissions when adding users to the Administrators group.</span></span>

##  <a name="just-enough-administration-jea"></a><span data-ttu-id="0445c-113">**Just Enough Administration (JEA)**</span><span class="sxs-lookup"><span data-stu-id="0445c-113">**Just Enough Administration (JEA)**</span></span> 
<span data-ttu-id="0445c-114">通过 PowerShell 远程处理提供基于角色的访问控制 (RBAC) 平台。</span><span class="sxs-lookup"><span data-stu-id="0445c-114">Provides a role-based access control (RBAC) platform through PowerShell Remoting.</span></span>
<span data-ttu-id="0445c-115">它允许特定用户在服务器上执行特定管理任务，而无需授予其管理员权限。</span><span class="sxs-lookup"><span data-stu-id="0445c-115">*It allows specific users to perform specific administrative tasks on servers without giving them administrator rights.*</span></span>
<span data-ttu-id="0445c-116">这让你能够填补现有 RBAC 解决方案之间的缺口，并简化了这些设置的管理。</span><span class="sxs-lookup"><span data-stu-id="0445c-116">This allows you to fill in the gaps between your existing RBAC solutions, and simplifies management of those settings.</span></span>

