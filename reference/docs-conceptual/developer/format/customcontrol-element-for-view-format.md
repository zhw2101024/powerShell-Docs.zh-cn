---
title: View 的 CustomControl 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363356"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="d66c4-102">CustomControl Element for View (Format)</span><span class="sxs-lookup"><span data-stu-id="d66c4-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="d66c4-103">定义视图的自定义控件格式。</span><span class="sxs-lookup"><span data-stu-id="d66c4-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="d66c4-104">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="d66c4-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d66c4-105">语法</span><span class="sxs-lookup"><span data-stu-id="d66c4-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d66c4-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="d66c4-106">Attributes and Elements</span></span>

<span data-ttu-id="d66c4-107">以下各节介绍了 `CustomControl` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d66c4-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="d66c4-108">您必须指定一个子元素。</span><span class="sxs-lookup"><span data-stu-id="d66c4-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d66c4-109">属性</span><span class="sxs-lookup"><span data-stu-id="d66c4-109">Attributes</span></span>

<span data-ttu-id="d66c4-110">无。</span><span class="sxs-lookup"><span data-stu-id="d66c4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d66c4-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d66c4-111">Child Elements</span></span>

|<span data-ttu-id="d66c4-112">元素</span><span class="sxs-lookup"><span data-stu-id="d66c4-112">Element</span></span>|<span data-ttu-id="d66c4-113">描述</span><span class="sxs-lookup"><span data-stu-id="d66c4-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d66c4-114">用于视图的 CustomControl 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d66c4-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="d66c4-115">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="d66c4-115">Required element.</span></span><br /><br /> <span data-ttu-id="d66c4-116">提供自定义控件视图的定义。</span><span class="sxs-lookup"><span data-stu-id="d66c4-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d66c4-117">父元素</span><span class="sxs-lookup"><span data-stu-id="d66c4-117">Parent Elements</span></span>

|<span data-ttu-id="d66c4-118">元素</span><span class="sxs-lookup"><span data-stu-id="d66c4-118">Element</span></span>|<span data-ttu-id="d66c4-119">描述</span><span class="sxs-lookup"><span data-stu-id="d66c4-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d66c4-120">View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d66c4-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="d66c4-121">定义用于显示一个或多个 .NET 对象的视图。</span><span class="sxs-lookup"><span data-stu-id="d66c4-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d66c4-122">备注</span><span class="sxs-lookup"><span data-stu-id="d66c4-122">Remarks</span></span>

<span data-ttu-id="d66c4-123">在大多数情况下，每个控件视图只需要一个定义，但如果您希望使用同一视图显示不同的 .NET 对象，则可以提供多个定义。</span><span class="sxs-lookup"><span data-stu-id="d66c4-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="d66c4-124">在这些情况下，可以为每个对象或一组对象提供单独的定义。</span><span class="sxs-lookup"><span data-stu-id="d66c4-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="d66c4-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d66c4-125">See Also</span></span>

[<span data-ttu-id="d66c4-126">用于视图的 CustomControl 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d66c4-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="d66c4-127">View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d66c4-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="d66c4-128">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="d66c4-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
