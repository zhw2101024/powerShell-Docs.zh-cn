---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: 库,powershell,cmdlet,psgallery
title: 通过社交媒体或发表评论提供反馈
ms.openlocfilehash: 79f1450337b9ed5bb0687494fe1ed7c2d87f1bb5
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="providing-feedback-via-social-media-or-comments"></a><span data-ttu-id="3e996-103">通过社交媒体或发表评论提供反馈</span><span class="sxs-lookup"><span data-stu-id="3e996-103">Providing Feedback via social media or comments</span></span>

<span data-ttu-id="3e996-104">Powershell 库支持以下两种反馈方法，以便用户能够提供有关项的公共反馈：</span><span class="sxs-lookup"><span data-stu-id="3e996-104">The Powershell Gallery supports two approaches for users to provide public feedback on an item:</span></span>

- <span data-ttu-id="3e996-105">使用左侧边缘的链接，在 Facebook、LinkedIn 或 Twitter 社交媒体网站中“分享”项；</span><span class="sxs-lookup"><span data-stu-id="3e996-105">Use the links on the left edge to "share" an item in Facebook, LinkedIn, or Twitter social media sites;</span></span>
- <span data-ttu-id="3e996-106">使用评论功能对项发表评论，并允许作者查看已对项发表的评论。</span><span class="sxs-lookup"><span data-stu-id="3e996-106">Use the Comment feature to post comments on an item, and to allow Authors to watch for comments on items they publish.</span></span>

## <a name="social-media-feedback"></a><span data-ttu-id="3e996-107">社交媒体反馈</span><span class="sxs-lookup"><span data-stu-id="3e996-107">Social Media Feedback</span></span>

<span data-ttu-id="3e996-108">对于 PowerShell 库中的每一项，网页左侧都有 Facebook、LinkedIn 和 Twitter 链接。</span><span class="sxs-lookup"><span data-stu-id="3e996-108">On the left side of the page for each item in the PowerShell Gallery there are links for Facebook, LinkedIn, and Twitter.</span></span>
<span data-ttu-id="3e996-109">单击这些链接可以打开社交媒体网站，并能快速分享项链接。</span><span class="sxs-lookup"><span data-stu-id="3e996-109">Clicking on these links will open the social media site, and allow quickly sharing a link to the item.</span></span>

<span data-ttu-id="3e996-110">用户必须登录已选择的网站，才能分享 PowerShell 库项。</span><span class="sxs-lookup"><span data-stu-id="3e996-110">Users must log in to the site they have chosen in order to share the PowerShell Gallery item.</span></span>

<span data-ttu-id="3e996-111">如果用户认为需要向他人推荐项，建议这样做。</span><span class="sxs-lookup"><span data-stu-id="3e996-111">Users are encouraged to do this if they find that an item is something they would recommend to others.</span></span>
<span data-ttu-id="3e996-112">PowerShell 库将检查每个用于“分享”项的社交媒体网站，并显示相应项在每个社交媒体网站中的分享次数。</span><span class="sxs-lookup"><span data-stu-id="3e996-112">The PowerShell Gallery will check each social media site for "shares" of the item, and display how many times that item has been shared in each of the social media sites.</span></span>
<span data-ttu-id="3e996-113">由于只显示分享次数，因此其他用户可以看作是“赞”相应项的次数。</span><span class="sxs-lookup"><span data-stu-id="3e996-113">Since this shows only the count of times something has been shared, it will be intepreted other users as "liking" the item.</span></span>


## <a name="comments"></a><span data-ttu-id="3e996-114">说明</span><span class="sxs-lookup"><span data-stu-id="3e996-114">Comments</span></span>

<span data-ttu-id="3e996-115">PowerShell 库使用 LiveFyre 服务来允许用户对项发表评论。</span><span class="sxs-lookup"><span data-stu-id="3e996-115">The PowerShell Gallery uses the LiveFyre service to allow users to comment on items.</span></span>
<span data-ttu-id="3e996-116">如果需要提供建议或反馈，用户可以使用此功能提供对项网页的所有访问者都可见的反馈。</span><span class="sxs-lookup"><span data-stu-id="3e996-116">Users who have recommendations or feedback can use this feature to provide feedback that is visible to anyone who visits the item page.</span></span>
<span data-ttu-id="3e996-117">项所有者可以关注此反馈，并在有人发表评论时收到通知。</span><span class="sxs-lookup"><span data-stu-id="3e996-117">Item owners can Follow this feedback, and be notified when someone posts a comment.</span></span>

<span data-ttu-id="3e996-118">评论系统基于 LiveFyre，这是不受 Microsoft 管理的独立服务，要求使用唯一登录名。</span><span class="sxs-lookup"><span data-stu-id="3e996-118">The Comment system is based on LiveFyre, which is a separate service that is not managed by Microsoft, and requires unique login to use.</span></span>
<span data-ttu-id="3e996-119">首次选择对一个项发表评论或关注评论时，系统会提示创建 LiveFyre 帐户。</span><span class="sxs-lookup"><span data-stu-id="3e996-119">The first time you choose to leave a comment or Follow comments on one of your items, you will be prompted to create a LiveFyre account.</span></span>

<span data-ttu-id="3e996-120">如果已经创建 LiveFyre 帐户并登录，可以编写评论以提供项反馈，再单击“发表评论...”。评论不会立即可见。</span><span class="sxs-lookup"><span data-stu-id="3e996-120">If you have created a LiveFyre account and logged in, you can craft a comment that provides feedback on the item, then click on "Post comment..." The comment will not be visible immediately.</span></span>
<span data-ttu-id="3e996-121">PowerShell 库管理员会审核库项的评论，要发表的所有评论都会先经由审查方审核，然后才会发表并对其他人可见。</span><span class="sxs-lookup"><span data-stu-id="3e996-121">Comments for gallery items are moderated by the PowerShell Gallery administrators, and all posts are reviewed by the moderators before being published and visible to others.</span></span>
<span data-ttu-id="3e996-122">之所以要审核评论是为了确保它们符合 PowerShell 库[使用条款](https://www.powershellgallery.com/policies/Terms)规定的公共行为。</span><span class="sxs-lookup"><span data-stu-id="3e996-122">Our purpose in moderating the comments is to ensure that they align with public behavior consistent with the PowerShell Gallery [Terms of Use](https://www.powershellgallery.com/policies/Terms).</span></span>

<span data-ttu-id="3e996-123">建议项所有者关注在 LiveFyre 中发表的评论。</span><span class="sxs-lookup"><span data-stu-id="3e996-123">Item owners are encouraged to Follow comments that are posted to LiveFyre.</span></span>
<span data-ttu-id="3e996-124">必须创建 LiveFyre 帐户，建议使用在 LiveFyre 中发布项时所用的同一电子邮件地址。</span><span class="sxs-lookup"><span data-stu-id="3e996-124">A LiveFyre account is required, and it is recommended to use the same email address you use for publishing your item in LiveFyre.</span></span>
<span data-ttu-id="3e996-125">若要关注评论，请先登录 LiveFyre，再转到你被列为所有者的任意项。</span><span class="sxs-lookup"><span data-stu-id="3e996-125">To Follow comments, log into LiveFyre, and navigate to any item where you are listed as an Owner.</span></span>
<span data-ttu-id="3e996-126">在每个项底部的评论框下方，都会看到“+关注”。</span><span class="sxs-lookup"><span data-stu-id="3e996-126">Below the Comment box at the bottom of each item you will see "+Follow".</span></span>
<span data-ttu-id="3e996-127">单击此按钮后，LiveFyre 便会在有人对此项发表新评论时向注册的电子邮件地址发送电子邮件。</span><span class="sxs-lookup"><span data-stu-id="3e996-127">Once you click on this, LiveFyre will send an email to the registered email address any time new comments made on the item.</span></span>