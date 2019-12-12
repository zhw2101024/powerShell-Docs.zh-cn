---
title: 编写 Windows PowerShell 提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a54ce657-e0e0-4b3e-b9dc-aed39876f933
caps.latest.revision: 11
ms.openlocfilehash: 58252956184703fdcdb3aa9b1db617c6e91294c1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366186"
---
# <a name="writing-a-windows-powershell-provider"></a><span data-ttu-id="1df6f-102">编写 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="1df6f-102">Writing a Windows PowerShell Provider</span></span>

<span data-ttu-id="1df6f-103">"编写 Windows PowerShell 提供程序" 适用于正在设计 Windows PowerShell 提供程序的程序管理器和实现提供程序代码的开发人员。</span><span class="sxs-lookup"><span data-stu-id="1df6f-103">"Writing a Windows PowerShell Provider" is for program managers who are designing Windows PowerShell providers and for developers who are implementing provider code.</span></span> <span data-ttu-id="1df6f-104">它将帮助你了解 Windows PowerShell 提供程序的工作原理，并提供可用于开始设计或编写你自己的提供程序的示例代码。</span><span class="sxs-lookup"><span data-stu-id="1df6f-104">It will help you understand how Windows PowerShell providers work, and it provides sample code that you can use to start designing or writing your own providers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="1df6f-105">本部分内容</span><span class="sxs-lookup"><span data-stu-id="1df6f-105">In This Section</span></span>

<span data-ttu-id="1df6f-106">[Windows PowerShell 提供程序快速入门](./windows-powershell-provider-quickstart.md)基本提供程序的示例代码和演练。</span><span class="sxs-lookup"><span data-stu-id="1df6f-106">[Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md) Example code and walkthrough of a very basic provider.</span></span>

<span data-ttu-id="1df6f-107">[Windows PowerShell 提供程序概述](./windows-powershell-provider-overview.md)本部分包含的主题介绍了 Windows PowerShell 提供程序的定义及其工作原理。</span><span class="sxs-lookup"><span data-stu-id="1df6f-107">[Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md) This section contains topics that describe what Windows PowerShell providers are and how they work.</span></span>

<span data-ttu-id="1df6f-108">[编写项提供程序](./writing-an-item-provider.md)支持获取和设置项的方法的示例代码和演练。</span><span class="sxs-lookup"><span data-stu-id="1df6f-108">[Writing an item provider](./writing-an-item-provider.md) Example code and walkthrough of methods that support getting and setting items.</span></span>

<span data-ttu-id="1df6f-109">[编写容器提供程序](./writing-a-container-provider.md)支持容器的方法（将其他项作为子级的项）的示例代码和演练。</span><span class="sxs-lookup"><span data-stu-id="1df6f-109">[Writing a container provider](./writing-a-container-provider.md) Example code and walkthrough of methods that support containers (items that have other items as children).</span></span>

<span data-ttu-id="1df6f-110">[编写导航提供程序](./writing-a-navigation-provider.md)支持嵌套容器、相对路径和将项从一个路径移到另一个路径的方法的示例代码和演练。</span><span class="sxs-lookup"><span data-stu-id="1df6f-110">[Writing a navigation provider](./writing-a-navigation-provider.md) Example code and walkthrough of methods that support nested containers, relative paths, and moving items from one path to another.</span></span>

<span data-ttu-id="1df6f-111">[提供程序示例](./provider-samples.md)本部分提供提供程序的示例。</span><span class="sxs-lookup"><span data-stu-id="1df6f-111">[Provider Samples](./provider-samples.md) This section provides samples of providers.</span></span>

## <a name="see-also"></a><span data-ttu-id="1df6f-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1df6f-112">See Also</span></span>

[<span data-ttu-id="1df6f-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1df6f-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)