---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: "库,powershell,cmdlet,psgallery"
title: psgalleryint_status
ms.openlocfilehash: 0b2f1ebcb365fcd24438a028a9c8181449266a8b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2017
---
<a name="powershell-gallery-status"></a><span data-ttu-id="dc995-103">PowerShell 库状态</span><span class="sxs-lookup"><span data-stu-id="dc995-103">PowerShell Gallery Status</span></span>
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="dc995-104">2017/03/27/ - 已解决：无法查看单个模块和脚本页面</span><span class="sxs-lookup"><span data-stu-id="dc995-104">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="dc995-105">__影响摘要__：指向 https://www.powershellgallery.com 上单个模块和脚本页面的直接链接已中断。</span><span class="sxs-lookup"><span data-stu-id="dc995-105">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="dc995-106">所有区域中均报告发生此问题。</span><span class="sxs-lookup"><span data-stu-id="dc995-106">This was being reported across all the regions.</span></span> <span data-ttu-id="dc995-107">这不会影响任意 PowerShellGet cmdlet（即 Install-Module、Install-Script、Update-Module、Update-Script、Publish-Module 和 Publish-Script）继续运行。</span><span class="sxs-lookup"><span data-stu-id="dc995-107">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script continued to work.</span></span>

<span data-ttu-id="dc995-108">__根本原因__：工程师确定原因是将类似 Facebook 的社交媒体按钮设置在了页面上。</span><span class="sxs-lookup"><span data-stu-id="dc995-108">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>  

<span data-ttu-id="dc995-109">__解决__：工程师已通过禁用 Facebook 计数信息修复了此问题。</span><span class="sxs-lookup"><span data-stu-id="dc995-109">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="dc995-110">__后续步骤__：已打开内部跟踪，跟踪 Facebook API 使用情况修复问题。</span><span class="sxs-lookup"><span data-stu-id="dc995-110">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="dc995-111">2016/12/15 - 无法通过 PowerShellGallery 网站发送电子邮件</span><span class="sxs-lookup"><span data-stu-id="dc995-111">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="dc995-112">__影响摘要__：在 2016/12/13 到 2016/12/15 之间，PowerShell 库管理员未收到通过“联系所有者”、“管理所有者”、“联系支持人员”或“举报不良信息”发送的任何邮件。</span><span class="sxs-lookup"><span data-stu-id="dc995-112">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>  
<span data-ttu-id="dc995-113">__根本原因__：工程师已确定原因是 SMTP 服务器身份验证问题。</span><span class="sxs-lookup"><span data-stu-id="dc995-113">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>  
<span data-ttu-id="dc995-114">__解决办法__：工程师能够解决身份验证问题，并恢复与 SMTP 服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="dc995-114">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>  
<span data-ttu-id="dc995-115">__后续步骤__：如果在这段时间内通过“联系所有者”、“管理所有者”、“联系支持人员”或“举报不良信息”链接向 cgadmin@microsoft.com 发送了邮件，而我们未回复，请重试。</span><span class="sxs-lookup"><span data-stu-id="dc995-115">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="dc995-116">由此造成的不便，我们深表歉意。</span><span class="sxs-lookup"><span data-stu-id="dc995-116">We apologize for the inconvenience.</span></span>   


## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="dc995-117">2016/8/10 - 已解决：无法将电子邮件发送到 cgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="dc995-117">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>
<span data-ttu-id="dc995-118">__影响摘要__：2016/8/5 - 2016/8/10 期间，客户无法将电子邮件发送到 cgadmin@microsoft.com，也无法使用“联系我们”功能。</span><span class="sxs-lookup"><span data-stu-id="dc995-118">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>  
<span data-ttu-id="dc995-119">__根本原因__：工程师确定原因为电子邮件帐户的配置更改。</span><span class="sxs-lookup"><span data-stu-id="dc995-119">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>  
<span data-ttu-id="dc995-120">__解决办法__：工程师努力解决了配置问题。</span><span class="sxs-lookup"><span data-stu-id="dc995-120">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>  
<span data-ttu-id="dc995-121">后续步骤：如果在此期间使用了“联系我们”链接或向 cgadmin@microsoft.com 发送了电子邮件，但我们没有回复，请重试。</span><span class="sxs-lookup"><span data-stu-id="dc995-121">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="dc995-122">感谢你的耐心等待。</span><span class="sxs-lookup"><span data-stu-id="dc995-122">Thank you for your patience.</span></span>


