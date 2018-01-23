---
description: 
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "Web 访问 cmdlet"
ms.technology: powershell
ms.openlocfilehash: 54821c318b165461ec613678a39c4e3b500dfd0e
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="windows-powershell-web-access-cmdlets"></a><span data-ttu-id="5a2dc-103">Windows PowerShell Web 访问 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5a2dc-103">Windows PowerShell Web Access Cmdlets</span></span>

<span data-ttu-id="5a2dc-104">本参考提供所有特定于 Windows PowerShell® Web 访问 cmdlet 的 cmdlet 说明和语法。</span><span class="sxs-lookup"><span data-stu-id="5a2dc-104">This reference provides cmdlet descriptions and syntax for all Windows PowerShell® Web Access-specific cmdlets.</span></span> <span data-ttu-id="5a2dc-105">本参考按 cmdlet 开头动词的字母顺序列出了这些 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5a2dc-105">It lists the cmdlets in alphabetical order based on the verb at the beginning of the cmdlet.</span></span>

## <a name="add-pswaauthorizationruleadd-pswaauthorizationrulemd"></a>[<span data-ttu-id="5a2dc-106">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="5a2dc-106">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)

<span data-ttu-id="5a2dc-107">向 Windows PowerShell® Web 访问授权规则集添加新的授权规则。</span><span class="sxs-lookup"><span data-stu-id="5a2dc-107">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="get-pswaauthorizationruleget-pswaauthorizationrulemd"></a>[<span data-ttu-id="5a2dc-108">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="5a2dc-108">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)

<span data-ttu-id="5a2dc-109">返回一组 Windows PowerShell Web 访问的授权规则。</span><span class="sxs-lookup"><span data-stu-id="5a2dc-109">Returns a set of the Windows PowerShell Web Access authorization rules.</span></span>

## <a name="install-pswawebapplicationinstall-pswawebapplicationmd"></a>[<span data-ttu-id="5a2dc-110">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="5a2dc-110">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)

<span data-ttu-id="5a2dc-111">在 IIS 中配置 Windows PowerShell Web 访问 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="5a2dc-111">Configures the Windows PowerShell Web Access web application in IIS.</span></span>

## <a name="remove-pswaauthorizationruleremove-pswaauthorizationrulemd"></a>[<span data-ttu-id="5a2dc-112">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="5a2dc-112">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)

<span data-ttu-id="5a2dc-113">从 Windows PowerShell Web 访问删除指定授权规则。</span><span class="sxs-lookup"><span data-stu-id="5a2dc-113">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="test-pswaauthorizationruletest-pswaauthorizationrulemd"></a>[<span data-ttu-id="5a2dc-114">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="5a2dc-114">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)

<span data-ttu-id="5a2dc-115">测试授权规则，以验证某个特定用户、计算机或终结点的访问请求是否被授权。</span><span class="sxs-lookup"><span data-stu-id="5a2dc-115">Tests authorization rules to validate that a particular user, computer, endpoint access request is authorized.</span></span>

## <a name="uninstall-pswawebapplicationuninstall-pswawebapplicationmd"></a>[<span data-ttu-id="5a2dc-116">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="5a2dc-116">Uninstall-PswaWebApplication</span></span>](uninstall-pswawebapplication.md)

<span data-ttu-id="5a2dc-117">从 IIS 卸载 Windows PowerShell Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="5a2dc-117">Uninstalls the Windows PowerShell web application from IIS.</span></span>

><span data-ttu-id="5a2dc-118">**注意**：</span><span class="sxs-lookup"><span data-stu-id="5a2dc-118">**Note**:</span></span>
>
><span data-ttu-id="5a2dc-119">若要列出所有可用 cmdlet，请使用：</span><span class="sxs-lookup"><span data-stu-id="5a2dc-119">To list all the cmdlets that are available, use the:</span></span>
>
> <span data-ttu-id="5a2dc-120">`Get-Command –Module PowerShellWebAccess` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5a2dc-120">`Get-Command –Module PowerShellWebAccess` cmdlet.</span></span>

<span data-ttu-id="5a2dc-121">有关其中任何一种 cmdlet 或其语法的详细信息，请使用：</span><span class="sxs-lookup"><span data-stu-id="5a2dc-121">For more information about, or for the syntax of, any of the cmdlets, use:</span></span>  
<span data-ttu-id="5a2dc-122">`Get-Help `&lt;cmdlet 名称&gt;</span><span class="sxs-lookup"><span data-stu-id="5a2dc-122">`Get-Help `*&lt;cmdlet name&gt;*</span></span>  
<span data-ttu-id="5a2dc-123">其中 &lt;cmdlet name&gt; 是要了解的 cmdlet 的名称。</span><span class="sxs-lookup"><span data-stu-id="5a2dc-123">where *&lt;cmdlet name&gt;* is the name of the cmdlet that you want to research.</span></span>

<span data-ttu-id="5a2dc-124">有关更多详细信息，你可以运行以下任何 cmdlet：</span><span class="sxs-lookup"><span data-stu-id="5a2dc-124">For more detailed information, you can run any of the following cmdlets:</span></span>

- <span data-ttu-id="5a2dc-125">`Get-Help `&lt;cmdlet 名称&gt;` -Detailed`</span><span class="sxs-lookup"><span data-stu-id="5a2dc-125">`Get-Help `*&lt;cmdlet name&gt;*` -Detailed`</span></span>
- <span data-ttu-id="5a2dc-126">`Get-Help `&lt;cmdlet 名称&gt;` -Examples`</span><span class="sxs-lookup"><span data-stu-id="5a2dc-126">`Get-Help `*&lt;cmdlet name&gt;*` -Examples`</span></span>
- <span data-ttu-id="5a2dc-127">`Get-Help `&lt;cmdlet 名称&gt;` -Full`</span><span class="sxs-lookup"><span data-stu-id="5a2dc-127">`Get-Help `*&lt;cmdlet name&gt;*` -Full`</span></span>

### <a name="more-information"></a><span data-ttu-id="5a2dc-128">详细信息</span><span class="sxs-lookup"><span data-stu-id="5a2dc-128">More Information</span></span>

<span data-ttu-id="5a2dc-129">有关 PowerShell Web 访问的详细信息，请参阅以下内容：</span><span class="sxs-lookup"><span data-stu-id="5a2dc-129">For more information about PowerShell Web Access, see the following:</span></span>

- [<span data-ttu-id="5a2dc-130">安装和使用 Windows PowerShell Web 访问</span><span class="sxs-lookup"><span data-stu-id="5a2dc-130">Install and Use Windows PowerShell Web Access</span></span>](../install-and-use-windows-powershell-web-access.md)

