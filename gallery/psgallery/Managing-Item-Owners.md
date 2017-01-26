---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: "管理项所有者"
ms.technology: powershell
ms.openlocfilehash: 36a3a3079bce642b16f0512ead2b0778b43e5d2d
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="managing-item-owners"></a>管理项所有者

由将项发布到库的人定义 PowerShell 中项的所有权。
有时需要在初始项发布之外管理此元数据，这意味着所有者元数据需要是可变的，而项本身不需要。

所有项所有者是对等的。 这意味着任何项所有者都可发布项的新版本。 这还意味着任何项所有者可以删除任何其他所有者。 每个所有者的权利相同。  

## <a name="setting-an-items-initial-owner"></a>设置项的初始所有者 

当新项发布到 PowerShell 库时，由发布项的用户定义初始所有者。 这根据 Publish-Module cmdlet 中使用谁的 API 密钥决定。

## <a name="adding-owners"></a>添加所有者

将项发布到 PowerShell 库后，可轻松邀请其他用户成为项的所有者。

1. 使用项的当前所有者的帐户[登录](https://powershellgallery.com/users/account/LogOn) PowerShell 库。
2. 通过使用“项”选项卡、搜索或单击你的用户名，然后单击[**“管理我的项”**](https://www.powershellgallery.com/account/Packages)，导航到项页面。
3. 以项的所有者身份登录时，左侧有“管理所有者”链接可以单击。
4. 输入要添加为所有者的人员的用户名，并单击“添加”。
5. 随后将向新的共同所有者发送一封电子邮件，作为成为项的所有者的邀请函。
6. 该用户单击此链接后，将成为对项具有完全控制权的完全共同所有者，其控制权包括删除其他用户所有者身份的能力。

**注意**：新的所有者必须先确认所有权，否则*不会*列为项的所有者。
查看“管理所有者”页面时，你将在当前所有者中看到“等待审批”条目。
可以删除该邀请；同样也可以删除其他所有者。
此邀请过程可防止用户错误地将其他用户添加为其项的所有者。

注意：“Authors”元数据是完全自由文本；仅“Owners”受控。


## <a name="removing-owners"></a>删除所有者
如果项具有多个所有者而需删除其中之一，过程很简单：

1. 使用项的当前所有者的帐户[登录](https://powershellgallery.com/users/account/LogOn) PowerShell 库；
2. 通过使用“项”选项卡、搜索或单击你的用户名，然后单击“管理我的项”[](https://www.powershellgallery.com/account/Packages)，导航到项页面。
3. 如果以项的所有者身份登录，左侧有“管理所有者”链接可以单击；
4. 单击要删除的所有者旁边的“删除”链接。



## <a name="transferring-item-ownership"></a>转移项所有权
我们时而收到将项所有权从一个用户转移到另一个用户的支持请求，但你几乎始终可自己完成该操作。
将所有权从一个用户转移到另一个用户只是以上两种功能的组合。

1. 当前所有者邀请新用户成为共同所有者，新用户接受邀请；
2. 新用户将旧用户从所有者列表中删除。

此请求有多种形式，但过程相同。

* 项所有者从一个开发人员更改为另一个开发人员
* 使用错误帐户意外发布了项


## <a name="orphaned-items"></a>孤立的项
最后一种情况曾经出现，但次数不多。
项变得孤立，唯一的项所有者帐户不能用于添加新所有者。
以下是本场景的一些示例：

* 所有者帐户与不再存在的电子邮件地址关联，且用户忘记其密码
* 生成项的已注册所有者已离开公司，无法与其联系以更新项所有权
* 由于仅影响少量的项的 bug，项在库中无所有者

PowerShell 库管理员可以访问任何项的“管理所有者”链接。
如果你是项的合法所有者，而无法联系当前所有者以获取所有权，可使用库中的“报告滥用行为”链接与 PowerShell 库管理员联系。
然后，我们将按流程验证你对该项的所有权。
如果我们确定你应为该项的所有者，我们将使用该项的“管理所有者”链接，向你发送成为所有者的邀请。
我们将仅在验证你应为所有者后才执行此操作，此过程因具体情况而异。
通常，我们将使用项的项目 URL 设法联系项目所有者，但我们也可能使用 Twitter、电子邮件或其他方式联系项目所有者。

