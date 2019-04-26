---
title: 如何添加的 Cmdlet 说明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083512"
---
# <a name="how-to-add-a-cmdlet-description"></a><span data-ttu-id="468c0-102">如何添加 Cmdlet 说明</span><span class="sxs-lookup"><span data-stu-id="468c0-102">How to Add a Cmdlet Description</span></span>

<span data-ttu-id="468c0-103">本部分介绍如何添加的 cmdlet 帮助描述部分中显示的内容。</span><span class="sxs-lookup"><span data-stu-id="468c0-103">This section describes how to add content that is displayed in the DESCRIPTION section of the cmdlet Help.</span></span> <span data-ttu-id="468c0-104">在帮助文件中，此内容添加到每个 cmdlet 的命令节点。</span><span class="sxs-lookup"><span data-stu-id="468c0-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="468c0-105">查看完整的帮助文件，打开一个 dll Help.xml 文件位于 Windows PowerShell 安装目录。</span><span class="sxs-lookup"><span data-stu-id="468c0-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="468c0-106">例如，Microsoft.PowerShell.Commands.Management.dll Help.xml 文件包含内容的多个 Windows PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="468c0-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-a-description"></a><span data-ttu-id="468c0-107">若要添加说明</span><span class="sxs-lookup"><span data-stu-id="468c0-107">To Add a Description</span></span>

- <span data-ttu-id="468c0-108">首先介绍更多详细信息中的 cmdlet 的基本功能。</span><span class="sxs-lookup"><span data-stu-id="468c0-108">Begin by explaining the basic features of the cmdlet in more detail.</span></span> <span data-ttu-id="468c0-109">在许多情况下，可以解释的 cmdlet 名称中使用的条款和说明的示例不熟悉的概念。</span><span class="sxs-lookup"><span data-stu-id="468c0-109">In many cases, you can explain the terms used in the cmdlet name and illustrate unfamiliar concepts with an example.</span></span> <span data-ttu-id="468c0-110">例如，如果该 cmdlet 将数据追加到文件，说明它将数据添加到现有文件的末尾。</span><span class="sxs-lookup"><span data-stu-id="468c0-110">For example, if the cmdlet appends data to a file, explain that it adds data to the end of an existing file.</span></span>

- <span data-ttu-id="468c0-111">若要查找所有 cmdlet 的功能，请查看参数列表。</span><span class="sxs-lookup"><span data-stu-id="468c0-111">To find all of the features of the cmdlet, review the parameter list.</span></span> <span data-ttu-id="468c0-112">描述主要功能的 cmdlet，并随后包括其他功能和特性。</span><span class="sxs-lookup"><span data-stu-id="468c0-112">Describe the primary function of the cmdlet, and then include other functions and features.</span></span> <span data-ttu-id="468c0-113">例如，如果该 cmdlet 的主要功能是若要更改一个属性，但该 cmdlet 可以更改的所有属性，这样说中详细说明。</span><span class="sxs-lookup"><span data-stu-id="468c0-113">For example, if the main function of the cmdlet is to change one property, but the cmdlet can change all of the properties, say so in the detailed description.</span></span> <span data-ttu-id="468c0-114">如果 cmdlet 参数让不同的方式收集信息的用户，则说明它。</span><span class="sxs-lookup"><span data-stu-id="468c0-114">If the cmdlet parameters let the users solicit information in different ways, explain it.</span></span>

- <span data-ttu-id="468c0-115">包括的用户可以使用 cmdlet，除了明显的使用方式的信息。</span><span class="sxs-lookup"><span data-stu-id="468c0-115">Include information on ways that users can use the cmdlet, in addition to the obvious uses.</span></span> <span data-ttu-id="468c0-116">例如，可以使用该对象的`Get-Host`cmdlet 检索要更改 Windows PowerShell 命令窗口中的文本颜色。</span><span class="sxs-lookup"><span data-stu-id="468c0-116">For example, you can use the object that the `Get-Host` cmdlet retrieves to change the color of text in the Windows PowerShell command window.</span></span>

  <span data-ttu-id="468c0-117">例如：" `Get-Acl` Cmdlet 获取表示文件或资源的安全描述符的对象。</span><span class="sxs-lookup"><span data-stu-id="468c0-117">Example:  "The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="468c0-118">安全描述符包含资源的访问控制列表 (ACL)。</span><span class="sxs-lookup"><span data-stu-id="468c0-118">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="468c0-119">ACL 可指定用户和用户组具有访问该资源的权限。"</span><span class="sxs-lookup"><span data-stu-id="468c0-119">The ACL specifies the permissions that users and user groups have to access the resource."</span></span>

- <span data-ttu-id="468c0-120">详细的说明应描述 cmdlet，但它应描述此 cmdlet 将使用的概念。</span><span class="sxs-lookup"><span data-stu-id="468c0-120">The detailed description should describe the cmdlet, but it should not describe concepts that the cmdlet uses.</span></span> <span data-ttu-id="468c0-121">将概念定义放置在其他说明。</span><span class="sxs-lookup"><span data-stu-id="468c0-121">Place concept definitions in Additional Notes.</span></span>

## <a name="see-also"></a><span data-ttu-id="468c0-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="468c0-122">See Also</span></span>

[<span data-ttu-id="468c0-123">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="468c0-123">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
