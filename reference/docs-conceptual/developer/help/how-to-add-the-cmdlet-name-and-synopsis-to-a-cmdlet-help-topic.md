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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361186"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="20c5e-102">如何向 Cmdlet 帮助主题添加 Cmdlet 名称和摘要</span><span class="sxs-lookup"><span data-stu-id="20c5e-102">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="20c5e-103">本部分介绍如何添加在 cmdlet 帮助的 "名称" 和 "概要" 部分中显示的内容。</span><span class="sxs-lookup"><span data-stu-id="20c5e-103">This section describes how to add content that is displayed in the NAME and SYNOPSIS sections of the cmdlet help.</span></span> <span data-ttu-id="20c5e-104">在帮助文件中，此内容将添加到每个 cmdlet 的命令节点。</span><span class="sxs-lookup"><span data-stu-id="20c5e-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="20c5e-105">若要获取帮助文件的完整视图，请打开位于 Windows PowerShell 安装目录中的 dll-Help 文件之一。</span><span class="sxs-lookup"><span data-stu-id="20c5e-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="20c5e-106">例如，dll-Help 文件包含多个 Windows PowerShell cmdlet 的内容，则不会。</span><span class="sxs-lookup"><span data-stu-id="20c5e-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="20c5e-107">添加 Cmdlet 名称和摘要</span><span class="sxs-lookup"><span data-stu-id="20c5e-107">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="20c5e-108">Cmdlet 帮助可以为 cmdlet 显示两个描述。</span><span class="sxs-lookup"><span data-stu-id="20c5e-108">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="20c5e-109">第一个说明是称为 "摘要" 的简短说明。</span><span class="sxs-lookup"><span data-stu-id="20c5e-109">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="20c5e-110">第二个说明是在[将详细描述添加到 Cmdlet 帮助主题](./how-to-add-a-cmdlet-description.md)中所述的更详细说明。</span><span class="sxs-lookup"><span data-stu-id="20c5e-110">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span> <span data-ttu-id="20c5e-111">这两个说明应作为一个段落来编写。</span><span class="sxs-lookup"><span data-stu-id="20c5e-111">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="20c5e-112">在 "摘要" 中，不重复 cmdlet 名称。</span><span class="sxs-lookup"><span data-stu-id="20c5e-112">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="20c5e-113">向用户通知获取服务器 cmdlet 获取服务器非常简短，但没有提示信息。</span><span class="sxs-lookup"><span data-stu-id="20c5e-113">Informing the user that the Get-Server cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="20c5e-114">请改用同义词并向说明添加详细信息。</span><span class="sxs-lookup"><span data-stu-id="20c5e-114">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="20c5e-115">示例： "获取表示本地或远程计算机的对象。"</span><span class="sxs-lookup"><span data-stu-id="20c5e-115">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="20c5e-116">使用摘要中的简单谓词，例如 "get"、"create" 和 "change"。</span><span class="sxs-lookup"><span data-stu-id="20c5e-116">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="20c5e-117">避免使用 "set"，因为它不明确，如 "修改"。</span><span class="sxs-lookup"><span data-stu-id="20c5e-117">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="20c5e-118">示例： "获取有关文件中 Authenticode 签名的信息。"</span><span class="sxs-lookup"><span data-stu-id="20c5e-118">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="20c5e-119">写入活动的语音。</span><span class="sxs-lookup"><span data-stu-id="20c5e-119">Write in active voice.</span></span> <span data-ttu-id="20c5e-120">例如，"使用 TimeSpan 对象 ..."比 "可使用 TimeSpan 对象 ..." 更清晰。</span><span class="sxs-lookup"><span data-stu-id="20c5e-120">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="20c5e-121">描述用于获取对象的 cmdlet 时，应避免出现 "显示" 谓词。</span><span class="sxs-lookup"><span data-stu-id="20c5e-121">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="20c5e-122">虽然 Windows PowerShell 显示 cmdlet 数据，但向用户介绍 cmdlet 会返回 .NET Framework 对象（这些对象的数据可能不会显示），这一点很重要。</span><span class="sxs-lookup"><span data-stu-id="20c5e-122">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="20c5e-123">如果您强调显示，用户可能不会意识到该 cmdlet 可能返回了许多其他有用的属性和未显示的方法。</span><span class="sxs-lookup"><span data-stu-id="20c5e-123">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="20c5e-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="20c5e-124">See Also</span></span>

 [<span data-ttu-id="20c5e-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="20c5e-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)