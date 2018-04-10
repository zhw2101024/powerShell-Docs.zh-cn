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
## <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="d1481-103">创建 PowerShell 库帐户</span><span class="sxs-lookup"><span data-stu-id="d1481-103">Creating a PowerShell Gallery Account</span></span>

<span data-ttu-id="d1481-104">必须先创建 PowerShell 库帐户，然后才能将任何内容发布到 PowerShell 库。</span><span class="sxs-lookup"><span data-stu-id="d1481-104">A PowerShell Gallery account must be established before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="d1481-105">必须将 PowerShell 库帐户与启用电子邮件的 Azure Active Directory 帐户或域名为 outlook.com、hotmail.com 等的 Microsoft 电子邮件帐户相关联。</span><span class="sxs-lookup"><span data-stu-id="d1481-105">The PowerShell Gallery accounts must be linked to an Azure Active Directory email-enabled account, or a Microsoft email account (with a domain of outlook.com, hotmail.com, etc.)</span></span>

<span data-ttu-id="d1481-106">若要创建 PowerShell 库帐户，请转到 https://PowerShellGallery.com，再单击“注册”（见下图）。</span><span class="sxs-lookup"><span data-stu-id="d1481-106">To create a PowerShell Gallery account, go to https://PowerShellGallery.com and click on "Register" (see the image below).</span></span>

![注册新帐户](./images/CreatingAccount-Register.png)

<span data-ttu-id="d1481-108">若要使用 Azure Active Directory 帐户，请在下一页中选择“工作或学校帐户”，并使用帐户登录。</span><span class="sxs-lookup"><span data-stu-id="d1481-108">In the next page, to use an Azure Active Directory account, select "Work or School Account", and log in with your account.</span></span>
<span data-ttu-id="d1481-109">若要使用 Microsoft 帐户（如域名为 Hotmail.com 或 Outlook.com 的帐户），请选择“个人帐户”并登录。</span><span class="sxs-lookup"><span data-stu-id="d1481-109">To use a Microsoft account - such as one in a Hotmail.com or Outlook.com domain - choose "Personal Account", and log in.</span></span>

<span data-ttu-id="d1481-110">登录后，系统便会提示创建 PowerShell 库帐户的用户名。</span><span class="sxs-lookup"><span data-stu-id="d1481-110">Once you have logged in, you will be prompted to create a username for the PowerShell Gallery.</span></span>
<span data-ttu-id="d1481-111">查看链接的使用条款和隐私策略，输入用户名，再单击“注册”。</span><span class="sxs-lookup"><span data-stu-id="d1481-111">Review the Terms of Use and Privacy Policy that are linked in, enter a username, and then click Register.</span></span>

<span data-ttu-id="d1481-112">注意：帐户名称一旦创建便无法再进行更改。</span><span class="sxs-lookup"><span data-stu-id="d1481-112">Note: This account name cannot be changed once it is created.</span></span>
<span data-ttu-id="d1481-113">请参阅[管理项所有者](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners)，了解与此相关的其他详细信息。</span><span class="sxs-lookup"><span data-stu-id="d1481-113">See [Managing Item Owners](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) for additional details related to this.</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="d1481-114">适用于 PowerShell 库帐户的推荐做法</span><span class="sxs-lookup"><span data-stu-id="d1481-114">Recommended Practices for PowerShell Gallery Accounts</span></span>

<span data-ttu-id="d1481-115">请务必确保可以主动监视对 PowerShell 库帐户使用的电子邮件帐户。</span><span class="sxs-lookup"><span data-stu-id="d1481-115">It is important that the email account used with your PowerShell Gallery account be actively monitored.</span></span>
<span data-ttu-id="d1481-116">将使用与 PowerShell 库帐户关联的电子邮件地址通过电子邮件的方式与 PowerShell 库项的所有者进行所有通信往来。</span><span class="sxs-lookup"><span data-stu-id="d1481-116">All communiction with owners of PowerShell Gallery items is through the email using the address associated with your PowerShell Gallery account.</span></span>
<span data-ttu-id="d1481-117">如果我们无法联系项所有者，在某些情况下，运营团队可能需要删除项。</span><span class="sxs-lookup"><span data-stu-id="d1481-117">If we are unable to contact an item owner, the Operations team may be required to delete an item under some circumstances.</span></span>

<span data-ttu-id="d1481-118">出于此目的，发布到 PowerShell 库的组织通常都会在 Outlook.com 或其他 Microsoft 帐户域中创建唯一帐户。</span><span class="sxs-lookup"><span data-stu-id="d1481-118">Organizations that publish to the PowerShell Gallery often create a unique account for that purpose in Outlook.com, or another Microsoft account domain.</span></span>
<span data-ttu-id="d1481-119">在许多情况下，都不会定期监视此帐户。</span><span class="sxs-lookup"><span data-stu-id="d1481-119">In many cases that account is not regularly monitored.</span></span>
<span data-ttu-id="d1481-120">在这种情况下，最佳做法是使用 Outlook 转发功能将电子邮件转发到另一个帐户（通常是组织内受项所有者监视的帐户）。</span><span class="sxs-lookup"><span data-stu-id="d1481-120">A best practice in that case is to use Outlook Forwarding to send email to another account, typically one within the organization, that will be monitored by the item owner(s).</span></span>

<span data-ttu-id="d1481-121">如果项有多个关联的所有者，那么来自 PowerShell 库的所有通信都会发送给全部所有者。</span><span class="sxs-lookup"><span data-stu-id="d1481-121">If there are multiple owners associated with an item, all communications that come from the PowerShell Gallery will go to all owners.</span></span>
<span data-ttu-id="d1481-122">请参阅[管理项所有者](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners)，详细了解如何向项添加所有者。</span><span class="sxs-lookup"><span data-stu-id="d1481-122">See [Managing Item Owners](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) for additional details on adding owners to an item.</span></span>