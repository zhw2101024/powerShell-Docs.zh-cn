---
ms.date: 09/11/2018
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: 创建 PowerShell 库帐户
ms.openlocfilehash: e4cf73edb03267cff6bbcc0cf3b754225e45be9f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328278"
---
# <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="ee333-103">创建 PowerShell 库帐户</span><span class="sxs-lookup"><span data-stu-id="ee333-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="ee333-104">在将任何内容发布到 PowerShell 库之前，必须先创建 PowerShell 库帐户。</span><span class="sxs-lookup"><span data-stu-id="ee333-104">You must create a PowerShell Gallery account before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="ee333-105">必须将 PowerShell 库帐户链接到启用电子邮件的登录帐户。</span><span class="sxs-lookup"><span data-stu-id="ee333-105">PowerShell Gallery accounts must be linked to an email-enabled login account.</span></span> <span data-ttu-id="ee333-106">此帐户可为 Azure Active Directory 帐户或 Microsoft ID，例如 outlook.com 或 hotmail.com 的电子邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="ee333-106">This account can be an Azure Active Directory account or a Microsoft ID, like an email account from outlook.com or hotmail.com.</span></span>

<span data-ttu-id="ee333-107">要创建 PowerShell 库帐户，请转到 [https://PowerShellGallery.com](https://PowerShellGallery.com)，然后单击“登录”，如下图所示  。</span><span class="sxs-lookup"><span data-stu-id="ee333-107">To create a PowerShell Gallery account, go to [https://PowerShellGallery.com](https://PowerShellGallery.com) and click on **Sign in** as shown in the following image.</span></span>

![注册新帐户](../../Images/CreateAccount-Register.png)

<span data-ttu-id="ee333-109">若要使用 Azure Active Directory 帐户，请选择“工作或学校帐户”，并使用帐户登录  。</span><span class="sxs-lookup"><span data-stu-id="ee333-109">To use an Azure Active Directory account, select **Work or School Account**, and sign in with your account.</span></span> <span data-ttu-id="ee333-110">若要使用 Microsoft ID，请选择“个人帐户”并登录  。</span><span class="sxs-lookup"><span data-stu-id="ee333-110">To use a Microsoft ID, choose **Personal Account** and sign in.</span></span>

<span data-ttu-id="ee333-111">接下来系统便会提示创建 PowerShell 库帐户的用户名。</span><span class="sxs-lookup"><span data-stu-id="ee333-111">Next, you are prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="ee333-112">查看使用条款和隐私策略，输入用户名，然后单击“注册”  。</span><span class="sxs-lookup"><span data-stu-id="ee333-112">Review the Terms of Use and Privacy Policy, enter a username, and then click **Register**.</span></span>

> [!NOTE]
> <span data-ttu-id="ee333-113">帐户名称一旦创建便无法再进行更改。</span><span class="sxs-lookup"><span data-stu-id="ee333-113">The account name cannot be changed once it is created.</span></span> <span data-ttu-id="ee333-114">有关详细信息，请参阅[管理包所有者](managing-package-owners.md)。</span><span class="sxs-lookup"><span data-stu-id="ee333-114">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="ee333-115">适用于 PowerShell 库帐户的推荐做法</span><span class="sxs-lookup"><span data-stu-id="ee333-115">Recommended practices for PowerShell Gallery accounts</span></span>

<span data-ttu-id="ee333-116">请务必确保可主动监视对 PowerShell 库帐户使用的电子邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="ee333-116">It's important to actively monitor the email account used with your PowerShell Gallery account.</span></span> <span data-ttu-id="ee333-117">与 PowerShell 库包所有者之间的所有通信均通过此电子邮件地址进行。</span><span class="sxs-lookup"><span data-stu-id="ee333-117">All communication with owners of PowerShell Gallery packages is through this email address.</span></span> <span data-ttu-id="ee333-118">若 PowerShell 库运营团队无法联系包所有者，我们可能需要删除包。</span><span class="sxs-lookup"><span data-stu-id="ee333-118">If the PowerShell Gallery Operations team is unable to contact a package owner, we may be required to delete a package.</span></span>

<span data-ttu-id="ee333-119">出于此目的，发布到 PowerShell 库的组织通常会创建唯一外部帐户。</span><span class="sxs-lookup"><span data-stu-id="ee333-119">Organizations that publish to the PowerShell Gallery often create a unique external account for that purpose.</span></span> <span data-ttu-id="ee333-120">我们建议使用电子邮件转发功能将通知转发到组织内的地址。</span><span class="sxs-lookup"><span data-stu-id="ee333-120">We recommend you use email forwarding to forward notifications to an address within your organization.</span></span>

<span data-ttu-id="ee333-121">当多个所有者与包关联时，会向所有所有者发送所有 PowerShell 库通知。</span><span class="sxs-lookup"><span data-stu-id="ee333-121">When multiple owners are associated with a package, all PowerShell Gallery notifications are sent to all owners.</span></span> <span data-ttu-id="ee333-122">有关详细信息，请参阅[管理包所有者](managing-package-owners.md)。</span><span class="sxs-lookup"><span data-stu-id="ee333-122">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>
