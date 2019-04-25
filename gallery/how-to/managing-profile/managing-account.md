---
ms.date: 09/05/2018
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: PowerShell 库帐户设置
ms.openlocfilehash: ebe784ec5aae5ff3a4d444d12a168ef38aaef65f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084424"
---
# <a name="powershell-gallery-account-settings"></a><span data-ttu-id="3a432-103">PowerShell 库帐户设置</span><span class="sxs-lookup"><span data-stu-id="3a432-103">PowerShell Gallery Account Settings</span></span>

<span data-ttu-id="3a432-104">PowerShell 库帐户是一个公开可见的名称，该名称链接到标识。</span><span class="sxs-lookup"><span data-stu-id="3a432-104">Your PowerShell Gallery account is a publicly visible name that is linked to an identity.</span></span> <span data-ttu-id="3a432-105">该标识可为 Microsoft ID，如 `user@hotmail.com` 或 `user@outlook.com`，也可为 Azure Active Directory (AAD) 帐户。</span><span class="sxs-lookup"><span data-stu-id="3a432-105">That identity is either a Microsoft ID, like `user@hotmail.com` or `user@outlook.com`, or an Azure Active Directory (AAD) account.</span></span>

<span data-ttu-id="3a432-106">PowerShell 库提供了以下帐户设置：</span><span class="sxs-lookup"><span data-stu-id="3a432-106">The PowerShell Gallery provides the following account settings:</span></span>

- <span data-ttu-id="3a432-107">与 PowerShell 库帐户关联的电子邮件帐户</span><span class="sxs-lookup"><span data-stu-id="3a432-107">The email account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="3a432-108">从 PowerShell 库发送的电子邮件通知选项</span><span class="sxs-lookup"><span data-stu-id="3a432-108">Options for email notifications sent from the PowerShell Gallery</span></span>
- <span data-ttu-id="3a432-109">与 PowerShell 库帐户关联的用户帐户</span><span class="sxs-lookup"><span data-stu-id="3a432-109">The user account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="3a432-110">与 PowerShell 库帐户关联的图片</span><span class="sxs-lookup"><span data-stu-id="3a432-110">The picture associated with your PowerShell Gallery account</span></span>

## <a name="email-address"></a><span data-ttu-id="3a432-111">电子邮件地址</span><span class="sxs-lookup"><span data-stu-id="3a432-111">Email address</span></span>

<span data-ttu-id="3a432-112">电子邮件地址是 PowerShell 库通知的目标。</span><span class="sxs-lookup"><span data-stu-id="3a432-112">The email address is the destination for PowerShell Gallery notifications.</span></span> <span data-ttu-id="3a432-113">它不必与登录帐户匹配。</span><span class="sxs-lookup"><span data-stu-id="3a432-113">It does not have to match the login account.</span></span> <span data-ttu-id="3a432-114">可使用任何有权访问的电子邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="3a432-114">You may use any email account you have access to.</span></span> <span data-ttu-id="3a432-115">PowerShell 库永不会向其他用户直接提供电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="3a432-115">Your email address is never directly provided by the PowerShell Gallery to other users.</span></span>

![更改电子邮件地址](../../Images/PSGallery_AcccountEmailAddress.png)

<span data-ttu-id="3a432-117">输入新的电子邮件地址时，PowerShell 库会向该地址发送验证邮件。</span><span class="sxs-lookup"><span data-stu-id="3a432-117">When you enter a new email address, the PowerShell Gallery sends a verification mail to that address.</span></span> <span data-ttu-id="3a432-118">验证邮件包含一个返回 PowerShell 库的链接，以完成更改过程。</span><span class="sxs-lookup"><span data-stu-id="3a432-118">The verification mail contains a link back to the PowerShell Gallery to complete the change process.</span></span> <span data-ttu-id="3a432-119">完成验证过程之前，所有通知都会发送到先前的地址。</span><span class="sxs-lookup"><span data-stu-id="3a432-119">Until you complete the verification process, all notifications are sent to the previous address.</span></span>

## <a name="email-notifications"></a><span data-ttu-id="3a432-120">电子邮件通知</span><span class="sxs-lookup"><span data-stu-id="3a432-120">Email notifications</span></span>

<span data-ttu-id="3a432-121">PowerShell 库提供了以下通知选项：</span><span class="sxs-lookup"><span data-stu-id="3a432-121">PowerShell Gallery provides the following notification options:</span></span>

- <span data-ttu-id="3a432-122">用户可通过 PowerShell 库与我联系</span><span class="sxs-lookup"><span data-stu-id="3a432-122">Users can contact me through the PowerShell Gallery</span></span>
- <span data-ttu-id="3a432-123">使用我的帐户向 PowerShell 库推送包时通知我</span><span class="sxs-lookup"><span data-stu-id="3a432-123">Notify me when an package is pushed to the PowerShell Gallery using my account</span></span>

![更改电子邮件地址](../../Images/PSGallery_AccountEmailOptions.png)

<span data-ttu-id="3a432-125">如页面所述，无法禁用 PowerShell 库中的重要通知。</span><span class="sxs-lookup"><span data-stu-id="3a432-125">As noted on the page, critical notifications from the PowerShell Gallery can't be disabled.</span></span>
<span data-ttu-id="3a432-126">其中包括：</span><span class="sxs-lookup"><span data-stu-id="3a432-126">These include:</span></span>

- <span data-ttu-id="3a432-127">安全通知</span><span class="sxs-lookup"><span data-stu-id="3a432-127">Security notifications</span></span>
- <span data-ttu-id="3a432-128">来自 PowerShell 库管理员的帐户管理通知</span><span class="sxs-lookup"><span data-stu-id="3a432-128">Account management notifications from PowerShell Gallery administrators</span></span>
- <span data-ttu-id="3a432-129">有关 PowerShell 库针对提交运行测试的通知</span><span class="sxs-lookup"><span data-stu-id="3a432-129">Notifications about the tests run by the PowerShell Gallery for submissions you have made</span></span>

## <a name="change-your-login-account"></a><span data-ttu-id="3a432-130">更改登录帐户</span><span class="sxs-lookup"><span data-stu-id="3a432-130">Change your login account</span></span>

<span data-ttu-id="3a432-131">若要更改登录帐户，必须使用当前帐户登录。</span><span class="sxs-lookup"><span data-stu-id="3a432-131">To change the login account, you must be signed in with the current account.</span></span> <span data-ttu-id="3a432-132">请使用以下步骤完成更改。</span><span class="sxs-lookup"><span data-stu-id="3a432-132">Use the following steps to complete the change.</span></span>

![登录帐户设置](../../Images/PSGallery_LoginAccountSettings.png)

1. <span data-ttu-id="3a432-134">单击“更改帐户”。</span><span class="sxs-lookup"><span data-stu-id="3a432-134">Click on **Change Account**.</span></span> <span data-ttu-id="3a432-135">弹出窗口说明更改登录帐户适用于 PowerShell 库中该帐户的所有用途。</span><span class="sxs-lookup"><span data-stu-id="3a432-135">A pop-up window explains that changing the login account applies to all uses of that account in the PowerShell Gallery.</span></span> <span data-ttu-id="3a432-136">查看信息，然后单击“确定”以继续。</span><span class="sxs-lookup"><span data-stu-id="3a432-136">Review the information, then click **OK** to continue.</span></span>

   ![登录帐户设置](../../Images/PSGallery_LoginAccountChange-1.png)

2. <span data-ttu-id="3a432-138">随后系统将提示使用新账户登录。</span><span class="sxs-lookup"><span data-stu-id="3a432-138">You are then prompted to sign in using the _new account_.</span></span>

   ![登录帐户设置](../../Images/PSGallery_LoginAccountChange-2.png)

3. <span data-ttu-id="3a432-140">单击“下一步”时，将看到使用当前帐户登录的消息。</span><span class="sxs-lookup"><span data-stu-id="3a432-140">When you click **Next**, you see a message that you are signed in using the current account.</span></span>
   <span data-ttu-id="3a432-141">单击“使用不同的帐户注销和登录”。</span><span class="sxs-lookup"><span data-stu-id="3a432-141">Click **Sign out and sign in with a different account**.</span></span>

   ![登录帐户设置](../../Images/PSGallery_LoginAccountChange-3.png)

4. <span data-ttu-id="3a432-143">请输入新帐户的密码。</span><span class="sxs-lookup"><span data-stu-id="3a432-143">Enter the password of the new account.</span></span> <span data-ttu-id="3a432-144">输入密码后，将返回到“帐户设置”页面，显示登录帐户已更新。</span><span class="sxs-lookup"><span data-stu-id="3a432-144">After entering the password, you are returned to the Account Settings page showing you that the login account has been updated.</span></span>


## <a name="enable-two-factor-authentication-2fa"></a><span data-ttu-id="3a432-145">启用双重身份验证 (2FA)</span><span class="sxs-lookup"><span data-stu-id="3a432-145">Enable Two-Factor Authentication (2FA)</span></span>

<span data-ttu-id="3a432-146">对于手动发布到 PowerShell 库的所有用户，建议使用双重身份验证。</span><span class="sxs-lookup"><span data-stu-id="3a432-146">Two-factor authentication is recommended for all users who publish manually to the PowerShell Gallery.</span></span> <span data-ttu-id="3a432-147">若要启用双重身份验证，登录帐户必须至少注册两种形式的身份验证。</span><span class="sxs-lookup"><span data-stu-id="3a432-147">To enable two-factor authentication, the login account must have at least two forms of authentication registered.</span></span> <span data-ttu-id="3a432-148">其中一种形式是密码，其他形式可为：</span><span class="sxs-lookup"><span data-stu-id="3a432-148">One is a password and the other forms can be:</span></span>

- <span data-ttu-id="3a432-149">可接收短信的电话号码</span><span class="sxs-lookup"><span data-stu-id="3a432-149">A phone number that can receive text messages</span></span>
- <span data-ttu-id="3a432-150">注册的身份验证器应用程序，例如适用于移动电话的 Microsoft 身份验证器</span><span class="sxs-lookup"><span data-stu-id="3a432-150">A registered authenticator application, such as Microsoft Authenticator for your mobile phone</span></span>

<span data-ttu-id="3a432-151">必须在 AAD 帐户信息或 Microsoft ID 帐户安全设置中配置这些身份验证形式。</span><span class="sxs-lookup"><span data-stu-id="3a432-151">These forms of authentication must be configured in your AAD account information or in your Microsoft ID Account Security settings.</span></span>

<span data-ttu-id="3a432-152">启用 2FA 后，每次登录 PowerShell 库时都需要使用配置的身份验证形式进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="3a432-152">Once 2FA is enabled, you are required to authenticate using the configured forms of authentication every time you sign in to the PowerShell Gallery.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3a432-153">为 PowerShell 库站点启用双重身份验证无需为登录帐户的所有用途启用 2FA。</span><span class="sxs-lookup"><span data-stu-id="3a432-153">Enabling two-factor authentication for the PowerShell Gallery site does not require you to enable 2FA for all uses of your login account.</span></span> <span data-ttu-id="3a432-154">有关详细信息，请参阅[有关双重验证](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification)。</span><span class="sxs-lookup"><span data-stu-id="3a432-154">For more information, see [About two-step verification](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span></span>

## <a name="change-your-profile-picture"></a><span data-ttu-id="3a432-155">更改个人资料图片</span><span class="sxs-lookup"><span data-stu-id="3a432-155">Change your profile picture</span></span>

<span data-ttu-id="3a432-156">PowerShell 库借助 Gravatar 存储和显示与个人资料相关联的图片。</span><span class="sxs-lookup"><span data-stu-id="3a432-156">The PowerShell Gallery relies on Gravatar to store and display the picture associated with your profile.</span></span> <span data-ttu-id="3a432-157">要更新个人资料图片，请访问 [Gravatar.com](http://www.gravatar.com/)。</span><span class="sxs-lookup"><span data-stu-id="3a432-157">To update your profile image, visit [Gravatar.com](http://www.gravatar.com/).</span></span>
