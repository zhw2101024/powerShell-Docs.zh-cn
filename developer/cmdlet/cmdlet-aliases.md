---
title: Cmdlet 别名 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068704"
---
# <a name="cmdlet-aliases"></a><span data-ttu-id="5754f-102">Cmdlet 别名</span><span class="sxs-lookup"><span data-stu-id="5754f-102">Cmdlet Aliases</span></span>

<span data-ttu-id="5754f-103">可以使用 cmdlet 别名来提高 cmdlet 的用户体验。</span><span class="sxs-lookup"><span data-stu-id="5754f-103">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="5754f-104">可以将别名添加到常用 cmdlet 来减少键入，快速使其能够更轻松地完成任务。</span><span class="sxs-lookup"><span data-stu-id="5754f-104">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="5754f-105">您可以在你的 cmdlet，包括内置别名或用户可以定义自己的自定义别名。</span><span class="sxs-lookup"><span data-stu-id="5754f-105">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="5754f-106">例如， [Get-command](/powershell/module/microsoft.powershell.core/get-command) cmdlet 具有内置`gcm`别名。</span><span class="sxs-lookup"><span data-stu-id="5754f-106">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="5754f-107">别名还可用于从其他语言添加命令名称，以便用户无需了解新的命令。</span><span class="sxs-lookup"><span data-stu-id="5754f-107">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="5754f-108">别名指导原则</span><span class="sxs-lookup"><span data-stu-id="5754f-108">Alias Guidelines</span></span>

<span data-ttu-id="5754f-109">为 cmdlet 创建内置的别名时，请遵循以下准则：</span><span class="sxs-lookup"><span data-stu-id="5754f-109">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="5754f-110">分配别名之前，启动 Windows PowerShell，然后运行[Get-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet 以查看已使用的别名。</span><span class="sxs-lookup"><span data-stu-id="5754f-110">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="5754f-111">包含引用的谓词的 cmdlet 名称和引用的名词的 cmdlet 名称的别名后缀别名前缀。</span><span class="sxs-lookup"><span data-stu-id="5754f-111">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="5754f-112">例如，对于别名`Import-Module`cmdlet 是"ipmo"。</span><span class="sxs-lookup"><span data-stu-id="5754f-112">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="5754f-113">所有谓词和其别名的列表，请参阅[Cmdlet 谓词](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="5754f-113">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="5754f-114">对于具有相同的谓词的 cmdlet，包括相同的别名前缀。</span><span class="sxs-lookup"><span data-stu-id="5754f-114">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="5754f-115">例如，其名称中包含"Get"谓词的所有 Windows PowerShell cmdlet 的别名使用"g"前缀。</span><span class="sxs-lookup"><span data-stu-id="5754f-115">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="5754f-116">对于具有相同的名词的 cmdlet，包括相同的别名后缀。</span><span class="sxs-lookup"><span data-stu-id="5754f-116">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="5754f-117">例如，具有"会话"名词名称中的所有 Windows PowerShell cmdlet 的别名中使用"sn 表示"后缀。</span><span class="sxs-lookup"><span data-stu-id="5754f-117">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="5754f-118">对于等效于其他语言中的命令的 cmdlet，使用该命令的名称。</span><span class="sxs-lookup"><span data-stu-id="5754f-118">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="5754f-119">一般情况下，请尽可能短的别名。</span><span class="sxs-lookup"><span data-stu-id="5754f-119">In general, make aliases as short as possible.</span></span> <span data-ttu-id="5754f-120">请确保该别名具有至少一个独特的字符的谓词和名词的一个独特的字符。</span><span class="sxs-lookup"><span data-stu-id="5754f-120">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="5754f-121">添加更多的字符，以使唯一别名。</span><span class="sxs-lookup"><span data-stu-id="5754f-121">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="5754f-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5754f-122">See Also</span></span>

[<span data-ttu-id="5754f-123">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5754f-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
