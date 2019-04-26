---
title: 视图 （格式） 的 GroupBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065525"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="91edd-102">GroupBy Element for View (Format)</span><span class="sxs-lookup"><span data-stu-id="91edd-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="91edd-103">定义新的一组对象的显示方式。</span><span class="sxs-lookup"><span data-stu-id="91edd-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="91edd-104">定义表、 列表、 宽，或自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="91edd-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="91edd-105">视图 （格式） 的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="91edd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="91edd-106">语法</span><span class="sxs-lookup"><span data-stu-id="91edd-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="91edd-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="91edd-107">Attributes and Elements</span></span>

<span data-ttu-id="91edd-108">以下各节描述了特性、 子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="91edd-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="91edd-109">属性</span><span class="sxs-lookup"><span data-stu-id="91edd-109">Attributes</span></span>

<span data-ttu-id="91edd-110">无。</span><span class="sxs-lookup"><span data-stu-id="91edd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="91edd-111">子元素</span><span class="sxs-lookup"><span data-stu-id="91edd-111">Child Elements</span></span>

|<span data-ttu-id="91edd-112">元素</span><span class="sxs-lookup"><span data-stu-id="91edd-112">Element</span></span>|<span data-ttu-id="91edd-113">说明</span><span class="sxs-lookup"><span data-stu-id="91edd-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="91edd-114">GroupBy （格式） 的 CustomControl 元素</span><span class="sxs-lookup"><span data-stu-id="91edd-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="91edd-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="91edd-115">Optional element.</span></span><br /><br /> <span data-ttu-id="91edd-116">定义显示新组的自定义控件。</span><span class="sxs-lookup"><span data-stu-id="91edd-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="91edd-117">GroupBy （格式） 的 CustomControlName 元素</span><span class="sxs-lookup"><span data-stu-id="91edd-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="91edd-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="91edd-118">Optional element.</span></span><br /><br /> <span data-ttu-id="91edd-119">指定控件用于显示新组的名称。</span><span class="sxs-lookup"><span data-stu-id="91edd-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="91edd-120">GroupBy （格式） 的标签元素</span><span class="sxs-lookup"><span data-stu-id="91edd-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="91edd-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="91edd-121">Optional element.</span></span><br /><br /> <span data-ttu-id="91edd-122">指定遇到新的组时显示的标签。</span><span class="sxs-lookup"><span data-stu-id="91edd-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="91edd-123">GroupBy （格式） 的属性名称元素</span><span class="sxs-lookup"><span data-stu-id="91edd-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="91edd-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="91edd-124">Optional element.</span></span><br /><br /> <span data-ttu-id="91edd-125">指定在开始的.NET 属性及其值发生更改时的新组。</span><span class="sxs-lookup"><span data-stu-id="91edd-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="91edd-126">GroupBy （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="91edd-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="91edd-127">可选元素。</span><span class="sxs-lookup"><span data-stu-id="91edd-127">Optional element.</span></span><br /><br /> <span data-ttu-id="91edd-128">指定其值发生更改时启动新的组的脚本。</span><span class="sxs-lookup"><span data-stu-id="91edd-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="91edd-129">父元素</span><span class="sxs-lookup"><span data-stu-id="91edd-129">Parent Elements</span></span>

|<span data-ttu-id="91edd-130">元素</span><span class="sxs-lookup"><span data-stu-id="91edd-130">Element</span></span>|<span data-ttu-id="91edd-131">说明</span><span class="sxs-lookup"><span data-stu-id="91edd-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="91edd-132">视图元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="91edd-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="91edd-133">定义一个视图，显示一个或多个.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="91edd-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="91edd-134">备注</span><span class="sxs-lookup"><span data-stu-id="91edd-134">Remarks</span></span>

<span data-ttu-id="91edd-135">在定义新的一组对象的显示方式时，必须指定属性或脚本将启动新的组;但是，您不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="91edd-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="91edd-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="91edd-136">See Also</span></span>

[<span data-ttu-id="91edd-137">GroupBy （格式） 的 CustomControlName 元素</span><span class="sxs-lookup"><span data-stu-id="91edd-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="91edd-138">GroupBy （格式） 的标签元素</span><span class="sxs-lookup"><span data-stu-id="91edd-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="91edd-139">GroupBy （格式） 的属性名称元素</span><span class="sxs-lookup"><span data-stu-id="91edd-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="91edd-140">GroupBy （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="91edd-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="91edd-141">视图元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="91edd-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="91edd-142">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="91edd-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
