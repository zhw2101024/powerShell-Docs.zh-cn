---
ms.date: 09/11/2018
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: 创建 PowerShell 库帐户
ms.openlocfilehash: 08d18310d9e18b00bd9e22efcc552dfd29f8982c
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522816"
---
# <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="ad832-103">创建 PowerShell 库帐户</span><span class="sxs-lookup"><span data-stu-id="ad832-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="ad832-104">在将任何内容发布到 PowerShell 库之前，必须先创建 PowerShell 库帐户。</span><span class="sxs-lookup"><span data-stu-id="ad832-104">You must create a PowerShell Gallery account before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="ad832-105">必须将 PowerShell 库帐户链接到启用电子邮件的登录帐户。</span><span class="sxs-lookup"><span data-stu-id="ad832-105">PowerShell Gallery accounts must be linked to an email-enabled login account.</span></span> <span data-ttu-id="ad832-106">此帐户可为 Azure Active Directory 帐户或 Microsoft ID，例如 outlook.com 或 hotmail.com 的电子邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="ad832-106">This account can be an Azure Active Directory account or a Microsoft ID, like an email account from outlook.com or hotmail.com.</span></span>

<span data-ttu-id="ad832-107">要创建 PowerShell 库帐户，请转到 [https://PowerShellGallery.com](https://PowerShellGallery.com)，然后单击“登录”，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="ad832-107">To create a PowerShell Gallery account, go to [https://PowerShellGallery.com](https://PowerShellGallery.com) and click on **Sign in** as shown in the following image.</span></span>

![注册新帐户](../../Images/CreateAccount-Register.png)

<span data-ttu-id="ad832-109">若要使用 Azure Active Directory 帐户，请选择“工作或学校帐户”，并使用帐户登录。</span><span class="sxs-lookup"><span data-stu-id="ad832-109">To use an Azure Active Directory account, select **Work or School Account**, and sign in with your account.</span></span> <span data-ttu-id="ad832-110">若要使用 Microsoft ID，请选择“个人帐户”并登录。</span><span class="sxs-lookup"><span data-stu-id="ad832-110">To use a Microsoft ID, choose **Personal Account** and sign in.</span></span>

<span data-ttu-id="ad832-111">接下来系统便会提示创建 PowerShell 库帐户的用户名。</span><span class="sxs-lookup"><span data-stu-id="ad832-111">Next, you are prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="ad832-112">查看使用条款和隐私策略，输入用户名，然后单击“注册”。</span><span class="sxs-lookup"><span data-stu-id="ad832-112">Review the Terms of Use and Privacy Policy, enter a username, and then click **Register**.</span></span>

> [!NOTE]
> <span data-ttu-id="ad832-113">帐户名称一旦创建便无法再进行更改。</span><span class="sxs-lookup"><span data-stu-id="ad832-113">The account name cannot be changed once it is created.</span></span> <span data-ttu-id="ad832-114">有关详细信息，请参阅[管理项所有者](managing-item-owners.md)。</span><span class="sxs-lookup"><span data-stu-id="ad832-114">For more information, see [Managing Item Owners](managing-item-owners.md).</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="ad832-115">适用于 PowerShell 库帐户的推荐做法</span><span class="sxs-lookup"><span data-stu-id="ad832-115">Recommended practices for PowerShell Gallery accounts</span></span>

<span data-ttu-id="ad832-116">请务必确保可主动监视对 PowerShell 库帐户使用的电子邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="ad832-116">It's important to actively monitor the email account used with your PowerShell Gallery account.</span></span> <span data-ttu-id="ad832-117">与 PowerShell 库项所有者的所有通信均通过此电子邮件地址进行。</span><span class="sxs-lookup"><span data-stu-id="ad832-117">All communication with owners of PowerShell Gallery items is through this email address.</span></span> <span data-ttu-id="ad832-118">若 PowerShell 库运营团队无法联系项所有者，我们可能需要删除项。</span><span class="sxs-lookup"><span data-stu-id="ad832-118">If the PowerShell Gallery Operations team is unable to contact an item owner, we may be required to delete an item.</span></span>

<span data-ttu-id="ad832-119">出于此目的，发布到 PowerShell 库的组织通常会创建唯一外部帐户。</span><span class="sxs-lookup"><span data-stu-id="ad832-119">Organizations that publish to the PowerShell Gallery often create a unique external account for that purpose.</span></span> <span data-ttu-id="ad832-120">我们建议使用电子邮件转发功能将通知转发到组织内的地址。</span><span class="sxs-lookup"><span data-stu-id="ad832-120">We recommend you use email forwarding to forward notifications to an address within your organization.</span></span>

<span data-ttu-id="ad832-121">当多个所有者与项关联时，所有 PowerShell 库向所有所有者发送通知。</span><span class="sxs-lookup"><span data-stu-id="ad832-121">When multiple owners are associated with an item, all PowerShell Gallery notifications are sent to all owners.</span></span> <span data-ttu-id="ad832-122">有关详细信息，请参阅[管理项所有者](managing-item-owners.md)。</span><span class="sxs-lookup"><span data-stu-id="ad832-122">For more information, see [Managing Item Owners](managing-item-owners.md).</span></span>
