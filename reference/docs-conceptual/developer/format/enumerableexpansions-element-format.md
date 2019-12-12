---
title: EnumerableExpansions 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363296"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="9bfc6-102">EnumerableExpansions Element (Format)</span><span class="sxs-lookup"><span data-stu-id="9bfc6-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="9bfc6-103">定义在视图中显示 .NET 集合对象时如何对其进行扩展。</span><span class="sxs-lookup"><span data-stu-id="9bfc6-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="9bfc6-104">配置元素（格式） DefaultSettings 元素（format） EnumerableExpansions 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9bfc6-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9bfc6-105">语法</span><span class="sxs-lookup"><span data-stu-id="9bfc6-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9bfc6-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="9bfc6-106">Attributes and Elements</span></span>

<span data-ttu-id="9bfc6-107">以下各节介绍了 `EnumerableExpansions` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9bfc6-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="9bfc6-108">您可以使用的子元素数没有限制。</span><span class="sxs-lookup"><span data-stu-id="9bfc6-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="9bfc6-109">属性</span><span class="sxs-lookup"><span data-stu-id="9bfc6-109">Attributes</span></span>

<span data-ttu-id="9bfc6-110">无。</span><span class="sxs-lookup"><span data-stu-id="9bfc6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9bfc6-111">子元素</span><span class="sxs-lookup"><span data-stu-id="9bfc6-111">Child Elements</span></span>

|<span data-ttu-id="9bfc6-112">元素</span><span class="sxs-lookup"><span data-stu-id="9bfc6-112">Element</span></span>|<span data-ttu-id="9bfc6-113">描述</span><span class="sxs-lookup"><span data-stu-id="9bfc6-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9bfc6-114">EnumerableExpansion 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9bfc6-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="9bfc6-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="9bfc6-115">Optional element.</span></span><br /><br /> <span data-ttu-id="9bfc6-116">定义特定 .NET 集合对象，这些对象在视图中显示时展开。</span><span class="sxs-lookup"><span data-stu-id="9bfc6-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9bfc6-117">父元素</span><span class="sxs-lookup"><span data-stu-id="9bfc6-117">Parent Elements</span></span>

|<span data-ttu-id="9bfc6-118">元素</span><span class="sxs-lookup"><span data-stu-id="9bfc6-118">Element</span></span>|<span data-ttu-id="9bfc6-119">描述</span><span class="sxs-lookup"><span data-stu-id="9bfc6-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9bfc6-120">DefaultSettings 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9bfc6-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="9bfc6-121">定义适用于格式设置文件的所有视图的常见设置。</span><span class="sxs-lookup"><span data-stu-id="9bfc6-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9bfc6-122">备注</span><span class="sxs-lookup"><span data-stu-id="9bfc6-122">Remarks</span></span>

<span data-ttu-id="9bfc6-123">此元素用于定义集合对象和集合中的对象的显示方式。</span><span class="sxs-lookup"><span data-stu-id="9bfc6-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="9bfc6-124">在这种情况下，集合对象引用支持**system.object**接口的任何对象。</span><span class="sxs-lookup"><span data-stu-id="9bfc6-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="9bfc6-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9bfc6-125">See Also</span></span>

[<span data-ttu-id="9bfc6-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="9bfc6-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
