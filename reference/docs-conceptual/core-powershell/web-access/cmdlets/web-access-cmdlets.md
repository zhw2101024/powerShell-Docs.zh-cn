---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "Web 访问 cmdlet"
ms.technology: powershell
ms.openlocfilehash: daebe2fe2cbccaf8d3f41d265d23dc45d3bb99b6
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2017
---
# <a name="windows-powershell-web-access-cmdlets"></a><span data-ttu-id="9b1ef-103">Windows PowerShell Web 访问 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9b1ef-103">Windows PowerShell Web Access Cmdlets</span></span>

<span data-ttu-id="9b1ef-104">本参考提供所有特定于 Windows PowerShell® Web 访问 cmdlet 的 cmdlet 说明和语法。</span><span class="sxs-lookup"><span data-stu-id="9b1ef-104">This reference provides cmdlet descriptions and syntax for all Windows PowerShell® Web Access-specific cmdlets.</span></span> <span data-ttu-id="9b1ef-105">本参考按 cmdlet 开头动词的字母顺序列出了这些 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9b1ef-105">It lists the cmdlets in alphabetical order based on the verb at the beginning of the cmdlet.</span></span>

## <a name="add-pswaauthorizationruleadd-pswaauthorizationrulemd"></a>[<span data-ttu-id="9b1ef-106">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9b1ef-106">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)

<span data-ttu-id="9b1ef-107">向 Windows PowerShell® Web 访问授权规则集添加新的授权规则。</span><span class="sxs-lookup"><span data-stu-id="9b1ef-107">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="get-pswaauthorizationruleget-pswaauthorizationrulemd"></a>[<span data-ttu-id="9b1ef-108">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9b1ef-108">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)

<span data-ttu-id="9b1ef-109">返回一组 Windows PowerShell Web 访问的授权规则。</span><span class="sxs-lookup"><span data-stu-id="9b1ef-109">Returns a set of the Windows PowerShell Web Access authorization rules.</span></span>

## <a name="install-pswawebapplicationinstall-pswawebapplicationmd"></a>[<span data-ttu-id="9b1ef-110">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="9b1ef-110">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)

<span data-ttu-id="9b1ef-111">在 IIS 中配置 Windows PowerShell Web 访问 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="9b1ef-111">Configures the Windows PowerShell Web Access web application in IIS.</span></span>

## <a name="remove-pswaauthorizationruleremove-pswaauthorizationrulemd"></a>[<span data-ttu-id="9b1ef-112">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9b1ef-112">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)

<span data-ttu-id="9b1ef-113">从 Windows PowerShell Web 访问删除指定授权规则。</span><span class="sxs-lookup"><span data-stu-id="9b1ef-113">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="test-pswaauthorizationruletest-pswaauthorizationrulemd"></a>[<span data-ttu-id="9b1ef-114">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9b1ef-114">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)

<span data-ttu-id="9b1ef-115">测试授权规则，以验证某个特定用户、计算机或终结点的访问请求是否被授权。</span><span class="sxs-lookup"><span data-stu-id="9b1ef-115">Tests authorization rules to validate that a particular user, computer, endpoint access request is authorized.</span></span>

## <a name="uninstall-pswawebapplicationuninstall-pswawebapplicationmd"></a>[<span data-ttu-id="9b1ef-116">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="9b1ef-116">Uninstall-PswaWebApplication</span></span>](uninstall-pswawebapplication.md)

<span data-ttu-id="9b1ef-117">从 IIS 卸载 Windows PowerShell Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="9b1ef-117">Uninstalls the Windows PowerShell web application from IIS.</span></span>

><span data-ttu-id="9b1ef-118">**注意**：</span><span class="sxs-lookup"><span data-stu-id="9b1ef-118">**Note**:</span></span>
>
><span data-ttu-id="9b1ef-119">若要列出所有可用 cmdlet，请使用：</span><span class="sxs-lookup"><span data-stu-id="9b1ef-119">To list all the cmdlets that are available, use the:</span></span>
>
> <span data-ttu-id="9b1ef-120">`Get-Command –Module PowerShellWebAccess` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9b1ef-120">`Get-Command –Module PowerShellWebAccess` cmdlet.</span></span>

<span data-ttu-id="9b1ef-121">有关其中任何一种 cmdlet 或其语法的详细信息，请使用：</span><span class="sxs-lookup"><span data-stu-id="9b1ef-121">For more information about, or for the syntax of, any of the cmdlets, use:</span></span>  
<span data-ttu-id="9b1ef-122">`Get-Help `&lt;cmdlet 名称&gt;</span><span class="sxs-lookup"><span data-stu-id="9b1ef-122">`Get-Help `*&lt;cmdlet name&gt;*</span></span>  
<span data-ttu-id="9b1ef-123">其中 &lt;cmdlet name&gt; 是要了解的 cmdlet 的名称。</span><span class="sxs-lookup"><span data-stu-id="9b1ef-123">where *&lt;cmdlet name&gt;* is the name of the cmdlet that you want to research.</span></span>

<span data-ttu-id="9b1ef-124">有关更多详细信息，你可以运行以下任何 cmdlet：</span><span class="sxs-lookup"><span data-stu-id="9b1ef-124">For more detailed information, you can run any of the following cmdlets:</span></span>

- <span data-ttu-id="9b1ef-125">`Get-Help `&lt;cmdlet 名称&gt;` -Detailed`</span><span class="sxs-lookup"><span data-stu-id="9b1ef-125">`Get-Help `*&lt;cmdlet name&gt;*` -Detailed`</span></span>
- <span data-ttu-id="9b1ef-126">`Get-Help `&lt;cmdlet 名称&gt;` -Examples`</span><span class="sxs-lookup"><span data-stu-id="9b1ef-126">`Get-Help `*&lt;cmdlet name&gt;*` -Examples`</span></span>
- <span data-ttu-id="9b1ef-127">`Get-Help `&lt;cmdlet 名称&gt;` -Full`</span><span class="sxs-lookup"><span data-stu-id="9b1ef-127">`Get-Help `*&lt;cmdlet name&gt;*` -Full`</span></span>

### <a name="more-information"></a><span data-ttu-id="9b1ef-128">详细信息</span><span class="sxs-lookup"><span data-stu-id="9b1ef-128">More Information</span></span>

<span data-ttu-id="9b1ef-129">有关 PowerShell Web 访问的详细信息，请参阅以下内容：</span><span class="sxs-lookup"><span data-stu-id="9b1ef-129">For more information about PowerShell Web Access, see the following:</span></span>

- [<span data-ttu-id="9b1ef-130">安装和使用 Windows PowerShell Web 访问</span><span class="sxs-lookup"><span data-stu-id="9b1ef-130">Install and Use Windows PowerShell Web Access</span></span>](../install-and-use-windows-powershell-web-access.md)

