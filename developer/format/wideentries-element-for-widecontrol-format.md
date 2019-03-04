---
title: WideControl （格式） 的 WideEntries 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853273"
---
# <a name="wideentries-element-for-widecontrol-format"></a><span data-ttu-id="8c686-102">WideEntries Element for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="8c686-102">WideEntries Element for WideControl (Format)</span></span>

<span data-ttu-id="8c686-103">提供了宽的视图的定义。</span><span class="sxs-lookup"><span data-stu-id="8c686-103">Provides the definitions of the wide view.</span></span> <span data-ttu-id="8c686-104">宽的视图必须指定一个或多个定义。</span><span class="sxs-lookup"><span data-stu-id="8c686-104">The wide view must specify one or more definitions.</span></span>

<span data-ttu-id="8c686-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） WideEntries 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="8c686-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8c686-106">语法</span><span class="sxs-lookup"><span data-stu-id="8c686-106">Syntax</span></span>

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="8c686-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="8c686-107">Attributes and Elements</span></span>

<span data-ttu-id="8c686-108">以下各节描述的特性、 子元素和父元素的`WideEntries`元素。</span><span class="sxs-lookup"><span data-stu-id="8c686-108">The following sections describe the attributes, child elements, and parent element of the `WideEntries` element.</span></span> <span data-ttu-id="8c686-109">必须指定至少一个子元素。</span><span class="sxs-lookup"><span data-stu-id="8c686-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="8c686-110">特性</span><span class="sxs-lookup"><span data-stu-id="8c686-110">Attributes</span></span>

<span data-ttu-id="8c686-111">无。</span><span class="sxs-lookup"><span data-stu-id="8c686-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8c686-112">子元素</span><span class="sxs-lookup"><span data-stu-id="8c686-112">Child Elements</span></span>

|<span data-ttu-id="8c686-113">元素</span><span class="sxs-lookup"><span data-stu-id="8c686-113">Element</span></span>|<span data-ttu-id="8c686-114">描述</span><span class="sxs-lookup"><span data-stu-id="8c686-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8c686-115">WideEntry 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="8c686-115">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="8c686-116">提供了宽的视图的定义。</span><span class="sxs-lookup"><span data-stu-id="8c686-116">Provides a definition of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8c686-117">父元素</span><span class="sxs-lookup"><span data-stu-id="8c686-117">Parent Elements</span></span>

|<span data-ttu-id="8c686-118">元素</span><span class="sxs-lookup"><span data-stu-id="8c686-118">Element</span></span>|<span data-ttu-id="8c686-119">描述</span><span class="sxs-lookup"><span data-stu-id="8c686-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8c686-120">WideControl 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="8c686-120">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="8c686-121">定义范围内 （单个值） 的视图的列表格式。</span><span class="sxs-lookup"><span data-stu-id="8c686-121">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8c686-122">备注</span><span class="sxs-lookup"><span data-stu-id="8c686-122">Remarks</span></span>

<span data-ttu-id="8c686-123">较宽的视图是显示单个属性值或为每个对象的脚本值以列表格式。</span><span class="sxs-lookup"><span data-stu-id="8c686-123">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="8c686-124">有关较宽的视图的组件的详细信息，请参阅[宽视图组件](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="8c686-124">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8c686-125">示例</span><span class="sxs-lookup"><span data-stu-id="8c686-125">Example</span></span>

<span data-ttu-id="8c686-126">下面的示例演示`WideEntries`元素定义单个`WideEntry`元素。</span><span class="sxs-lookup"><span data-stu-id="8c686-126">The following example shows a `WideEntries` element that defines a single `WideEntry` element.</span></span> <span data-ttu-id="8c686-127">`WideEntry`元素包含一个`WideItem`定义哪些属性或脚本的值显示在视图中的元素。</span><span class="sxs-lookup"><span data-stu-id="8c686-127">The `WideEntry` element contains a single `WideItem` element that defines what property or script value is displayed in the view.</span></span>

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

<span data-ttu-id="8c686-128">有关较宽的视图的完整示例，请参阅[宽的视图 （基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="8c686-128">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8c686-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8c686-129">See Also</span></span>

[<span data-ttu-id="8c686-130">创建较宽的视图</span><span class="sxs-lookup"><span data-stu-id="8c686-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="8c686-131">WideControl 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="8c686-131">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="8c686-132">WideEntry 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="8c686-132">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="8c686-133">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="8c686-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
