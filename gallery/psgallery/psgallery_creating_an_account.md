---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: 库,powershell,cmdlet,psgallery
title: 创建 PowerShell 库帐户
ms.openlocfilehash: c9c263a1926957cbdf059e062326b1903c117f46
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
## <a name="creating-a-powershell-gallery-account"></a>创建 PowerShell 库帐户

必须先创建 PowerShell 库帐户，然后才能将任何内容发布到 PowerShell 库。
必须将 PowerShell 库帐户与启用电子邮件的 Azure Active Directory 帐户或域名为 outlook.com、hotmail.com 等的 Microsoft 电子邮件帐户相关联。

若要创建 PowerShell 库帐户，请转到 https://PowerShellGallery.com，再单击“注册”（见下图）。

![注册新帐户](./images/CreatingAccount-Register.png)

若要使用 Azure Active Directory 帐户，请在下一页中选择“工作或学校帐户”，并使用帐户登录。
若要使用 Microsoft 帐户（如域名为 Hotmail.com 或 Outlook.com 的帐户），请选择“个人帐户”并登录。

登录后，系统便会提示创建 PowerShell 库帐户的用户名。
查看链接的使用条款和隐私策略，输入用户名，再单击“注册”。

注意：帐户名称一旦创建便无法再进行更改。
请参阅[管理项所有者](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners)，了解与此相关的其他详细信息。

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>适用于 PowerShell 库帐户的推荐做法

请务必确保可以主动监视对 PowerShell 库帐户使用的电子邮件帐户。
将使用与 PowerShell 库帐户关联的电子邮件地址通过电子邮件的方式与 PowerShell 库项的所有者进行所有通信往来。
如果我们无法联系项所有者，在某些情况下，运营团队可能需要删除项。

出于此目的，发布到 PowerShell 库的组织通常都会在 Outlook.com 或其他 Microsoft 帐户域中创建唯一帐户。
在许多情况下，都不会定期监视此帐户。
在这种情况下，最佳做法是使用 Outlook 转发功能将电子邮件转发到另一个帐户（通常是组织内受项所有者监视的帐户）。

如果项有多个关联的所有者，那么来自 PowerShell 库的所有通信都会发送给全部所有者。
请参阅[管理项所有者](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners)，详细了解如何向项添加所有者。