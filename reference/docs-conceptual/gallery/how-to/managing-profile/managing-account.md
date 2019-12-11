---
ms.date: 09/05/2018
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: PowerShell 库帐户设置
ms.openlocfilehash: ebe784ec5aae5ff3a4d444d12a168ef38aaef65f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328028"
---
# <a name="powershell-gallery-account-settings"></a>PowerShell 库帐户设置

PowerShell 库帐户是一个公开可见的名称，该名称链接到标识。 该标识可为 Microsoft ID，如 `user@hotmail.com` 或 `user@outlook.com`，也可为 Azure Active Directory (AAD) 帐户。

PowerShell 库提供了以下帐户设置：

- 与 PowerShell 库帐户关联的电子邮件帐户
- 从 PowerShell 库发送的电子邮件通知选项
- 与 PowerShell 库帐户关联的用户帐户
- 与 PowerShell 库帐户关联的图片

## <a name="email-address"></a>电子邮件地址

电子邮件地址是 PowerShell 库通知的目标。 它不必与登录帐户匹配。 可使用任何有权访问的电子邮件帐户。 PowerShell 库永不会向其他用户直接提供电子邮件地址。

![更改电子邮件地址](../../Images/PSGallery_AcccountEmailAddress.png)

输入新的电子邮件地址时，PowerShell 库会向该地址发送验证邮件。 验证邮件包含一个返回 PowerShell 库的链接，以完成更改过程。 完成验证过程之前，所有通知都会发送到先前的地址。

## <a name="email-notifications"></a>电子邮件通知

PowerShell 库提供了以下通知选项：

- 用户可通过 PowerShell 库与我联系
- 使用我的帐户向 PowerShell 库推送包时通知我

![更改电子邮件地址](../../Images/PSGallery_AccountEmailOptions.png)

如页面所述，无法禁用 PowerShell 库中的重要通知。
其中包括：

- 安全通知
- 来自 PowerShell 库管理员的帐户管理通知
- 有关 PowerShell 库针对提交运行测试的通知

## <a name="change-your-login-account"></a>更改登录帐户

若要更改登录帐户，必须使用当前帐户登录。 请使用以下步骤完成更改。

![登录帐户设置](../../Images/PSGallery_LoginAccountSettings.png)

1. 单击“更改帐户”  。 弹出窗口说明更改登录帐户适用于 PowerShell 库中该帐户的所有用途。 查看信息，然后单击“确定”以继续  。

   ![登录帐户设置](../../Images/PSGallery_LoginAccountChange-1.png)

2. 随后系统将提示使用新账户登录  。

   ![登录帐户设置](../../Images/PSGallery_LoginAccountChange-2.png)

3. 单击“下一步”时，将看到使用当前帐户登录的消息  。
   单击“使用不同的帐户注销和登录”  。

   ![登录帐户设置](../../Images/PSGallery_LoginAccountChange-3.png)

4. 请输入新帐户的密码。 输入密码后，将返回到“帐户设置”页面，显示登录帐户已更新。


## <a name="enable-two-factor-authentication-2fa"></a>启用双重身份验证 (2FA)

对于手动发布到 PowerShell 库的所有用户，建议使用双重身份验证。 若要启用双重身份验证，登录帐户必须至少注册两种形式的身份验证。 其中一种形式是密码，其他形式可为：

- 可接收短信的电话号码
- 注册的身份验证器应用程序，例如适用于移动电话的 Microsoft 身份验证器

必须在 AAD 帐户信息或 Microsoft ID 帐户安全设置中配置这些身份验证形式。

启用 2FA 后，每次登录 PowerShell 库时都需要使用配置的身份验证形式进行身份验证。

> [!IMPORTANT]
> 为 PowerShell 库站点启用双重身份验证无需为登录帐户的所有用途启用 2FA。 有关详细信息，请参阅[有关双重验证](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification)。

## <a name="change-your-profile-picture"></a>更改个人资料图片

PowerShell 库借助 Gravatar 存储和显示与个人资料相关联的图片。 要更新个人资料图片，请访问 [Gravatar.com](http://www.gravatar.com/)。
