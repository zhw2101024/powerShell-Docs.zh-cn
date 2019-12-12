---
title: 如何添加 Cmdlet 说明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361276"
---
# <a name="how-to-add-a-cmdlet-description"></a><span data-ttu-id="7438c-102">如何添加 Cmdlet 说明</span><span class="sxs-lookup"><span data-stu-id="7438c-102">How to Add a Cmdlet Description</span></span>

<span data-ttu-id="7438c-103">本部分介绍如何添加在 cmdlet 帮助的 "描述" 部分中显示的内容。</span><span class="sxs-lookup"><span data-stu-id="7438c-103">This section describes how to add content that is displayed in the DESCRIPTION section of the cmdlet Help.</span></span> <span data-ttu-id="7438c-104">在帮助文件中，此内容将添加到每个 cmdlet 的命令节点。</span><span class="sxs-lookup"><span data-stu-id="7438c-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="7438c-105">若要获取帮助文件的完整视图，请打开位于 Windows PowerShell 安装目录中的 dll-Help 文件之一。</span><span class="sxs-lookup"><span data-stu-id="7438c-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="7438c-106">例如，dll-Help 文件包含多个 Windows PowerShell cmdlet 的内容，则不会。</span><span class="sxs-lookup"><span data-stu-id="7438c-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-a-description"></a><span data-ttu-id="7438c-107">添加说明</span><span class="sxs-lookup"><span data-stu-id="7438c-107">To Add a Description</span></span>

- <span data-ttu-id="7438c-108">首先，更详细地介绍 cmdlet 的基本功能。</span><span class="sxs-lookup"><span data-stu-id="7438c-108">Begin by explaining the basic features of the cmdlet in more detail.</span></span> <span data-ttu-id="7438c-109">在许多情况下，你可以解释 cmdlet 名称中使用的术语，并举例说明不熟悉的概念。</span><span class="sxs-lookup"><span data-stu-id="7438c-109">In many cases, you can explain the terms used in the cmdlet name and illustrate unfamiliar concepts with an example.</span></span> <span data-ttu-id="7438c-110">例如，如果 cmdlet 将数据追加到文件，则说明它会将数据添加到现有文件的末尾。</span><span class="sxs-lookup"><span data-stu-id="7438c-110">For example, if the cmdlet appends data to a file, explain that it adds data to the end of an existing file.</span></span>

- <span data-ttu-id="7438c-111">若要查找 cmdlet 的所有功能，请查看参数列表。</span><span class="sxs-lookup"><span data-stu-id="7438c-111">To find all of the features of the cmdlet, review the parameter list.</span></span> <span data-ttu-id="7438c-112">描述 cmdlet 的主要功能，然后包含其他函数和功能。</span><span class="sxs-lookup"><span data-stu-id="7438c-112">Describe the primary function of the cmdlet, and then include other functions and features.</span></span> <span data-ttu-id="7438c-113">例如，如果该 cmdlet 的主要功能是更改一个属性，但该 cmdlet 可以更改所有属性，例如，在详细说明中。</span><span class="sxs-lookup"><span data-stu-id="7438c-113">For example, if the main function of the cmdlet is to change one property, but the cmdlet can change all of the properties, say so in the detailed description.</span></span> <span data-ttu-id="7438c-114">如果 cmdlet 参数允许用户以不同的方式请求信息，请对其进行说明。</span><span class="sxs-lookup"><span data-stu-id="7438c-114">If the cmdlet parameters let the users solicit information in different ways, explain it.</span></span>

- <span data-ttu-id="7438c-115">除了明显的使用之外，还包括有关用户可以使用 cmdlet 的方式的信息。</span><span class="sxs-lookup"><span data-stu-id="7438c-115">Include information on ways that users can use the cmdlet, in addition to the obvious uses.</span></span> <span data-ttu-id="7438c-116">例如，可以使用 `Get-Host` cmdlet 检索的对象来更改 Windows PowerShell 命令窗口中的文本颜色。</span><span class="sxs-lookup"><span data-stu-id="7438c-116">For example, you can use the object that the `Get-Host` cmdlet retrieves to change the color of text in the Windows PowerShell command window.</span></span>

  <span data-ttu-id="7438c-117">示例： "`Get-Acl` cmdlet 可获取表示文件或资源的安全描述符的对象。</span><span class="sxs-lookup"><span data-stu-id="7438c-117">Example:  "The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="7438c-118">安全描述符包含资源的访问控制列表 (ACL)。</span><span class="sxs-lookup"><span data-stu-id="7438c-118">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="7438c-119">ACL 指定用户和用户组访问资源所需的权限。</span><span class="sxs-lookup"><span data-stu-id="7438c-119">The ACL specifies the permissions that users and user groups have to access the resource."</span></span>

- <span data-ttu-id="7438c-120">详细描述应描述 cmdlet，但它不应描述 cmdlet 使用的概念。</span><span class="sxs-lookup"><span data-stu-id="7438c-120">The detailed description should describe the cmdlet, but it should not describe concepts that the cmdlet uses.</span></span> <span data-ttu-id="7438c-121">在其他说明中放置概念定义。</span><span class="sxs-lookup"><span data-stu-id="7438c-121">Place concept definitions in Additional Notes.</span></span>

## <a name="see-also"></a><span data-ttu-id="7438c-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7438c-122">See Also</span></span>

[<span data-ttu-id="7438c-123">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7438c-123">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
