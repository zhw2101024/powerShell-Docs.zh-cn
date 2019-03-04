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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860053"
---
# <a name="writing-a-windows-powershell-provider"></a><span data-ttu-id="04bb2-102">编写 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="04bb2-102">Writing a Windows PowerShell Provider</span></span>

<span data-ttu-id="04bb2-103">"编写 Windows PowerShell 提供程序"是用于设计 Windows PowerShell 提供程序的程序经理和开发人员实现提供程序代码。</span><span class="sxs-lookup"><span data-stu-id="04bb2-103">"Writing a Windows PowerShell Provider" is for program managers who are designing Windows PowerShell providers and for developers who are implementing provider code.</span></span> <span data-ttu-id="04bb2-104">它将帮助你了解 Windows PowerShell 提供程序的工作，并且它提供了可用于启动设计或编写自己的提供程序的示例代码。</span><span class="sxs-lookup"><span data-stu-id="04bb2-104">It will help you understand how Windows PowerShell providers work, and it provides sample code that you can use to start designing or writing your own providers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="04bb2-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="04bb2-105">In This Section</span></span>

<span data-ttu-id="04bb2-106">[Windows PowerShell 提供程序快速入门](./windows-powershell-provider-quickstart.md)的代码示例和演练的非常基本的提供程序。</span><span class="sxs-lookup"><span data-stu-id="04bb2-106">[Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md) Example code and walkthrough of a very basic provider.</span></span>

<span data-ttu-id="04bb2-107">[Windows PowerShell 提供程序概述](./windows-powershell-provider-overview.md)本部分包含介绍什么是 Windows PowerShell 提供程序以及它们如何工作的主题。</span><span class="sxs-lookup"><span data-stu-id="04bb2-107">[Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md) This section contains topics that describe what Windows PowerShell providers are and how they work.</span></span>

<span data-ttu-id="04bb2-108">[编写项提供程序](./writing-an-item-provider.md)示例代码和支持获取和设置项的方法的演练。</span><span class="sxs-lookup"><span data-stu-id="04bb2-108">[Writing an item provider](./writing-an-item-provider.md) Example code and walkthrough of methods that support getting and setting items.</span></span>

<span data-ttu-id="04bb2-109">[编写容器提供程序](./writing-a-container-provider.md)的代码示例和演练支持容器 （具有作为子级的其他项的项） 的方法。</span><span class="sxs-lookup"><span data-stu-id="04bb2-109">[Writing a container provider](./writing-a-container-provider.md) Example code and walkthrough of methods that support containers (items that have other items as children).</span></span>

<span data-ttu-id="04bb2-110">[编写导航提供程序](./writing-a-navigation-provider.md)的代码示例和演练支持嵌套的容器、 相对路径，并将项目移到另一个路径中的方法。</span><span class="sxs-lookup"><span data-stu-id="04bb2-110">[Writing a navigation provider](./writing-a-navigation-provider.md) Example code and walkthrough of methods that support nested containers, relative paths, and moving items from one path to another.</span></span>

<span data-ttu-id="04bb2-111">[提供程序示例](./provider-samples.md)本部分提供了提供程序的示例。</span><span class="sxs-lookup"><span data-stu-id="04bb2-111">[Provider Samples](./provider-samples.md) This section provides samples of providers.</span></span>

## <a name="see-also"></a><span data-ttu-id="04bb2-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="04bb2-112">See Also</span></span>

[<span data-ttu-id="04bb2-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="04bb2-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)