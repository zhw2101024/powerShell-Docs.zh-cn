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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369976"
---
# <a name="cmdlet-aliases"></a><span data-ttu-id="99276-102">Cmdlet 别名</span><span class="sxs-lookup"><span data-stu-id="99276-102">Cmdlet Aliases</span></span>

<span data-ttu-id="99276-103">可以使用 cmdlet 别名来改善 cmdlet 用户体验。</span><span class="sxs-lookup"><span data-stu-id="99276-103">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="99276-104">你可以将别名添加到常用的 cmdlet，以减少键入并更轻松地完成任务。</span><span class="sxs-lookup"><span data-stu-id="99276-104">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="99276-105">可以在 cmdlet 中包含内置别名，或者用户可以定义自己的自定义别名。</span><span class="sxs-lookup"><span data-stu-id="99276-105">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="99276-106">例如， [get-help](/powershell/module/microsoft.powershell.core/get-command) cmdlet 具有内置 `gcm` 别名。</span><span class="sxs-lookup"><span data-stu-id="99276-106">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="99276-107">你还可以使用别名来添加其他语言的命令名称，以便用户无需了解新的命令。</span><span class="sxs-lookup"><span data-stu-id="99276-107">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="99276-108">别名指南</span><span class="sxs-lookup"><span data-stu-id="99276-108">Alias Guidelines</span></span>

<span data-ttu-id="99276-109">为 cmdlet 创建内置别名时，请遵循以下准则：</span><span class="sxs-lookup"><span data-stu-id="99276-109">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="99276-110">在分配别名之前，请启动 Windows PowerShell，然后运行[获取别名](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias)cmdlet 以查看已使用的别名。</span><span class="sxs-lookup"><span data-stu-id="99276-110">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="99276-111">包含一个别名前缀，该前缀引用 cmdlet 名称的谓词和引用 cmdlet 名称名词的别名后缀。</span><span class="sxs-lookup"><span data-stu-id="99276-111">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="99276-112">例如，`Import-Module` cmdlet 的别名为 "ipmo"。</span><span class="sxs-lookup"><span data-stu-id="99276-112">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="99276-113">有关所有谓词及其别名的列表，请参阅[Cmdlet 谓词](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="99276-113">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="99276-114">对于具有相同谓词的 cmdlet，请包含相同的别名前缀。</span><span class="sxs-lookup"><span data-stu-id="99276-114">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="99276-115">例如，其名称中具有 "Get" 谓词的所有 Windows PowerShell cmdlet 的别名均使用 "g" 前缀。</span><span class="sxs-lookup"><span data-stu-id="99276-115">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="99276-116">对于具有相同名词的 cmdlet，请包含相同的别名后缀。</span><span class="sxs-lookup"><span data-stu-id="99276-116">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="99276-117">例如，名称中包含 "Session" 名词的所有 Windows PowerShell cmdlet 的别名均使用 "sn" 后缀。</span><span class="sxs-lookup"><span data-stu-id="99276-117">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="99276-118">对于等效于其他语言中的命令的 cmdlet，请使用命令的名称。</span><span class="sxs-lookup"><span data-stu-id="99276-118">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="99276-119">通常，请尽可能缩短别名。</span><span class="sxs-lookup"><span data-stu-id="99276-119">In general, make aliases as short as possible.</span></span> <span data-ttu-id="99276-120">请确保该别名至少具有一个用于该谓词的非重复字符和名词的一个不同字符。</span><span class="sxs-lookup"><span data-stu-id="99276-120">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="99276-121">根据需要添加更多字符，使别名唯一。</span><span class="sxs-lookup"><span data-stu-id="99276-121">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="99276-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="99276-122">See Also</span></span>

[<span data-ttu-id="99276-123">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="99276-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
