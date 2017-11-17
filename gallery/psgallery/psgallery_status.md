---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: "库,powershell,cmdlet,psgallery"
title: psgallery_status
ms.openlocfilehash: af6111d3c511273571bd978c6d0e7447726c2917
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/13/2017
---
<a name="powershell-gallery-status"></a><span data-ttu-id="803ec-103">PowerShell 库状态</span><span class="sxs-lookup"><span data-stu-id="803ec-103">PowerShell Gallery Status</span></span>
=========================
## <a name="10102017---powershell-gallery-unavailable-for-2-hours-101017"></a><span data-ttu-id="803ec-104">2017 年 10 月 10 日 - PowerShell 库在 2017 年 10 月 10 日有两小时不可用</span><span class="sxs-lookup"><span data-stu-id="803ec-104">10/10/2017 - PowerShell Gallery unavailable for 2 hours 10/10/17</span></span>

<span data-ttu-id="803ec-105">__影响摘要__：PowerShell 库遇到了一段时间的高延迟，这导致大约从 2017 年 10 月 10 日下午 5 点（太平洋夏令时）开始出现间歇性连接问题。</span><span class="sxs-lookup"><span data-stu-id="803ec-105">__Summary of Impact__: The PowerShell Gallery experienced a period of very high latency, resulting in intermittent connection issues, beginning approximately 5pm (PDT) 10/10/17.</span></span> <span data-ttu-id="803ec-106">解决问题时，站点大约从晚上 10 点（太平洋夏令时）开始脱机达 2 小时。</span><span class="sxs-lookup"><span data-stu-id="803ec-106">While resolving the issue, the site was taken offline for 2 hours starting approximately 10pm (PDT).</span></span> <span data-ttu-id="803ec-107">站点已于 2017 年 10 月 10 日午夜前不久恢复。</span><span class="sxs-lookup"><span data-stu-id="803ec-107">The site was restored shortly before midnight 10/10/2017.</span></span> 
 
<span data-ttu-id="803ec-108">__根本原因__：高延迟的根本原因仍在调查中。</span><span class="sxs-lookup"><span data-stu-id="803ec-108">__Root Cause__: The root cause of the high latency is still being investigated.</span></span>

<span data-ttu-id="803ec-109">__解决方案__：必须使 Web 服务脱机并还原才能解决主要问题。</span><span class="sxs-lookup"><span data-stu-id="803ec-109">__Resolution__: The web services had to be taken offline and restored in order to address the primary issue.</span></span> 

<span data-ttu-id="803ec-110">__后续步骤__：正在调查原始问题的根本原因。</span><span class="sxs-lookup"><span data-stu-id="803ec-110">__Next Steps__: The root cause for the original issue is being investigated.</span></span>

## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a><span data-ttu-id="803ec-111">2017 年 6 月 1 日 - 暂无法部署到 Azure 自动化</span><span class="sxs-lookup"><span data-stu-id="803ec-111">06/01/2017 - Deploy to Azure Automation Currently Unavailable</span></span>

<span data-ttu-id="803ec-112">__影响摘要__：暂无法将包含依赖项的项从 PowerShell 库部署到 Azure 自动化。</span><span class="sxs-lookup"><span data-stu-id="803ec-112">__Summary of Impact__: Deploying items with dependencies to Azure Automation from the PowerShell Gallery is currently unavailable.</span></span>  <span data-ttu-id="803ec-113">仍可以在 Azure 自动化中从 PowerShell 库导入项。</span><span class="sxs-lookup"><span data-stu-id="803ec-113">Importing items from the PowerShell Gallery from inside Azure Automation is still available.</span></span>  
 
<span data-ttu-id="803ec-114">__根本原因__：无法将依赖其他项的项以及以前部署到 Azure 自动化的项部署到 Azure 自动化。</span><span class="sxs-lookup"><span data-stu-id="803ec-114">__Root Cause__: Items that have dependencies on others, and have been previously deployed to Azure Automation, will not be deployed to Azure Automation.</span></span> <span data-ttu-id="803ec-115">工程师已发现“部署到 Azure 自动化”功能在为包含依赖项的项生成 ARM 模板的方式上存在问题。</span><span class="sxs-lookup"><span data-stu-id="803ec-115">Engineers have identified an issue with how ARM templates are generated for items with dependencies for the Deploy to Azure Automation functionality.</span></span>

<span data-ttu-id="803ec-116">__解决方法__：工程师正在努力解决此问题。</span><span class="sxs-lookup"><span data-stu-id="803ec-116">__Resolution__: Engineers are working to resolve issue.</span></span>  <span data-ttu-id="803ec-117">用户当前可以采用的解决方法是，在 Azure 自动化中从 PowerShell 库导入项。</span><span class="sxs-lookup"><span data-stu-id="803ec-117">The current workaround for users is to import the item from the PowerShell Gallery from inside Azure Automation.</span></span> 

<span data-ttu-id="803ec-118">__后续步骤__：工程师很快将发布修补程序。</span><span class="sxs-lookup"><span data-stu-id="803ec-118">__Next Steps__: Engineers will release the fix shortly.</span></span>  <span data-ttu-id="803ec-119">在此期间，请使用建议的解决方法。</span><span class="sxs-lookup"><span data-stu-id="803ec-119">In the meantime, please use the recommended workaround.</span></span> 


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a><span data-ttu-id="803ec-120">2017/04/11 - 用户无法使用 Azure Active Directory (AAD) 帐户登录</span><span class="sxs-lookup"><span data-stu-id="803ec-120">04/11/2017 - Users unable to log in with Azure Active Directory (AAD) accounts</span></span>

<span data-ttu-id="803ec-121">__影响摘要__：某些用户无法使用 Azure AD 帐户登录到 PowerShell 库。</span><span class="sxs-lookup"><span data-stu-id="803ec-121">__Summary of Impact__: Some users were unable to log in to the PowerShell Gallery using Azure AD Accounts.</span></span> 
 
<span data-ttu-id="803ec-122">__根本原因__：在执行更新以实现与 AAD 更安全交互的过程中，缺少了某项设置更改。</span><span class="sxs-lookup"><span data-stu-id="803ec-122">__Root Cause__: During an update to interact more securely with AAD, a setting change was missed.</span></span> <span data-ttu-id="803ec-123">用于验证更改的测试未包含某些类型的 AAD 帐户，因此该部署还会继续。</span><span class="sxs-lookup"><span data-stu-id="803ec-123">The testing done to validate the change did not include certain types of AAD accounts, so the deployment proceeded.</span></span>

<span data-ttu-id="803ec-124">__解决办法__：工程师确定了缺少的设置并更正了此问题。</span><span class="sxs-lookup"><span data-stu-id="803ec-124">__Resolution__: Engineers identified the missing setting and corrected the problem.</span></span> 

<span data-ttu-id="803ec-125">__后续步骤__：我们将修改测试以包含一组更广泛的 AAD 帐户类型。</span><span class="sxs-lookup"><span data-stu-id="803ec-125">__Next Steps__: We will be modifying our testing to include a broader set of AAD account types.</span></span>

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="803ec-126">2017/03/27/ - 已解决：无法查看单个模块和脚本页面</span><span class="sxs-lookup"><span data-stu-id="803ec-126">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="803ec-127">__影响摘要__：指向 https://www.powershellgallery.com 上单个模块和脚本页面的直接链接已中断。</span><span class="sxs-lookup"><span data-stu-id="803ec-127">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="803ec-128">所有区域中均报告发生此问题。</span><span class="sxs-lookup"><span data-stu-id="803ec-128">This was being reported across all the regions.</span></span> <span data-ttu-id="803ec-129">这不会影响任意 PowerShellGet cmdlet，即 Install-Module、Install-Script、Update-Module、Update-Script、Publish-Module 和 Publish-Scirpt 继续运行。</span><span class="sxs-lookup"><span data-stu-id="803ec-129">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt continued to work.</span></span>

<span data-ttu-id="803ec-130">__根本原因__：工程师确定原因是将类似 Facebook 的社交媒体按钮设置在了页面上。</span><span class="sxs-lookup"><span data-stu-id="803ec-130">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>  

<span data-ttu-id="803ec-131">__解决__：工程师已通过禁用 Facebook 计数信息修复了此问题。</span><span class="sxs-lookup"><span data-stu-id="803ec-131">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="803ec-132">__后续步骤__：已打开内部跟踪，跟踪 Facebook API 使用情况修复问题。</span><span class="sxs-lookup"><span data-stu-id="803ec-132">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="803ec-133">2016/12/15 - 无法通过 PowerShellGallery 网站发送电子邮件</span><span class="sxs-lookup"><span data-stu-id="803ec-133">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="803ec-134">__影响摘要__：在 2016/12/13 到 2016/12/15 之间，PowerShell 库管理员未收到通过“联系所有者”、“管理所有者”、“联系支持人员”或“举报不良信息”发送的任何邮件。</span><span class="sxs-lookup"><span data-stu-id="803ec-134">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>  
<span data-ttu-id="803ec-135">__根本原因__：工程师已确定原因是 SMTP 服务器身份验证问题。</span><span class="sxs-lookup"><span data-stu-id="803ec-135">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>  
<span data-ttu-id="803ec-136">__解决办法__：工程师能够解决身份验证问题，并恢复与 SMTP 服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="803ec-136">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>  
<span data-ttu-id="803ec-137">__后续步骤__：如果在这段时间内通过“联系所有者”、“管理所有者”、“联系支持人员”或“举报不良信息”链接向 cgadmin@microsoft.com 发送了邮件，而我们未回复，请重试。</span><span class="sxs-lookup"><span data-stu-id="803ec-137">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="803ec-138">由此造成的不便，我们深表歉意。</span><span class="sxs-lookup"><span data-stu-id="803ec-138">We apologize for the inconvenience.</span></span>  



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="803ec-139">2016/8/10 - 已解决：无法将电子邮件发送到 cgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="803ec-139">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>

<span data-ttu-id="803ec-140">__影响摘要__：2016/8/5 - 2016/8/10 期间，客户无法将电子邮件发送到 cgadmin@microsoft.com，也无法使用“联系我们”功能。</span><span class="sxs-lookup"><span data-stu-id="803ec-140">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>  
<span data-ttu-id="803ec-141">__根本原因__：工程师确定原因为电子邮件帐户的配置更改。</span><span class="sxs-lookup"><span data-stu-id="803ec-141">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>  
<span data-ttu-id="803ec-142">__解决办法__：工程师努力解决了配置问题。</span><span class="sxs-lookup"><span data-stu-id="803ec-142">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>  
<span data-ttu-id="803ec-143">后续步骤：如果在此期间使用了“联系我们”链接或向 cgadmin@microsoft.com 发送了电子邮件，但我们没有回复，请重试。</span><span class="sxs-lookup"><span data-stu-id="803ec-143">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="803ec-144">感谢你的耐心等待。</span><span class="sxs-lookup"><span data-stu-id="803ec-144">Thank you for your patience.</span></span>



## <a name="7132016---download-items-failed"></a><span data-ttu-id="803ec-145">2016/7/13 - 下载项目失败</span><span class="sxs-lookup"><span data-stu-id="803ec-145">7/13/2016 - Download Items Failed</span></span>

<span data-ttu-id="803ec-146">__影响摘要__：2016/7/11 - 2016/7/13 期间，部分客户在从 PowerShell 库下载项目时遇到问题。</span><span class="sxs-lookup"><span data-stu-id="803ec-146">__Summary of Impact__: Between 7/11/2016 and 7/13/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="803ec-147">该问题可能会表现为从 Install-Module/Install-Script 或 Save-Module/Save-Script 返回的以下错误信息：</span><span class="sxs-lookup"><span data-stu-id="803ec-147">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```powershell
PS C:\> Install-Module xStorage 
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because: 
End of Central Directory record could not be found. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ... 
$null = PackageManagement\Install-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult: 
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}' 
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage 
```

<span data-ttu-id="803ec-148">__初始根本原因__：工程师发现 2016/7/11 部署到 PowerShell 库的 Azure Content Deliver Network (CDN) 出现问题。</span><span class="sxs-lookup"><span data-stu-id="803ec-148">__Preliminary root cause__: Engineers identified an issue with Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 7/11/2016.</span></span>  
<span data-ttu-id="803ec-149">__缓解__：工程师在 PowerShell 库中禁用 Azure CDN。</span><span class="sxs-lookup"><span data-stu-id="803ec-149">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>  
<span data-ttu-id="803ec-150">__后续步骤__：调查根本原因并制定解决方案，防止将来再次发生。</span><span class="sxs-lookup"><span data-stu-id="803ec-150">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>


## <a name="5192016---download-items-failed"></a><span data-ttu-id="803ec-151">2016/5/19 - 下载项目失败</span><span class="sxs-lookup"><span data-stu-id="803ec-151">5/19/2016 - Download Items Failed</span></span>
<span data-ttu-id="803ec-152">__影响摘要__：2016/5/17 - 2016/5/19 期间，部分客户从 PowerShell 库下载项目时遇到问题。</span><span class="sxs-lookup"><span data-stu-id="803ec-152">__Summary of Impact__: Between 5/17/2016 and 5/19/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="803ec-153">该问题可能会表现为从 Install-Module/Install-Script 或 Save-Module/Save-Script 返回的以下错误信息：</span><span class="sxs-lookup"><span data-stu-id="803ec-153">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```powershell
VERBOSE: Hash for package 'AzureRM.OperationalInsights' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='AzureRM.OperationalInsights', version='1.0.8',
destination='C:\Users\jbritt\AppData\Local\Temp\2\1741355729'
WARNING: Package 'AzureRM.OperationalInsights' failed to be installed because: 
End of Central Directory record could not be found. 
WARNING: Dependent Package 'AzureRM.OperationalInsights' failed to install. 
WARNING: Package 'AzureRM' failed to install. 
VERBOSE: Module 'AzureRM.Network' was saved successfully. 
VERBOSE: Saving the dependency module 'AzureRM.NotificationHubs' with version '1.0.8' for the 
module 'AzureRM'. 
VERBOSE: Module 'AzureRM.NotificationHubs' was saved successfully. 
PackageManagement\Save-Package : Unable to save the module 'AzureRM'. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1187 char:21 + 
$null = PackageManagement\Save-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + 
CategoryInfo : InvalidOperation: (Microsoft.Power...ets.SavePackage:SavePackage) 
[Save-Package], Exception + FullyQualifiedErrorId : ProviderFailToDownloadFile,
Microsoft.PowerShell.PackageManagement.Cmdlets.SavePackage 
```

<span data-ttu-id="803ec-154">__初始根本原因__：工程师发现 2016/5/17 部署到 PowerShell 库的 Azure Content Deliver Network (CDN) 的基础提供程序中断。</span><span class="sxs-lookup"><span data-stu-id="803ec-154">__Preliminary root cause__: Engineers identified an outage in the underlying provider of Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 5/17/2016.</span></span>  
<span data-ttu-id="803ec-155">__缓解__：工程师在 PowerShell 库中禁用 Azure CDN。</span><span class="sxs-lookup"><span data-stu-id="803ec-155">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>  
<span data-ttu-id="803ec-156">__后续步骤__：调查根本原因并制定解决方案，防止将来再次发生。</span><span class="sxs-lookup"><span data-stu-id="803ec-156">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>

