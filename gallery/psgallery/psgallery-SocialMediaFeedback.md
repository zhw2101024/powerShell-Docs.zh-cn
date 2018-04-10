---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: 库,powershell,cmdlet,psgallery
title: 通过社交媒体或发表评论提供反馈
ms.openlocfilehash: 9e2a5a246b1caa37ad7b03e20c8f543b9e5cf530
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="providing-feedback-via-social-media-or-comments"></a>通过社交媒体或发表评论提供反馈

Powershell 库支持以下两种反馈方法，以便用户能够提供有关项的公共反馈：

* 使用左侧边缘的链接，在 Facebook、LinkedIn 或 Twitter 社交媒体网站中“分享”项；
* 使用评论功能对项发表评论，并允许作者查看已对项发表的评论。

## <a name="social-media-feedback"></a>社交媒体反馈
对于 PowerShell 库中的每一项，网页左侧都有 Facebook、LinkedIn 和 Twitter 链接。
单击这些链接可以打开社交媒体网站，并能快速分享项链接。

用户必须登录已选择的网站，才能分享 PowerShell 库项。

如果用户认为需要向他人推荐项，建议这样做。
PowerShell 库将检查每个用于“分享”项的社交媒体网站，并显示相应项在每个社交媒体网站中的分享次数。
由于只显示分享次数，因此其他用户可以看作是“赞”相应项的次数。


## <a name="comments"></a>说明
PowerShell 库使用 LiveFyre 服务来允许用户对项发表评论。
如果需要提供建议或反馈，用户可以使用此功能提供对项网页的所有访问者都可见的反馈。
项所有者可以关注此反馈，并在有人发表评论时收到通知。

评论系统基于 LiveFyre，这是不受 Microsoft 管理的独立服务，要求使用唯一登录名。
首次选择对一个项发表评论或关注评论时，系统会提示创建 LiveFyre 帐户。

如果已经创建 LiveFyre 帐户并登录，可以编写评论以提供项反馈，再单击“发表评论...”。评论不会立即可见。
PowerShell 库管理员会审核库项的评论，要发表的所有评论都会先经由审查方审核，然后才会发表并对其他人可见。
之所以要审核评论是为了确保它们符合 PowerShell 库[使用条款](https://www.powershellgallery.com/policies/Terms)规定的公共行为。

建议项所有者关注在 LiveFyre 中发表的评论。
必须创建 LiveFyre 帐户，建议使用在 LiveFyre 中发布项时所用的同一电子邮件地址。
若要关注评论，请先登录 LiveFyre，再转到你被列为所有者的任意项。
在每个项底部的评论框下方，都会看到“+关注”。
单击此按钮后，LiveFyre 便会在有人对此项发表新评论时向注册的电子邮件地址发送电子邮件。