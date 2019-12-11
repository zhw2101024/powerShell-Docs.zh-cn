---
ms.date: 09/10/2018
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: 管理 API 密钥
ms.openlocfilehash: 954eb27c25babdb8efe50c13caf5f2d287c6b3e3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328288"
---
# <a name="managing-api-keys"></a><span data-ttu-id="55625-103">管理 API 密钥</span><span class="sxs-lookup"><span data-stu-id="55625-103">Managing API keys</span></span>

<span data-ttu-id="55625-104">PowerShell 库支持创建多个 API 密钥以支持一系列发布要求。</span><span class="sxs-lookup"><span data-stu-id="55625-104">The PowerShell Gallery supports creating multiple API keys to support a range of publishing requirements.</span></span> <span data-ttu-id="55625-105">API 密钥可应用于一个或多个包，授予特定权限，并具有到期日期。</span><span class="sxs-lookup"><span data-stu-id="55625-105">An API key can apply to one or more packages, grants specific privileges, and has an expiration date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="55625-106">在引入作用域 API 密钥之前发布到 PowerShell 库的用户将具有“完全访问 API 密钥”。</span><span class="sxs-lookup"><span data-stu-id="55625-106">Users who published to the PowerShell Gallery prior to the introduction of scoped API keys will have a "Full access API key".</span></span> <span data-ttu-id="55625-107">完全访问密钥没有内置于作用域 API 密钥的安全性改进。</span><span class="sxs-lookup"><span data-stu-id="55625-107">The full access keys do not have the security improvements built into scoped API keys.</span></span> <span data-ttu-id="55625-108">完全访问密钥永不过期并适用于用户拥有的所有内容。</span><span class="sxs-lookup"><span data-stu-id="55625-108">The full access keys never expires and apply to everything owned by the user.</span></span> <span data-ttu-id="55625-109">若删除此密钥，则无法重新创建。</span><span class="sxs-lookup"><span data-stu-id="55625-109">If you delete this key, it cannot be recreated.</span></span>

<span data-ttu-id="55625-110">下图显示了创建作用域 API 密钥时可用的选项。</span><span class="sxs-lookup"><span data-stu-id="55625-110">The following image shows the options available when creating a scoped API key.</span></span>

![正在创建 API 密钥](../../Images/PSGallery_KeyScoped.png)

<span data-ttu-id="55625-112">在此示例中，我们创建了一个名为 AzureRMDataFactory 的 API 密钥  。</span><span class="sxs-lookup"><span data-stu-id="55625-112">In this example, we created an API key named **AzureRMDataFactory**.</span></span> <span data-ttu-id="55625-113">此密钥值可用于推送名称以“AzureRM.DataFactory”开头并且有效期为 365 天的包。</span><span class="sxs-lookup"><span data-stu-id="55625-113">This key value can be used to push packages with names that begin with 'AzureRM.DataFactory' and is valid for 365 days.</span></span> <span data-ttu-id="55625-114">这是同一组织中不同团队处理不同包的典型方案。</span><span class="sxs-lookup"><span data-stu-id="55625-114">This is a typical scenario when different teams within the same organization work on different packages.</span></span> <span data-ttu-id="55625-115">团队成员拥有密钥，可授予他们所处理的特定包的权限。</span><span class="sxs-lookup"><span data-stu-id="55625-115">The members of the team have a key that grants them privileges for the specific package they work on.</span></span>
<span data-ttu-id="55625-116">到期值可防止使用过期或遗忘的密钥。</span><span class="sxs-lookup"><span data-stu-id="55625-116">The expiration value prevents the use of stale or forgotten keys.</span></span>

## <a name="using-glob-patterns"></a><span data-ttu-id="55625-117">使用 glob 模式</span><span class="sxs-lookup"><span data-stu-id="55625-117">Using glob patterns</span></span>

<span data-ttu-id="55625-118">若要处理多个包，可使用通配模式将多个包作为一个组进行匹配。</span><span class="sxs-lookup"><span data-stu-id="55625-118">If you work on multiple packages, you can use globbing patterns to match multiple packages as a group.</span></span> <span data-ttu-id="55625-119">API 密钥权限适用于与 glob 模式匹配的所有新建包。</span><span class="sxs-lookup"><span data-stu-id="55625-119">API key permissions apply to all new packages matching the glob pattern.</span></span> <span data-ttu-id="55625-120">例如，前面的示例使用“AzureRM.DataFactory \*”的 Glob 模式值  。</span><span class="sxs-lookup"><span data-stu-id="55625-120">For example, the previous example uses a **Glob Pattern** value of 'AzureRM.DataFactory\*'.</span></span> <span data-ttu-id="55625-121">可使用此密钥推送名为“AzureRm.DataFactoryV2.Netcore”的包，因为该包与 glob 模式匹配。</span><span class="sxs-lookup"><span data-stu-id="55625-121">You can push a package named 'AzureRm.DataFactoryV2.Netcore' using this key since the package matches the glob pattern.</span></span>

## <a name="create-api-keys-securely"></a><span data-ttu-id="55625-122">安全创建 API 密钥</span><span class="sxs-lookup"><span data-stu-id="55625-122">Create API keys securely</span></span>

<span data-ttu-id="55625-123">为了安全起见，屏幕上永远不会显示新创建的密钥值，只能使用“复制”按钮，如下所示。</span><span class="sxs-lookup"><span data-stu-id="55625-123">For security, a newly created key value is never shown on the screen and is only available with the Copy button, as shown below.</span></span>

![获取新的 API 密钥值](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> <span data-ttu-id="55625-125">只可在创建或刷新后立即复制 API 密钥值。</span><span class="sxs-lookup"><span data-stu-id="55625-125">You can only copy the API key value immediately after creating or refreshing it.</span></span> <span data-ttu-id="55625-126">将不会显示该密钥值，且无法在刷新页面后再次访问。</span><span class="sxs-lookup"><span data-stu-id="55625-126">It will not be displayed, and will not be accessible again after the page is refreshed.</span></span> <span data-ttu-id="55625-127">若丢失了密钥值，则必须使用“重新生成”，并在重新生成后复制该密钥。</span><span class="sxs-lookup"><span data-stu-id="55625-127">If you lose the key value, you must use Regenerate, and copy the key after it is regenerated.</span></span>

## <a name="key-permissions-and-expiration"></a><span data-ttu-id="55625-128">密钥权限和到期时间</span><span class="sxs-lookup"><span data-stu-id="55625-128">Key permissions and expiration</span></span>

<span data-ttu-id="55625-129">作用域 API 密钥可分配以下任何权限：</span><span class="sxs-lookup"><span data-stu-id="55625-129">Scoped API keys can assign any of the following permissions:</span></span>

- <span data-ttu-id="55625-130">推送新建包</span><span class="sxs-lookup"><span data-stu-id="55625-130">Push new packages</span></span>
- <span data-ttu-id="55625-131">推送新建包或更新包</span><span class="sxs-lookup"><span data-stu-id="55625-131">Push new or update packages</span></span>
- <span data-ttu-id="55625-132">取消列出包</span><span class="sxs-lookup"><span data-stu-id="55625-132">Unlist packages</span></span>

<span data-ttu-id="55625-133">每个新密钥都有到期时间。</span><span class="sxs-lookup"><span data-stu-id="55625-133">Every new key has an expiration.</span></span> <span data-ttu-id="55625-134">到期时间以天为单位。</span><span class="sxs-lookup"><span data-stu-id="55625-134">The expiration value is measured in days.</span></span> <span data-ttu-id="55625-135">到期时间的值可能为：</span><span class="sxs-lookup"><span data-stu-id="55625-135">The possible values for expiration are:</span></span>

- <span data-ttu-id="55625-136">1 天</span><span class="sxs-lookup"><span data-stu-id="55625-136">1 day</span></span>
- <span data-ttu-id="55625-137">90 天</span><span class="sxs-lookup"><span data-stu-id="55625-137">90 days</span></span>
- <span data-ttu-id="55625-138">180 天</span><span class="sxs-lookup"><span data-stu-id="55625-138">180 days</span></span>
- <span data-ttu-id="55625-139">270 天</span><span class="sxs-lookup"><span data-stu-id="55625-139">270 days</span></span>
- <span data-ttu-id="55625-140">365 天（默认值）</span><span class="sxs-lookup"><span data-stu-id="55625-140">365 days (default)</span></span>

<span data-ttu-id="55625-141">创建密钥后，不能更改这些设置。</span><span class="sxs-lookup"><span data-stu-id="55625-141">These settings cannot be changed once the key is created.</span></span> <span data-ttu-id="55625-142">无法创建永不过期的新密钥。</span><span class="sxs-lookup"><span data-stu-id="55625-142">You cannot create a new key that never expires.</span></span>

## <a name="editing-and-deleting-existing-api-keys"></a><span data-ttu-id="55625-143">编辑和删除现有 API 密钥</span><span class="sxs-lookup"><span data-stu-id="55625-143">Editing and deleting existing API keys</span></span>

<span data-ttu-id="55625-144">可更改现有密钥的某些设置。</span><span class="sxs-lookup"><span data-stu-id="55625-144">You can change some settings of an existing key.</span></span> <span data-ttu-id="55625-145">如上文所述，无法修改现有 API 密钥的安全作用域或更改到期时间。</span><span class="sxs-lookup"><span data-stu-id="55625-145">As previously noted, you cannot modify the security scope for an existing API key or change the expiration.</span></span> <span data-ttu-id="55625-146">可更改的选项如下面的屏幕截图所示：</span><span class="sxs-lookup"><span data-stu-id="55625-146">The changeable options are shown in the following screenshot:</span></span>

![获取新的 API 密钥值](../../Images/PSGallery_EditAPIKey.png)

<span data-ttu-id="55625-148">若要更改由密钥控制的包，可从列表中选择单个包，或更改 glob 模式。</span><span class="sxs-lookup"><span data-stu-id="55625-148">To change the packages controlled by a key, you can choose individual packages from the list or change the glob pattern.</span></span>

<span data-ttu-id="55625-149">单击“重新生成”创建一个新密钥值  。</span><span class="sxs-lookup"><span data-stu-id="55625-149">Clicking **Regenerate** creates a new key value.</span></span> <span data-ttu-id="55625-150">就像最初创建密钥时一样，必须在更新后立即“复制”密钥值  。</span><span class="sxs-lookup"><span data-stu-id="55625-150">Just like when you initially created the key, you must **Copy** the key value immediately after updating it.</span></span> <span data-ttu-id="55625-151">离开此页后，“复制”选项不可用  。</span><span class="sxs-lookup"><span data-stu-id="55625-151">The **Copy** option is not available once you leave this page.</span></span>

<span data-ttu-id="55625-152">单击“删除”将显示一条确认消息  。</span><span class="sxs-lookup"><span data-stu-id="55625-152">Clicking **Delete** displays a confirmation message.</span></span> <span data-ttu-id="55625-153">删除密钥后，密钥将不可用。</span><span class="sxs-lookup"><span data-stu-id="55625-153">Once a key is deleted, it will be unusable.</span></span>

## <a name="key-expiration"></a><span data-ttu-id="55625-154">密钥到期时间</span><span class="sxs-lookup"><span data-stu-id="55625-154">Key expiration</span></span>

<span data-ttu-id="55625-155">在到期前十天，PowerShell 库会向 API 密钥的帐户持有者发送警告电子邮件。</span><span class="sxs-lookup"><span data-stu-id="55625-155">Ten days before the expiration, the PowerShell Gallery sends a warning email the account holder of the API key.</span></span> <span data-ttu-id="55625-156">到期后，该密钥将不可用。</span><span class="sxs-lookup"><span data-stu-id="55625-156">After expiration, the key is unusable.</span></span> <span data-ttu-id="55625-157">API 密钥管理页面顶部将显示一条警告消息，显示不再有效的密钥。</span><span class="sxs-lookup"><span data-stu-id="55625-157">A warning message is displayed at the top of the API key management page showing which keys are no longer valid.</span></span> <span data-ttu-id="55625-158">可生成一个新密钥值。</span><span class="sxs-lookup"><span data-stu-id="55625-158">You can generate a new key value.</span></span>
