---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: 库,powershell,cmdlet,psgallery
title: 取消列出项
ms.openlocfilehash: 35dcd283ddace5aec62d692b0ede12ae0bada765
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="unlisting-items"></a><span data-ttu-id="6dba1-103">取消列出项</span><span class="sxs-lookup"><span data-stu-id="6dba1-103">Unlisting items</span></span>

<span data-ttu-id="6dba1-104">**为什么未显示从 PowerShell 库删除项的选项？**</span><span class="sxs-lookup"><span data-stu-id="6dba1-104">**Why is removing an item from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="6dba1-105">PowerShell 库不支持用户永久删除其项。</span><span class="sxs-lookup"><span data-stu-id="6dba1-105">The PowerShell Gallery does not support users permanently deleting their items.</span></span>
<span data-ttu-id="6dba1-106">这让其他人能够依赖你的项而无需担心将来可能产生的中断。</span><span class="sxs-lookup"><span data-stu-id="6dba1-106">This enables others to take dependencies on your items without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="6dba1-107">例如，如果 Pester 模块依赖 Azure 模块，而 Azure 模块从库中删除，那么用户将不能使用 Pester 模块。</span><span class="sxs-lookup"><span data-stu-id="6dba1-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="6dba1-108">你无法删除项，但可将其取消列出。</span><span class="sxs-lookup"><span data-stu-id="6dba1-108">Instead of removing an item, however, you can unlist it instead.</span></span>

<span data-ttu-id="6dba1-109">**在 PowerShell 库中取消列出项的作用是什么？**</span><span class="sxs-lookup"><span data-stu-id="6dba1-109">**What does unlisting an item on PowerShell Gallery do?**</span></span>

<span data-ttu-id="6dba1-110">在 PowerShell 库中取消列出项（例如模块或脚本）会将其从“项”选项卡中删除。此外，使用搜索栏将无法发现取消列出的项。</span><span class="sxs-lookup"><span data-stu-id="6dba1-110">Unlisting an item such as module or script on PowerShell Gallery will remove it from the Items tab. In addition, unlisted items will not be discoverable using the search bar.</span></span>
<span data-ttu-id="6dba1-111">下载取消列出的项的唯一方法是指定项的精确名称和版本。</span><span class="sxs-lookup"><span data-stu-id="6dba1-111">The only way to download an unlisted item is to specify the exact name and version of the item.</span></span>
<span data-ttu-id="6dba1-112">因此，取消列出的项将不会破坏依赖它的其他模块或脚本。</span><span class="sxs-lookup"><span data-stu-id="6dba1-112">Because of this, the unlisting of an item will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="6dba1-113">若要取消列出项，可访问项详细信息页，选择“删除项”。</span><span class="sxs-lookup"><span data-stu-id="6dba1-113">To unlist your item, visit the item details page and select 'Delete Item'.</span></span> <span data-ttu-id="6dba1-114">取消选中“列出”复选框，单击“保存”。</span><span class="sxs-lookup"><span data-stu-id="6dba1-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="6dba1-115">**如何删除项？**</span><span class="sxs-lookup"><span data-stu-id="6dba1-115">**How can I remove an item?**</span></span>

<span data-ttu-id="6dba1-116">如果你遇到有必要删除项的情况，请与 PowerShell 库管理员联系。</span><span class="sxs-lookup"><span data-stu-id="6dba1-116">If you experience a scenario where item deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="6dba1-117">正当的删除情况包括：</span><span class="sxs-lookup"><span data-stu-id="6dba1-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="6dba1-118">侵犯版权问题。</span><span class="sxs-lookup"><span data-stu-id="6dba1-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="6dba1-119">项包含可能有害的内容。</span><span class="sxs-lookup"><span data-stu-id="6dba1-119">Item contains potentially harmful content.</span></span>
- <span data-ttu-id="6dba1-120">项包含敏感数据。</span><span class="sxs-lookup"><span data-stu-id="6dba1-120">Item contains sensitive data.</span></span>

<span data-ttu-id="6dba1-121">若要向 PowerShell 库管理员提交删除项请求，请访问项的详细信息页面并选择“联系支持人员”。</span><span class="sxs-lookup"><span data-stu-id="6dba1-121">To submit a Delete Item Request to the PowerShell Gallery Administrators, visit your item's detail page and select Contact Support.</span></span>