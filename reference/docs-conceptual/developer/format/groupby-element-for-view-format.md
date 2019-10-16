---
title: View 的 GroupBy 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363626"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="2f65b-102">GroupBy Element for View (Format)</span><span class="sxs-lookup"><span data-stu-id="2f65b-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="2f65b-103">定义如何显示新的对象组。</span><span class="sxs-lookup"><span data-stu-id="2f65b-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="2f65b-104">定义表、列表、宽或自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="2f65b-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="2f65b-105">View 元素（format） ViewDefinitions 元素（format） View 元素（format） GroupBy 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="2f65b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2f65b-106">语法</span><span class="sxs-lookup"><span data-stu-id="2f65b-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2f65b-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="2f65b-107">Attributes and Elements</span></span>

<span data-ttu-id="2f65b-108">以下各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2f65b-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2f65b-109">属性</span><span class="sxs-lookup"><span data-stu-id="2f65b-109">Attributes</span></span>

<span data-ttu-id="2f65b-110">无。</span><span class="sxs-lookup"><span data-stu-id="2f65b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2f65b-111">子元素</span><span class="sxs-lookup"><span data-stu-id="2f65b-111">Child Elements</span></span>

|<span data-ttu-id="2f65b-112">元素</span><span class="sxs-lookup"><span data-stu-id="2f65b-112">Element</span></span>|<span data-ttu-id="2f65b-113">描述</span><span class="sxs-lookup"><span data-stu-id="2f65b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2f65b-114">GroupBy 的 CustomControl 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="2f65b-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="2f65b-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2f65b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="2f65b-116">定义显示新组的自定义控件。</span><span class="sxs-lookup"><span data-stu-id="2f65b-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="2f65b-117">GroupBy 的 CustomControlName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="2f65b-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="2f65b-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2f65b-118">Optional element.</span></span><br /><br /> <span data-ttu-id="2f65b-119">指定用于显示新组的控件的名称。</span><span class="sxs-lookup"><span data-stu-id="2f65b-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="2f65b-120">GroupBy 的标签元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2f65b-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="2f65b-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2f65b-121">Optional element.</span></span><br /><br /> <span data-ttu-id="2f65b-122">指定在遇到新组时显示的标签。</span><span class="sxs-lookup"><span data-stu-id="2f65b-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="2f65b-123">GroupBy 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="2f65b-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="2f65b-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2f65b-124">Optional element.</span></span><br /><br /> <span data-ttu-id="2f65b-125">指定 .NET 属性，在新组的值发生更改时启动新组。</span><span class="sxs-lookup"><span data-stu-id="2f65b-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="2f65b-126">GroupBy 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2f65b-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="2f65b-127">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2f65b-127">Optional element.</span></span><br /><br /> <span data-ttu-id="2f65b-128">指定在新组的值发生更改时启动新组的脚本。</span><span class="sxs-lookup"><span data-stu-id="2f65b-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2f65b-129">父元素</span><span class="sxs-lookup"><span data-stu-id="2f65b-129">Parent Elements</span></span>

|<span data-ttu-id="2f65b-130">元素</span><span class="sxs-lookup"><span data-stu-id="2f65b-130">Element</span></span>|<span data-ttu-id="2f65b-131">描述</span><span class="sxs-lookup"><span data-stu-id="2f65b-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2f65b-132">View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2f65b-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="2f65b-133">定义一个视图，该视图显示一个或多个 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="2f65b-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2f65b-134">备注</span><span class="sxs-lookup"><span data-stu-id="2f65b-134">Remarks</span></span>

<span data-ttu-id="2f65b-135">定义如何显示新的对象组时，您必须指定将启动新组的属性或脚本。但是，不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="2f65b-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="2f65b-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2f65b-136">See Also</span></span>

[<span data-ttu-id="2f65b-137">GroupBy 的 CustomControlName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="2f65b-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="2f65b-138">GroupBy 的标签元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2f65b-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="2f65b-139">GroupBy 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="2f65b-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="2f65b-140">GroupBy 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2f65b-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="2f65b-141">View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2f65b-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="2f65b-142">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="2f65b-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
