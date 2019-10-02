---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: 取消列出包
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328268"
---
# <a name="unlisting-packages"></a><span data-ttu-id="0a4ad-103">取消列出包</span><span class="sxs-lookup"><span data-stu-id="0a4ad-103">Unlisting Packages</span></span>

<span data-ttu-id="0a4ad-104">为什么未显示从 PowerShell 库删除包的选项？ </span><span class="sxs-lookup"><span data-stu-id="0a4ad-104">**Why is removing a package from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="0a4ad-105">PowerShell 库不支持用户永久删除其包。</span><span class="sxs-lookup"><span data-stu-id="0a4ad-105">The PowerShell Gallery does not support users permanently deleting their packages.</span></span>
<span data-ttu-id="0a4ad-106">这让其他人能够依赖你的包而无需担心将来可能产生的中断。</span><span class="sxs-lookup"><span data-stu-id="0a4ad-106">This enables others to take dependencies on your packages without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="0a4ad-107">例如，如果 Pester 模块依赖 Azure 模块，而 Azure 模块从库中删除，那么用户将不能使用 Pester 模块。</span><span class="sxs-lookup"><span data-stu-id="0a4ad-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="0a4ad-108">无法删除包，但可将其取消列出。</span><span class="sxs-lookup"><span data-stu-id="0a4ad-108">Instead of removing an package, however, you can unlist it instead.</span></span>

<span data-ttu-id="0a4ad-109">在 PowerShell 库中取消列出包的作用是什么？ </span><span class="sxs-lookup"><span data-stu-id="0a4ad-109">**What does unlisting a package on PowerShell Gallery do?**</span></span>

<span data-ttu-id="0a4ad-110">在 PowerShell 库中取消列出包（例如模块或脚本）会将其从“包”选项卡中移除。此外，使用搜索栏将无法发现取消列出的包。</span><span class="sxs-lookup"><span data-stu-id="0a4ad-110">Unlisting a package such as module or script on PowerShell Gallery will remove it from the Packages tab. In addition, unlisted packages will not be discoverable using the search bar.</span></span>
<span data-ttu-id="0a4ad-111">下载取消列出的包的唯一方法是指定包的确切名称和版本。</span><span class="sxs-lookup"><span data-stu-id="0a4ad-111">The only way to download an unlisted package is to specify the exact name and version of the package.</span></span>
<span data-ttu-id="0a4ad-112">因此，取消列出的包将不会中断依赖它的其他模块或脚本。</span><span class="sxs-lookup"><span data-stu-id="0a4ad-112">Because of this, the unlisting of an package will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="0a4ad-113">若要取消列出包，可访问包详细信息页，选择“删除模块”。</span><span class="sxs-lookup"><span data-stu-id="0a4ad-113">To unlist your package, visit the package details page and select 'Delete Module'.</span></span> <span data-ttu-id="0a4ad-114">取消选中“列出”复选框，单击“保存”。</span><span class="sxs-lookup"><span data-stu-id="0a4ad-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="0a4ad-115">如何移除包？ </span><span class="sxs-lookup"><span data-stu-id="0a4ad-115">**How can I remove an package?**</span></span>

<span data-ttu-id="0a4ad-116">如果遇到有必要删除包的情况，请与 PowerShell 库管理员联系。</span><span class="sxs-lookup"><span data-stu-id="0a4ad-116">If you experience a scenario where package deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="0a4ad-117">正当的删除情况包括：</span><span class="sxs-lookup"><span data-stu-id="0a4ad-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="0a4ad-118">侵犯版权问题。</span><span class="sxs-lookup"><span data-stu-id="0a4ad-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="0a4ad-119">包包含可能有害的内容。</span><span class="sxs-lookup"><span data-stu-id="0a4ad-119">Package contains potentially harmful content.</span></span>
- <span data-ttu-id="0a4ad-120">包包含敏感数据。</span><span class="sxs-lookup"><span data-stu-id="0a4ad-120">Package contains sensitive data.</span></span>

<span data-ttu-id="0a4ad-121">若要向 PowerShell 库管理员提交删除包请求，请访问包的详细信息页并选择“联系支持人员”。</span><span class="sxs-lookup"><span data-stu-id="0a4ad-121">To submit a Delete Package Request to the PowerShell Gallery Administrators, visit your package's detail page and select Contact Support.</span></span>
