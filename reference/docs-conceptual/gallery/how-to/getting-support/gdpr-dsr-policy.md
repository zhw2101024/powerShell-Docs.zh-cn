---
ms.date: 03/27/2018
contributor: JKeithB
keywords: 库, powershell, psgallery, GDPR
title: PowerShell 库 GDPR 符合性
ms.openlocfilehash: fb1191d8a1cd12d5994e41238c384eb504d0c261
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328318"
---
# <a name="powershell-gallery-gdpr-compliance"></a>PowerShell 库 GDPR 符合性

## <a name="overview"></a>概述

2018 年 5 月，名为“一般数据保护条例 (GDPR)”的欧洲隐私法生效。
GDPR 规定了公司、政府机构、公益组织以及负责以下事务的其他组织需要遵守的新规则：为欧盟民众提供商品和服务，或收集和分析与欧盟民众相关的数据。
GDPR 的适用对象不受地理位置限制。

> [!NOTE]
> 本文提供有关如何从 PowerShell 库删除个人数据的步骤，并可用于支持你在 GDPR 约束下的义务。 如果要了解 GDPR 的一般信息，请参阅[服务信任门户的 GDPR 部分](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted)。

## <a name="personally-identifiable-data"></a>个人身份数据

PowerShell 库存储以下可能由用户提供的信息，信息中可能包含个人信息：

- PowerShell 库帐户
- 发布到 PowerShell 库的包
- 与 PowerShell 库团队的电子邮件通信

大多数用户不创建 PowerShell 库帐户。
除非要发布包或使用 PowerShell 库中的“联系所有者”功能，否则不需要帐户。
除了用户发起的电子邮件通信，PowerShell 库不保存未创建帐户的用户的个人身份数据。

创建 PowerShell 库帐户的用户可以将包发布到 PowerShell 库。
这些包都应为 PowerShell 代码，但也可能包含其他信息，包括个人信息。
以下信息将显示如何获取已发布到 PowerShell 库的所有包。

## <a name="dsr-export-of-powershell-gallery-data"></a>PowerShell 库数据的 DSR 导出

以下各节介绍 PowerShell 库如何支持数据主体请求 (DSR)，其中涉及如何导出保存在 PowerShell 库中的信息，以及如何请求删除此信息。

### <a name="email"></a>电子邮件

电子邮件通信可能包括以下任一项：

- 如果代码分析扫描检测到已发布到 PowerShell 库的包存在问题，则会向 PowerShell 库包的所有者发送电子邮件
- 任何人使用“联系我们”页面中的电子邮件地址 ([cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)) 向 PowerShell 库团队发送电子邮件
- 注册用户使用 PowerShell 库中的“联系所有者”功能，向 PowerShell 库中某个包的所有者发送电子邮件

PowerShell 库发送和接收的电子邮件具有 90 天的保留策略，以支持 PowerShell 库中发现恶意代码时进行可能的安全调查。
根据策略，电子邮件会在 90 天后删除。

可以请求过去 90 天里，你的电子邮件地址和 PowerShell 库发送和接收的所有电子邮件副本。
若要请求这种对应关系，请发送电子邮件至 [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)，标题为：“此帐户相关电子邮件的 DSR 请求”。
请在邮件正文中说明请求的信息（例如：请发送所有发送到或接收自此电子邮件地址的电子邮件。）请求日期前 90 天与你的电子邮件地址有关的所有电子邮件将在 7 个工作日内发送。

### <a name="powershell-gallery-account-information"></a>PowerShell 库帐户信息

如果已创建 PowerShell 库帐户，可通过以下步骤查找存储在 PowerShell 库中的所有个人信息：

1. 登录 PowerShell 库，然后单击你的用户名
2. 显示的下一页为帐户页，将显示用于 PowerShell 库帐户的电子邮件地址

如果已在 PowerShell 库中创建多个帐户，则需要为每个帐户重复执行这些步骤。

### <a name="packages-in-the-powershell-gallery"></a>PowerShell 库中的包

为了导出发布到 PowerShell 库的包，我们已将脚本“GetPSGalleryItemsForAuthor”发布到 PowerShell 库。
此脚本基于包中存储的作者信息，导出 PowerShell 库上的每个包的所有版本副本。

> [!NOTE]
> 发布包时，包清单中将存储作者。
> 不保证该创建者与 PowerShell 库中使用的帐户是相同身份。
> 如果“创建者”字段使用其他值，则需要在使用此脚本时提供此值。

可使用以下 PowerShell 命令来下载该脚本：

```powershell
Save-Script Get-repository psgallery
```

可通过运行以下 PowerShell 命令直接运行该脚本：

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

系统会提示你提供作者以及要在系统上保存包的文件夹。

## <a name="deleting-personal-data-from-the-powershell-gallery"></a>从 PowerShell 库中删除个人数据

若要删除 PowerShell 库帐户或你在 PowerShell 库中拥有的任何包，请发送电子邮件至 cgadmin@microsoft.com，标题为：“此帐户相关项目的 GDPR 请求”。
请在邮件正文中说明要删除哪些信息。 例如：

- 请删除我的包“包名称”的版本 x.y.z
- 请删除我的包“包名称”的所有版本
- 请删除我的 PowerShell 库帐户

PowerShell 库管理员将在 7 个工作日内回复。
在发送请求后的 30 天内，将删除指定的包。
