---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psgallery_status
ms.technology: powershell
ms.openlocfilehash: a260b9b696b41947fbbb789fd165dfe4bdac1dc3
ms.sourcegitcommit: 214b8442f05618d078837889cbb6a30b42c01edb
translationtype: HT
---
<a name="powershell-gallery-status"></a>PowerShell 库状态
=========================

## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a>2017/04/11 - 用户无法使用 Azure Active Directory (AAD) 帐户登录

__影响摘要__：某些用户无法使用 Azure AD 帐户登录到 PowerShell 库。 
 
__根本原因__：在执行更新以实现与 AAD 更安全交互的过程中，缺少了某项设置更改。 用于验证更改的测试未包含某些类型的 AAD 帐户，因此该部署还会继续。

__解决办法__：工程师确定了缺少的设置并更正了此问题。 

__后续步骤__：我们将修改测试以包含一组更广泛的 AAD 帐户类型。

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a>2017/03/27/ - 已解决：无法查看单个模块和脚本页面

__影响摘要__：指向 https://www.powershellgallery.com 上单个模块和脚本页面的直接链接已中断。 所有区域中均报告发生此问题。 这不会影响任意 PowerShellGet cmdlet，即 Install-Module、Install-Script、Update-Module、Update-Script、Publish-Module 和 Publish-Scirpt 继续运行。

__根本原因__：工程师确定原因是将类似 Facebook 的社交媒体按钮设置在了页面上。  

__解决__：工程师已通过禁用 Facebook 计数信息修复了此问题。

__后续步骤__：已打开内部跟踪，跟踪 Facebook API 使用情况修复问题。

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a>2016/12/15 - 无法通过 PowerShellGallery 网站发送电子邮件

__影响摘要__：在 2016/12/13 到 2016/12/15 之间，PowerShell 库管理员未收到通过“联系所有者”、“管理所有者”、“联系支持人员”或“举报不良信息”发送的任何邮件。  
__根本原因__：工程师已确定原因是 SMTP 服务器身份验证问题。  
__解决办法__：工程师能够解决身份验证问题，并恢复与 SMTP 服务器的连接。  
__后续步骤__：如果在这段时间内通过“联系所有者”、“管理所有者”、“联系支持人员”或“举报不良信息”链接向 cgadmin@microsoft.com 发送了邮件，而我们未回复，请重试。 由此造成的不便，我们深表歉意。  



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a>2016/8/10 - 已解决：无法将电子邮件发送到 cgadmin@microsoft.com

__影响摘要__：2016/8/5 - 2016/8/10 期间，客户无法将电子邮件发送到 cgadmin@microsoft.com，也无法使用“联系我们”功能。  
__根本原因__：工程师确定原因为电子邮件帐户的配置更改。  
__解决办法__：工程师努力解决了配置问题。  
后续步骤：如果在此期间使用了“联系我们”链接或向 cgadmin@microsoft.com 发送了电子邮件，但我们没有回复，请重试。 感谢你的耐心等待。



## <a name="7132016---download-items-failed"></a>2016/7/13 - 下载项目失败

__影响摘要__：2016/7/11 - 2016/7/13 期间，部分客户在从 PowerShell 库下载项目时遇到问题。 该问题可能会表现为从 Install-Module/Install-Script 或 Save-Module/Save-Script 返回的以下错误信息：

```PowerShell
PS C:\> Install-Module xStorage 
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because: 
End of Central Directory record could not be found. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ... 
$null = PackageManagement\Install-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult: 
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}' 
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage 
```

__初始根本原因__：工程师发现 2016/7/11 部署到 PowerShell 库的 Azure Content Deliver Network (CDN) 出现问题。  
__缓解__：工程师在 PowerShell 库中禁用 Azure CDN。  
__后续步骤__：调查根本原因并制定解决方案，防止将来再次发生。


## <a name="5192016---download-items-failed"></a>2016/5/19 - 下载项目失败
__影响摘要__：2016/5/17 - 2016/5/19 期间，部分客户从 PowerShell 库下载项目时遇到问题。 该问题可能会表现为从 Install-Module/Install-Script 或 Save-Module/Save-Script 返回的以下错误信息：

```PowerShell
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

__初始根本原因__：工程师发现 2016/5/17 部署到 PowerShell 库的 Azure Content Deliver Network (CDN) 的基础提供程序中断。  
__缓解__：工程师在 PowerShell 库中禁用 Azure CDN。  
__后续步骤__：调查根本原因并制定解决方案，防止将来再次发生。

