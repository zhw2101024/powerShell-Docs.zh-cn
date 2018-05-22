---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: 管理项所有者
ms.openlocfilehash: 10d2a433253162847028e157b5bac47b23406469
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="managing-item-owners"></a><span data-ttu-id="64e53-103">管理项所有者</span><span class="sxs-lookup"><span data-stu-id="64e53-103">Managing item owners</span></span>

<span data-ttu-id="64e53-104">由将项发布到库的人定义 PowerShell 中项的所有权。</span><span class="sxs-lookup"><span data-stu-id="64e53-104">Ownership of an item in the PowerShell Gallery is defined by who published the item to the gallery.</span></span>
<span data-ttu-id="64e53-105">有时需要在初始项发布之外管理此元数据，这意味着所有者元数据需要是可变的，而项本身不需要。</span><span class="sxs-lookup"><span data-stu-id="64e53-105">Sometimes this metadata needs to be managed beyond the initial item publishing, which means the owner metadata needs to be mutable while the item itself is not.</span></span>

<span data-ttu-id="64e53-106">所有项所有者是对等的。</span><span class="sxs-lookup"><span data-stu-id="64e53-106">All item owners are peers.</span></span>
<span data-ttu-id="64e53-107">这意味着任何项所有者都可发布项的新版本。</span><span class="sxs-lookup"><span data-stu-id="64e53-107">This means any item owner can publish a new version of an item.</span></span> <span data-ttu-id="64e53-108">这还意味着任何项所有者可以删除任何其他所有者。</span><span class="sxs-lookup"><span data-stu-id="64e53-108">It also means that any item owner can remove any other item owner.</span></span>
<span data-ttu-id="64e53-109">每个所有者的权利相同。</span><span class="sxs-lookup"><span data-stu-id="64e53-109">No owner has more authority than other owners.</span></span>

## <a name="setting-an-items-initial-owner"></a><span data-ttu-id="64e53-110">设置项的初始所有者</span><span class="sxs-lookup"><span data-stu-id="64e53-110">Setting an Item's Initial Owner</span></span>

<span data-ttu-id="64e53-111">当新项发布到 PowerShell 库时，由发布项的用户定义初始所有者。</span><span class="sxs-lookup"><span data-stu-id="64e53-111">When a new item is published to PowerShell Gallery, the initial owner is defined by the user that published the item.</span></span> <span data-ttu-id="64e53-112">这根据 Publish-Module cmdlet 中使用谁的 API 密钥决定。</span><span class="sxs-lookup"><span data-stu-id="64e53-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="64e53-113">添加所有者</span><span class="sxs-lookup"><span data-stu-id="64e53-113">Adding Owners</span></span>

<span data-ttu-id="64e53-114">将项发布到 PowerShell 库后，可轻松邀请其他用户成为项的所有者。</span><span class="sxs-lookup"><span data-stu-id="64e53-114">Once an item has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of an item.</span></span>

1. <span data-ttu-id="64e53-115">使用项的当前所有者的帐户[登录](https://powershellgallery.com/users/account/LogOn) PowerShell 库。</span><span class="sxs-lookup"><span data-stu-id="64e53-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of an item.</span></span>
2. <span data-ttu-id="64e53-116">通过使用“项”选项卡、搜索或单击你的用户名，然后单击[**“管理我的项”**](https://www.powershellgallery.com/account/Packages)，导航到项页面。</span><span class="sxs-lookup"><span data-stu-id="64e53-116">Navigate to an item page using the 'Items' tab, searching, or clicking your username and then [**Manage My Items**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="64e53-117">以项的所有者身份登录时，左侧有“管理所有者”链接可以单击。</span><span class="sxs-lookup"><span data-stu-id="64e53-117">When logged on as an item's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="64e53-118">输入要添加为所有者的人员的用户名，并单击“添加”。</span><span class="sxs-lookup"><span data-stu-id="64e53-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="64e53-119">随后将向新的共同所有者发送一封电子邮件，作为成为项的所有者的邀请函。</span><span class="sxs-lookup"><span data-stu-id="64e53-119">An email is then sent to the new co-owner, as an invitation to become an owner of an item.</span></span>
6. <span data-ttu-id="64e53-120">该用户单击此链接后，将成为对项具有完全控制权的完全共同所有者，其控制权包括删除其他用户所有者身份的能力。</span><span class="sxs-lookup"><span data-stu-id="64e53-120">Once that user clicks the link, they are a full co-owner with full control over an item, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="64e53-121">**注意**：新的所有者必须先确认所有权，否则*不会*列为项的所有者。</span><span class="sxs-lookup"><span data-stu-id="64e53-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of an item.</span></span>
<span data-ttu-id="64e53-122">查看“管理所有者”页面时，你将在当前所有者中看到“等待审批”条目。</span><span class="sxs-lookup"><span data-stu-id="64e53-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="64e53-123">可以删除该邀请；同样也可以删除其他所有者。</span><span class="sxs-lookup"><span data-stu-id="64e53-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="64e53-124">此邀请过程可防止用户错误地将其他用户添加为其项的所有者。</span><span class="sxs-lookup"><span data-stu-id="64e53-124">This process of invitations prevents users from falsely adding other users as owners of their items.</span></span>

<span data-ttu-id="64e53-125">注意：“Authors”元数据是完全自由文本；仅“Owners”受控。</span><span class="sxs-lookup"><span data-stu-id="64e53-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="64e53-126">删除所有者</span><span class="sxs-lookup"><span data-stu-id="64e53-126">Removing Owners</span></span>

<span data-ttu-id="64e53-127">如果项具有多个所有者而需删除其中之一，过程很简单：</span><span class="sxs-lookup"><span data-stu-id="64e53-127">When an item has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="64e53-128">使用项的当前所有者的帐户[登录](https://powershellgallery.com/users/account/LogOn) PowerShell 库；</span><span class="sxs-lookup"><span data-stu-id="64e53-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of an item;</span></span>
2. <span data-ttu-id="64e53-129">通过使用“项”选项卡、搜索或单击你的用户名，然后单击[**“管理我的项”**](https://www.powershellgallery.com/account/Packages)，导航到项页面。</span><span class="sxs-lookup"><span data-stu-id="64e53-129">Navigate to an item page using the Items tab, searching, or clicking your username and then [**Manage My Items**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="64e53-130">如果以项的所有者身份登录，左侧有“管理所有者”链接可以单击；</span><span class="sxs-lookup"><span data-stu-id="64e53-130">When logged on as an item's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="64e53-131">单击要删除的所有者旁边的“删除”链接。</span><span class="sxs-lookup"><span data-stu-id="64e53-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-item-ownership"></a><span data-ttu-id="64e53-132">转移项所有权</span><span class="sxs-lookup"><span data-stu-id="64e53-132">Transferring Item Ownership</span></span>

<span data-ttu-id="64e53-133">我们时而收到将项所有权从一个用户转移到另一个用户的支持请求，但你几乎始终可自己完成该操作。</span><span class="sxs-lookup"><span data-stu-id="64e53-133">We sometimes get support requests to transfer item ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="64e53-134">将所有权从一个用户转移到另一个用户只是以上两种功能的组合。</span><span class="sxs-lookup"><span data-stu-id="64e53-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="64e53-135">当前所有者邀请新用户成为共同所有者，新用户接受邀请；</span><span class="sxs-lookup"><span data-stu-id="64e53-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="64e53-136">新用户将旧用户从所有者列表中删除。</span><span class="sxs-lookup"><span data-stu-id="64e53-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="64e53-137">此请求有多种形式，但过程相同。</span><span class="sxs-lookup"><span data-stu-id="64e53-137">This request has come in under a couple forms but the process works the same.</span></span>

- <span data-ttu-id="64e53-138">项所有者从一个开发人员更改为另一个开发人员</span><span class="sxs-lookup"><span data-stu-id="64e53-138">The item ownership is changing from one developer to another</span></span>
- <span data-ttu-id="64e53-139">使用错误帐户意外发布了项</span><span class="sxs-lookup"><span data-stu-id="64e53-139">The item was accidentally published using the wrong account</span></span>


## <a name="orphaned-items"></a><span data-ttu-id="64e53-140">孤立的项</span><span class="sxs-lookup"><span data-stu-id="64e53-140">Orphaned Items</span></span>

<span data-ttu-id="64e53-141">最后一种情况曾经出现，但次数不多。</span><span class="sxs-lookup"><span data-stu-id="64e53-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="64e53-142">项变得孤立，唯一的项所有者帐户不能用于添加新所有者。</span><span class="sxs-lookup"><span data-stu-id="64e53-142">Items have become orphans and the only item owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="64e53-143">以下是本场景的一些示例：</span><span class="sxs-lookup"><span data-stu-id="64e53-143">Here are some examples of this scenario:</span></span>

- <span data-ttu-id="64e53-144">所有者帐户与不再存在的电子邮件地址关联，且用户忘记其密码</span><span class="sxs-lookup"><span data-stu-id="64e53-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
- <span data-ttu-id="64e53-145">生成项的已注册所有者已离开公司，无法与其联系以更新项所有权</span><span class="sxs-lookup"><span data-stu-id="64e53-145">The registered owner has left the company that produces the item and cannot be reached to update the item ownership</span></span>
- <span data-ttu-id="64e53-146">由于仅影响少量的项的 bug，项在库中无所有者</span><span class="sxs-lookup"><span data-stu-id="64e53-146">Due to a bug that has only affected a handful of items, the item is somehow ownerless on the gallery</span></span>

<span data-ttu-id="64e53-147">PowerShell 库管理员可以访问任何项的“管理所有者”链接。</span><span class="sxs-lookup"><span data-stu-id="64e53-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any item.</span></span>
<span data-ttu-id="64e53-148">如果你是项的合法所有者，而无法联系当前所有者以获取所有权，可使用库中的“报告滥用行为”链接与 PowerShell 库管理员联系。</span><span class="sxs-lookup"><span data-stu-id="64e53-148">If you are the rightful owner of a item and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="64e53-149">然后，我们将按流程验证你对该项的所有权。</span><span class="sxs-lookup"><span data-stu-id="64e53-149">We will then follow a process to verify your ownership of the item.</span></span>
<span data-ttu-id="64e53-150">如果我们确定你应为该项的所有者，我们将使用该项的“管理所有者”链接，向你发送成为所有者的邀请。</span><span class="sxs-lookup"><span data-stu-id="64e53-150">If we determine you should be an owner of the item, we will use the 'Manage Owners' link for the item ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="64e53-151">我们将仅在验证你应为所有者后才执行此操作，此过程因具体情况而异。</span><span class="sxs-lookup"><span data-stu-id="64e53-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="64e53-152">通常，我们将使用项的项目 URL 设法联系项目所有者，但我们也可能使用 Twitter、电子邮件或其他方式联系项目所有者。</span><span class="sxs-lookup"><span data-stu-id="64e53-152">Often times, we will use the item's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>