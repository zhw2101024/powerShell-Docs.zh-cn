---
title: WideControl 的 WideEntries 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361426"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="7d5ac-102">WideEntries Element for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7d5ac-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="7d5ac-103">提供宽视图的定义。</span><span class="sxs-lookup"><span data-stu-id="7d5ac-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="7d5ac-104">宽视图必须指定一个或多个定义。</span><span class="sxs-lookup"><span data-stu-id="7d5ac-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="7d5ac-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） WideControl 元素（format） WideEntries 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="7d5ac-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7d5ac-106">语法</span><span class="sxs-lookup"><span data-stu-id="7d5ac-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="7d5ac-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="7d5ac-107">Attributes and Elements</span></span>

<span data-ttu-id="7d5ac-108">以下各节介绍 `WideEntries` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7d5ac-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="7d5ac-109">必须至少指定一个子元素。</span><span class="sxs-lookup"><span data-stu-id="7d5ac-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="7d5ac-110">属性</span><span class="sxs-lookup"><span data-stu-id="7d5ac-110">Attributes</span></span>

<span data-ttu-id="7d5ac-111">无。</span><span class="sxs-lookup"><span data-stu-id="7d5ac-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7d5ac-112">子元素</span><span class="sxs-lookup"><span data-stu-id="7d5ac-112">Child Elements</span></span>

|<span data-ttu-id="7d5ac-113">元素</span><span class="sxs-lookup"><span data-stu-id="7d5ac-113">Element</span></span>|<span data-ttu-id="7d5ac-114">描述</span><span class="sxs-lookup"><span data-stu-id="7d5ac-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7d5ac-115">WideEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7d5ac-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="7d5ac-116">提供宽视图的定义。</span><span class="sxs-lookup"><span data-stu-id="7d5ac-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7d5ac-117">父元素</span><span class="sxs-lookup"><span data-stu-id="7d5ac-117">Parent Elements</span></span>

|<span data-ttu-id="7d5ac-118">元素</span><span class="sxs-lookup"><span data-stu-id="7d5ac-118">Element</span></span>|<span data-ttu-id="7d5ac-119">描述</span><span class="sxs-lookup"><span data-stu-id="7d5ac-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7d5ac-120">WideControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7d5ac-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="7d5ac-121">定义视图的宽（单值）列表格式。</span><span class="sxs-lookup"><span data-stu-id="7d5ac-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7d5ac-122">备注</span><span class="sxs-lookup"><span data-stu-id="7d5ac-122">Remarks</span></span>

<span data-ttu-id="7d5ac-123">宽视图是显示每个对象的单个属性值或脚本值的列表格式。</span><span class="sxs-lookup"><span data-stu-id="7d5ac-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="7d5ac-124">有关宽视图组件的详细信息，请参阅[宽视图组件](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="7d5ac-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7d5ac-125">示例</span><span class="sxs-lookup"><span data-stu-id="7d5ac-125">Example</span></span>

<span data-ttu-id="7d5ac-126">下面的示例演示了一个 `WideEntries` 元素，该元素定义单个 @no__t 1 元素。</span><span class="sxs-lookup"><span data-stu-id="7d5ac-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="7d5ac-127">@No__t-0 元素包含一个 @no__t 元素，该元素定义在视图中显示的属性或脚本值。</span><span class="sxs-lookup"><span data-stu-id="7d5ac-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="7d5ac-128">有关宽视图的完整示例，请参阅[宽视图（基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="7d5ac-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7d5ac-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7d5ac-129">See Also</span></span>

[<span data-ttu-id="7d5ac-130">创建宽视图</span><span class="sxs-lookup"><span data-stu-id="7d5ac-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="7d5ac-131">WideControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7d5ac-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="7d5ac-132">WideEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7d5ac-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="7d5ac-133">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="7d5ac-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
