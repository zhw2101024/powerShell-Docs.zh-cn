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
# <a name="powershell-gallery-gdpr-compliance"></a><span data-ttu-id="141c8-103">PowerShell 库 GDPR 符合性</span><span class="sxs-lookup"><span data-stu-id="141c8-103">PowerShell Gallery GDPR compliance</span></span>

## <a name="overview"></a><span data-ttu-id="141c8-104">概述</span><span class="sxs-lookup"><span data-stu-id="141c8-104">Overview</span></span>

<span data-ttu-id="141c8-105">2018 年 5 月，名为“一般数据保护条例 (GDPR)”的欧洲隐私法生效。</span><span class="sxs-lookup"><span data-stu-id="141c8-105">In May 2018, a European privacy law, the General Data Protection Regulation (GDPR), took effect.</span></span>
<span data-ttu-id="141c8-106">GDPR 规定了公司、政府机构、公益组织以及负责以下事务的其他组织需要遵守的新规则：为欧盟民众提供商品和服务，或收集和分析与欧盟民众相关的数据。</span><span class="sxs-lookup"><span data-stu-id="141c8-106">The GDPR imposes new rules on companies, government agencies, non-profits, and other organizations that offer goods and services to people in the European Union (EU), or that collect and analyze data tied to EU residents.</span></span>
<span data-ttu-id="141c8-107">GDPR 的适用对象不受地理位置限制。</span><span class="sxs-lookup"><span data-stu-id="141c8-107">The GDPR applies no matter where you are located.</span></span>

> [!NOTE]
> <span data-ttu-id="141c8-108">本文提供有关如何从 PowerShell 库删除个人数据的步骤，并可用于支持你在 GDPR 约束下的义务。</span><span class="sxs-lookup"><span data-stu-id="141c8-108">This article provides steps for how to delete personal data from the PowerShell Gallery and can be used to support your obligations under the GDPR.</span></span> <span data-ttu-id="141c8-109">如果要了解 GDPR 的一般信息，请参阅[服务信任门户的 GDPR 部分](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted)。</span><span class="sxs-lookup"><span data-stu-id="141c8-109">If you’re looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span></span>

## <a name="personally-identifiable-data"></a><span data-ttu-id="141c8-110">个人身份数据</span><span class="sxs-lookup"><span data-stu-id="141c8-110">Personally identifiable data</span></span>

<span data-ttu-id="141c8-111">PowerShell 库存储以下可能由用户提供的信息，信息中可能包含个人信息：</span><span class="sxs-lookup"><span data-stu-id="141c8-111">The PowerShell Gallery stores the following information that may be provided by users, which may contain personal information:</span></span>

- <span data-ttu-id="141c8-112">PowerShell 库帐户</span><span class="sxs-lookup"><span data-stu-id="141c8-112">PowerShell Gallery account</span></span>
- <span data-ttu-id="141c8-113">发布到 PowerShell 库的包</span><span class="sxs-lookup"><span data-stu-id="141c8-113">Packages published to the PowerShell Gallery</span></span>
- <span data-ttu-id="141c8-114">与 PowerShell 库团队的电子邮件通信</span><span class="sxs-lookup"><span data-stu-id="141c8-114">Email correspondence with the PowerShell Gallery team</span></span>

<span data-ttu-id="141c8-115">大多数用户不创建 PowerShell 库帐户。</span><span class="sxs-lookup"><span data-stu-id="141c8-115">Most users do not create a PowerShell Gallery account.</span></span>
<span data-ttu-id="141c8-116">除非要发布包或使用 PowerShell 库中的“联系所有者”功能，否则不需要帐户。</span><span class="sxs-lookup"><span data-stu-id="141c8-116">An account is not required unless you are going to publish a package or use the "Contact Owner" feature in the PowerShell Gallery.</span></span>
<span data-ttu-id="141c8-117">除了用户发起的电子邮件通信，PowerShell 库不保存未创建帐户的用户的个人身份数据。</span><span class="sxs-lookup"><span data-stu-id="141c8-117">Other than email correspondence initiated by the user, the PowerShell Gallery does not store personally identifiable data for users who have not created an account.</span></span>

<span data-ttu-id="141c8-118">创建 PowerShell 库帐户的用户可以将包发布到 PowerShell 库。</span><span class="sxs-lookup"><span data-stu-id="141c8-118">Users who create a PowerShell Gallery account can publish packages to the PowerShell Gallery.</span></span>
<span data-ttu-id="141c8-119">这些包都应为 PowerShell 代码，但也可能包含其他信息，包括个人信息。</span><span class="sxs-lookup"><span data-stu-id="141c8-119">Those packages are expected to be PowerShell code, but may contain other information including personal information.</span></span>
<span data-ttu-id="141c8-120">以下信息将显示如何获取已发布到 PowerShell 库的所有包。</span><span class="sxs-lookup"><span data-stu-id="141c8-120">The information below will show how you can get all the packages you have published to the PowerShell Gallery.</span></span>

## <a name="dsr-export-of-powershell-gallery-data"></a><span data-ttu-id="141c8-121">PowerShell 库数据的 DSR 导出</span><span class="sxs-lookup"><span data-stu-id="141c8-121">DSR Export of PowerShell Gallery Data</span></span>

<span data-ttu-id="141c8-122">以下各节介绍 PowerShell 库如何支持数据主体请求 (DSR)，其中涉及如何导出保存在 PowerShell 库中的信息，以及如何请求删除此信息。</span><span class="sxs-lookup"><span data-stu-id="141c8-122">The following sections describe how the PowerShell Gallery supports data subject requests (DSR), by explaining how to export information stored in the PowerShell Gallery, and how to request deletion of this information.</span></span>

### <a name="email"></a><span data-ttu-id="141c8-123">电子邮件</span><span class="sxs-lookup"><span data-stu-id="141c8-123">Email</span></span>

<span data-ttu-id="141c8-124">电子邮件通信可能包括以下任一项：</span><span class="sxs-lookup"><span data-stu-id="141c8-124">Email correspondence may include any of the following:</span></span>

- <span data-ttu-id="141c8-125">如果代码分析扫描检测到已发布到 PowerShell 库的包存在问题，则会向 PowerShell 库包的所有者发送电子邮件</span><span class="sxs-lookup"><span data-stu-id="141c8-125">Email sent to the owners of PowerShell Gallery packages if the code analysis scans detected an issue with any package they have published to the PowerShell Gallery</span></span>
- <span data-ttu-id="141c8-126">任何人使用“联系我们”页面中的电子邮件地址 ([cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)) 向 PowerShell 库团队发送电子邮件</span><span class="sxs-lookup"><span data-stu-id="141c8-126">Email sent by anyone to the PowerShell Gallery team using the email address in the "Contact Us" page [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)</span></span>
- <span data-ttu-id="141c8-127">注册用户使用 PowerShell 库中的“联系所有者”功能，向 PowerShell 库中某个包的所有者发送电子邮件</span><span class="sxs-lookup"><span data-stu-id="141c8-127">Registered users who use the "Contact Owner" feature in the PowerShell Gallery to send email to the owner of a package in the PowerShell Gallery</span></span>

<span data-ttu-id="141c8-128">PowerShell 库发送和接收的电子邮件具有 90 天的保留策略，以支持 PowerShell 库中发现恶意代码时进行可能的安全调查。</span><span class="sxs-lookup"><span data-stu-id="141c8-128">Emails sent by or to the PowerShell Gallery have a retention policy of 90 days to support possible security investigations should malicious code be discovered on the PowerShell Gallery.</span></span>
<span data-ttu-id="141c8-129">根据策略，电子邮件会在 90 天后删除。</span><span class="sxs-lookup"><span data-stu-id="141c8-129">Emails are deleted by policy after 90 days.</span></span>

<span data-ttu-id="141c8-130">可以请求过去 90 天里，你的电子邮件地址和 PowerShell 库发送和接收的所有电子邮件副本。</span><span class="sxs-lookup"><span data-stu-id="141c8-130">You may request copies of all emails sent to or from your email address and the PowerShell Gallery within the previous 90 days.</span></span>
<span data-ttu-id="141c8-131">若要请求这种对应关系，请发送电子邮件至 [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)，标题为：“此帐户相关电子邮件的 DSR 请求”。</span><span class="sxs-lookup"><span data-stu-id="141c8-131">To request this correspondence, send an email to [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com), with the title: "DSR Request for emails relating to this account".</span></span>
<span data-ttu-id="141c8-132">请在邮件正文中说明请求的信息（例如：请发送所有发送到或接收自此电子邮件地址的电子邮件。）请求日期前 90 天与你的电子邮件地址有关的所有电子邮件将在 7 个工作日内发送。</span><span class="sxs-lookup"><span data-stu-id="141c8-132">In the body of the message, state what information you are requesting (for example: Please send all emails sent to or received from this email address.) All emails involving your email address within 90 days of the request will be sent within 7 business days.</span></span>

### <a name="powershell-gallery-account-information"></a><span data-ttu-id="141c8-133">PowerShell 库帐户信息</span><span class="sxs-lookup"><span data-stu-id="141c8-133">PowerShell Gallery Account Information</span></span>

<span data-ttu-id="141c8-134">如果已创建 PowerShell 库帐户，可通过以下步骤查找存储在 PowerShell 库中的所有个人信息：</span><span class="sxs-lookup"><span data-stu-id="141c8-134">If you have created a PowerShell Gallery account, you can find all personal information that has been stored in PowerShell Gallery by taking the following steps:</span></span>

1. <span data-ttu-id="141c8-135">登录 PowerShell 库，然后单击你的用户名</span><span class="sxs-lookup"><span data-stu-id="141c8-135">Sign in to the PowerShell Gallery, then click on your username</span></span>
2. <span data-ttu-id="141c8-136">显示的下一页为帐户页，将显示用于 PowerShell 库帐户的电子邮件地址</span><span class="sxs-lookup"><span data-stu-id="141c8-136">The next page displayed is the Account page, which shows the email address used for the PowerShell Gallery account</span></span>

<span data-ttu-id="141c8-137">如果已在 PowerShell 库中创建多个帐户，则需要为每个帐户重复执行这些步骤。</span><span class="sxs-lookup"><span data-stu-id="141c8-137">If you have created more than one account in the PowerShell Gallery, you will need to repeat these steps for each account.</span></span>

### <a name="packages-in-the-powershell-gallery"></a><span data-ttu-id="141c8-138">PowerShell 库中的包</span><span class="sxs-lookup"><span data-stu-id="141c8-138">Packages in the PowerShell Gallery</span></span>

<span data-ttu-id="141c8-139">为了导出发布到 PowerShell 库的包，我们已将脚本“GetPSGalleryItemsForAuthor”发布到 PowerShell 库。</span><span class="sxs-lookup"><span data-stu-id="141c8-139">To facilitate exporting packages published to the PowerShell Gallery, we have published the script "GetPSGalleryItemsForAuthor" to the PowerShell Gallery.</span></span>
<span data-ttu-id="141c8-140">此脚本基于包中存储的作者信息，导出 PowerShell 库上的每个包的所有版本副本。</span><span class="sxs-lookup"><span data-stu-id="141c8-140">This script exports a copy of every version of every package put into the PowerShell Gallery based on the author information stored in the package.</span></span>

> [!NOTE]
> <span data-ttu-id="141c8-141">发布包时，包清单中将存储作者。</span><span class="sxs-lookup"><span data-stu-id="141c8-141">The Author is stored in the package manifest when you publish your package.</span></span>
> <span data-ttu-id="141c8-142">不保证该创建者与 PowerShell 库中使用的帐户是相同身份。</span><span class="sxs-lookup"><span data-stu-id="141c8-142">There is no guarantee that the Author is the same identity as the account you use in the PowerShell Gallery.</span></span>
> <span data-ttu-id="141c8-143">如果“创建者”字段使用其他值，则需要在使用此脚本时提供此值。</span><span class="sxs-lookup"><span data-stu-id="141c8-143">If you use some other value in the Author field, you will need to supply that value when using this script.</span></span>

<span data-ttu-id="141c8-144">可使用以下 PowerShell 命令来下载该脚本：</span><span class="sxs-lookup"><span data-stu-id="141c8-144">You may download the script by using the following PowerShell command:</span></span>

```powershell
Save-Script Get-repository psgallery
```

<span data-ttu-id="141c8-145">可通过运行以下 PowerShell 命令直接运行该脚本：</span><span class="sxs-lookup"><span data-stu-id="141c8-145">You can then run the script directly, by running the following PowerShell commands:</span></span>

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

<span data-ttu-id="141c8-146">系统会提示你提供作者以及要在系统上保存包的文件夹。</span><span class="sxs-lookup"><span data-stu-id="141c8-146">You will be prompted to supply the Author and a folder on your system where you want the packages to be saved.</span></span>

## <a name="deleting-personal-data-from-the-powershell-gallery"></a><span data-ttu-id="141c8-147">从 PowerShell 库中删除个人数据</span><span class="sxs-lookup"><span data-stu-id="141c8-147">Deleting Personal Data From The PowerShell Gallery</span></span>

<span data-ttu-id="141c8-148">若要删除 PowerShell 库帐户或你在 PowerShell 库中拥有的任何包，请发送电子邮件至 cgadmin@microsoft.com，标题为：“此帐户相关项目的 GDPR 请求”。</span><span class="sxs-lookup"><span data-stu-id="141c8-148">To delete your PowerShell Gallery account or any package you own in the PowerShell Gallery, send email to cgadmin@microsoft.com with the title: "GDPR Request for items relating to this account".</span></span>
<span data-ttu-id="141c8-149">请在邮件正文中说明要删除哪些信息。</span><span class="sxs-lookup"><span data-stu-id="141c8-149">In the body of the message state what information you want deleted.</span></span> <span data-ttu-id="141c8-150">例如：</span><span class="sxs-lookup"><span data-stu-id="141c8-150">For example:</span></span>

- <span data-ttu-id="141c8-151">请删除我的包“包名称”的版本 x.y.z</span><span class="sxs-lookup"><span data-stu-id="141c8-151">Please delete version x.y.z of my package "package name"</span></span>
- <span data-ttu-id="141c8-152">请删除我的包“包名称”的所有版本</span><span class="sxs-lookup"><span data-stu-id="141c8-152">Please delete all versions of my package "package name"</span></span>
- <span data-ttu-id="141c8-153">请删除我的 PowerShell 库帐户</span><span class="sxs-lookup"><span data-stu-id="141c8-153">Please delete my PowerShell Gallery account</span></span>

<span data-ttu-id="141c8-154">PowerShell 库管理员将在 7 个工作日内回复。</span><span class="sxs-lookup"><span data-stu-id="141c8-154">The PowerShell Gallery administrators will reply within 7 business days.</span></span>
<span data-ttu-id="141c8-155">在发送请求后的 30 天内，将删除指定的包。</span><span class="sxs-lookup"><span data-stu-id="141c8-155">The packages specified will be deleted within 30 days after the request is sent.</span></span>
