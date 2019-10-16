---
title: 数量参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c0bd8a9-1749-4885-ab24-38c0a4d9f2cb
caps.latest.revision: 6
ms.openlocfilehash: 7a3efc60fcc8729d833f6de070016cfd08cc9b88
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369556"
---
# <a name="quantity-parameters"></a><span data-ttu-id="39b0f-102">数量参数</span><span class="sxs-lookup"><span data-stu-id="39b0f-102">Quantity Parameters</span></span>

<span data-ttu-id="39b0f-103">下表列出了用于数量参数的建议名称和功能。</span><span class="sxs-lookup"><span data-stu-id="39b0f-103">The following table lists the recommended names and functionality for quantity parameters.</span></span>

|<span data-ttu-id="39b0f-104">参数</span><span class="sxs-lookup"><span data-stu-id="39b0f-104">Parameter</span></span>|<span data-ttu-id="39b0f-105">功能</span><span class="sxs-lookup"><span data-stu-id="39b0f-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="39b0f-106">**一切**</span><span class="sxs-lookup"><span data-stu-id="39b0f-106">**All**</span></span><br><span data-ttu-id="39b0f-107">数据类型：布尔值</span><span class="sxs-lookup"><span data-stu-id="39b0f-107">Data type: Boolean</span></span>|<span data-ttu-id="39b0f-108">实现此参数以便 `true` 指示应对所有资源，而不是默认的资源子集。</span><span class="sxs-lookup"><span data-stu-id="39b0f-108">Implement this parameter so that `true` indicates that all resources should be acted upon instead of a default subset of resources.</span></span> <span data-ttu-id="39b0f-109">实现此参数以便 `false` 表示资源的子集。</span><span class="sxs-lookup"><span data-stu-id="39b0f-109">Implement this parameter so that `false` indicates a subset of the resources.</span></span>|
|<span data-ttu-id="39b0f-110">**分区**</span><span class="sxs-lookup"><span data-stu-id="39b0f-110">**Allocation**</span></span><br><span data-ttu-id="39b0f-111">数据类型： Int32</span><span class="sxs-lookup"><span data-stu-id="39b0f-111">Data type: Int32</span></span>|<span data-ttu-id="39b0f-112">实现此参数，以便用户可以指定要分配的项数。</span><span class="sxs-lookup"><span data-stu-id="39b0f-112">Implement this parameter so that the user can specify the number of items to allocate.</span></span>|
|<span data-ttu-id="39b0f-113">**BlockCount**</span><span class="sxs-lookup"><span data-stu-id="39b0f-113">**BlockCount**</span></span><br><span data-ttu-id="39b0f-114">数据类型： Int64</span><span class="sxs-lookup"><span data-stu-id="39b0f-114">Data type: Int64</span></span>|<span data-ttu-id="39b0f-115">实现此参数，以便用户可以指定块计数。</span><span class="sxs-lookup"><span data-stu-id="39b0f-115">Implement this parameter so that the user can specify the block count.</span></span>|
|<span data-ttu-id="39b0f-116">**计**</span><span class="sxs-lookup"><span data-stu-id="39b0f-116">**Count**</span></span><br><span data-ttu-id="39b0f-117">数据类型： Int64</span><span class="sxs-lookup"><span data-stu-id="39b0f-117">Data type: Int64</span></span>|<span data-ttu-id="39b0f-118">实现此参数，以便用户可以指定计数。</span><span class="sxs-lookup"><span data-stu-id="39b0f-118">Implement this parameter so that the user can specify the count.</span></span>|
|<span data-ttu-id="39b0f-119">**内**</span><span class="sxs-lookup"><span data-stu-id="39b0f-119">**Scope**</span></span><br><span data-ttu-id="39b0f-120">数据类型：关键字</span><span class="sxs-lookup"><span data-stu-id="39b0f-120">Data type: Keyword</span></span>|<span data-ttu-id="39b0f-121">实现此参数，以便用户可以指定要操作的范围。</span><span class="sxs-lookup"><span data-stu-id="39b0f-121">Implement this parameter so that the user can specify the scope to operate on.</span></span>|

## <a name="see-also"></a><span data-ttu-id="39b0f-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="39b0f-122">See Also</span></span>

[<span data-ttu-id="39b0f-123">Cmdlet 参数</span><span class="sxs-lookup"><span data-stu-id="39b0f-123">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="39b0f-124">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="39b0f-124">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="39b0f-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="39b0f-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
