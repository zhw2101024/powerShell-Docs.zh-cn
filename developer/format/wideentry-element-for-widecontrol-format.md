---
title: WideControl （格式） 的 WideEntry 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856523"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="266ea-102">WideEntry Element for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="266ea-102">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="266ea-103">提供了宽的视图的定义。</span><span class="sxs-lookup"><span data-stu-id="266ea-103">Provides a definition of the wide view.</span></span>

<span data-ttu-id="266ea-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） WideEntries 元素 （格式） WideEntry 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="266ea-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="266ea-105">语法</span><span class="sxs-lookup"><span data-stu-id="266ea-105">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="266ea-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="266ea-106">Attributes and Elements</span></span>

<span data-ttu-id="266ea-107">以下各节描述了特性、 子元素和父元素的`WideEntry`元素。</span><span class="sxs-lookup"><span data-stu-id="266ea-107">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="266ea-108">必须指定单个`WideItem`子元素。</span><span class="sxs-lookup"><span data-stu-id="266ea-108">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="266ea-109">特性</span><span class="sxs-lookup"><span data-stu-id="266ea-109">Attributes</span></span>

<span data-ttu-id="266ea-110">无。</span><span class="sxs-lookup"><span data-stu-id="266ea-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="266ea-111">子元素</span><span class="sxs-lookup"><span data-stu-id="266ea-111">Child Elements</span></span>

|<span data-ttu-id="266ea-112">元素</span><span class="sxs-lookup"><span data-stu-id="266ea-112">Element</span></span>|<span data-ttu-id="266ea-113">描述</span><span class="sxs-lookup"><span data-stu-id="266ea-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="266ea-114">WideEntry （格式） 的 EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="266ea-114">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="266ea-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="266ea-115">Optional element.</span></span><br /><br /> <span data-ttu-id="266ea-116">定义使用此宽的项定义或要使用此定义中必须存在的条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="266ea-116">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="266ea-117">WideItem 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="266ea-117">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="266ea-118">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="266ea-118">Required element.</span></span><br /><br /> <span data-ttu-id="266ea-119">定义属性或其值显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="266ea-119">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="266ea-120">父元素</span><span class="sxs-lookup"><span data-stu-id="266ea-120">Parent Elements</span></span>

|<span data-ttu-id="266ea-121">元素</span><span class="sxs-lookup"><span data-stu-id="266ea-121">Element</span></span>|<span data-ttu-id="266ea-122">描述</span><span class="sxs-lookup"><span data-stu-id="266ea-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="266ea-123">WideEntries 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="266ea-123">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="266ea-124">提供了宽的视图的定义。</span><span class="sxs-lookup"><span data-stu-id="266ea-124">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="266ea-125">备注</span><span class="sxs-lookup"><span data-stu-id="266ea-125">Remarks</span></span>

<span data-ttu-id="266ea-126">较宽的视图是显示单个属性值或为每个对象的脚本值以列表格式。</span><span class="sxs-lookup"><span data-stu-id="266ea-126">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="266ea-127">与其他类型的视图，您可以指定只有一个项元素的每个视图定义。</span><span class="sxs-lookup"><span data-stu-id="266ea-127">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="266ea-128">有关较宽的视图的其他组件的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="266ea-128">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="266ea-129">示例</span><span class="sxs-lookup"><span data-stu-id="266ea-129">Example</span></span>

<span data-ttu-id="266ea-130">下面的示例演示`WideEntry`元素定义单个`WideItem`元素。</span><span class="sxs-lookup"><span data-stu-id="266ea-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="266ea-131">`WideItem`元素定义其值显示在视图中的属性。</span><span class="sxs-lookup"><span data-stu-id="266ea-131">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="266ea-132">有关较宽的视图的完整示例，请参阅[宽的视图 （基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="266ea-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="266ea-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="266ea-133">See Also</span></span>

[<span data-ttu-id="266ea-134">创建较宽的视图</span><span class="sxs-lookup"><span data-stu-id="266ea-134">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="266ea-135">WideEntry （格式） 的 SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="266ea-135">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="266ea-136">WideEntry （格式） 的 SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="266ea-136">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="266ea-137">WideEntry （格式） 的类型名称元素</span><span class="sxs-lookup"><span data-stu-id="266ea-137">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="266ea-138">WideEntries 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="266ea-138">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="266ea-139">WideItem 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="266ea-139">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="266ea-140">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="266ea-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
