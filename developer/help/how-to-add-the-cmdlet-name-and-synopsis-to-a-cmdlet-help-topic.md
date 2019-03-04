---
title: 如何将 Cmdlet 名称和摘要添加到 Cmdlet 帮助主题 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861823"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="87eb3-102">如何向 Cmdlet 帮助主题添加 Cmdlet 名称和摘要</span><span class="sxs-lookup"><span data-stu-id="87eb3-102">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="87eb3-103">本部分介绍如何添加的 cmdlet 帮助在名称和摘要部分中显示的内容。</span><span class="sxs-lookup"><span data-stu-id="87eb3-103">This section describes how to add content that is displayed in the NAME and SYNOPSIS sections of the cmdlet help.</span></span> <span data-ttu-id="87eb3-104">在帮助文件中，此内容添加到每个 cmdlet 的命令节点。</span><span class="sxs-lookup"><span data-stu-id="87eb3-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="87eb3-105">查看完整的帮助文件，打开一个 dll Help.xml 文件位于 Windows PowerShell 安装目录。</span><span class="sxs-lookup"><span data-stu-id="87eb3-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="87eb3-106">例如，Microsoft.PowerShell.Commands.Management.dll Help.xml 文件包含内容的多个 Windows PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="87eb3-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="87eb3-107">若要添加的 Cmdlet 名称和摘要</span><span class="sxs-lookup"><span data-stu-id="87eb3-107">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="87eb3-108">Cmdlet 帮助可以显示两个 cmdlet 的说明。</span><span class="sxs-lookup"><span data-stu-id="87eb3-108">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="87eb3-109">第一个描述是被称为摘要的简短说明。</span><span class="sxs-lookup"><span data-stu-id="87eb3-109">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="87eb3-110">第二个说明是更详细的说明中所讨论[添加到 Cmdlet 帮助主题的详细说明](./how-to-add-a-cmdlet-description.md)。</span><span class="sxs-lookup"><span data-stu-id="87eb3-110">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span> <span data-ttu-id="87eb3-111">这两个这些说明应编写为一个段落。</span><span class="sxs-lookup"><span data-stu-id="87eb3-111">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="87eb3-112">摘要不会重复 cmdlet 名称。</span><span class="sxs-lookup"><span data-stu-id="87eb3-112">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="87eb3-113">通知用户 Get-server cmdlet 获取的服务器是简短，但不是提供信息。</span><span class="sxs-lookup"><span data-stu-id="87eb3-113">Informing the user that the Get-Server cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="87eb3-114">相反，使用同义词功能，并添加到说明的详细信息。</span><span class="sxs-lookup"><span data-stu-id="87eb3-114">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="87eb3-115">例如："获取一个对象，表示本地或远程计算机"。</span><span class="sxs-lookup"><span data-stu-id="87eb3-115">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="87eb3-116">使用简单的谓词，如"get"、"创建"和"更改"摘要。</span><span class="sxs-lookup"><span data-stu-id="87eb3-116">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="87eb3-117">避免使用"设置"，因为它是含糊不清，和复杂单词如"修改。"</span><span class="sxs-lookup"><span data-stu-id="87eb3-117">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="87eb3-118">例如："在文件中获取有关验证码签名的信息。"</span><span class="sxs-lookup"><span data-stu-id="87eb3-118">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="87eb3-119">编写使用主动语态。</span><span class="sxs-lookup"><span data-stu-id="87eb3-119">Write in active voice.</span></span> <span data-ttu-id="87eb3-120">例如，"使用 TimeSpan 对象..."是更清晰，不是"时间跨度对象可用于..."</span><span class="sxs-lookup"><span data-stu-id="87eb3-120">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="87eb3-121">描述 cmdlet 获取对象时避免"display"的谓词。</span><span class="sxs-lookup"><span data-stu-id="87eb3-121">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="87eb3-122">尽管 Windows PowerShell 会显示 cmdlet 的数据，但是非常重要，向用户介绍该 cmdlet 将返回可能不会显示其数据的.NET Framework 对象的概念。</span><span class="sxs-lookup"><span data-stu-id="87eb3-122">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="87eb3-123">如果突出显示，请用户可能不知道，该 cmdlet 返回可能返回的许多其他有用的属性和方法不会显示。</span><span class="sxs-lookup"><span data-stu-id="87eb3-123">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="87eb3-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="87eb3-124">See Also</span></span>

 [<span data-ttu-id="87eb3-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="87eb3-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)