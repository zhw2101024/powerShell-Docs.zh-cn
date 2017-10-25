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
<a name="powershell-gallery-status"></a>PowerShell 库状态
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a>2017/03/27/ - 已解决：无法查看单个模块和脚本页面

__影响摘要__：指向 https://www.powershellgallery.com 上单个模块和脚本页面的直接链接已中断。 所有区域中均报告发生此问题。 这不会影响任意 PowerShellGet cmdlet（即 Install-Module、Install-Script、Update-Module、Update-Script、Publish-Module 和 Publish-Script）继续运行。

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


