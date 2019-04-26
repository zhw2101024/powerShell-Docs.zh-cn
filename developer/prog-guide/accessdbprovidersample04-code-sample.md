---
title: AccessDbProviderSample04 Code Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: 43f01b9cd6af3ab6c26f88ee0c1e9269499b2bc3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081948"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="c57f2-102">AccessDbProviderSample04 代码示例</span><span class="sxs-lookup"><span data-stu-id="c57f2-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="c57f2-103">下面的代码演示中所述的 Windows PowerShell 提供程序实现[创建一个 Windows PowerShell 容器提供程序](./creating-a-windows-powershell-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="c57f2-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span> <span data-ttu-id="c57f2-104">此提供程序适用于多层数据存储。</span><span class="sxs-lookup"><span data-stu-id="c57f2-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="c57f2-105">对于此类型的数据存储区中，存储的最高级别包含根项和每个后续级别被称为子项目的节点。</span><span class="sxs-lookup"><span data-stu-id="c57f2-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="c57f2-106">通过允许用户若要在这些子节点上运行，用户可以通过在数据存储区按层次结构交互。</span><span class="sxs-lookup"><span data-stu-id="c57f2-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c57f2-107">代码示例</span><span class="sxs-lookup"><span data-stu-id="c57f2-107">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="c57f2-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c57f2-108">See Also</span></span>

[<span data-ttu-id="c57f2-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c57f2-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)