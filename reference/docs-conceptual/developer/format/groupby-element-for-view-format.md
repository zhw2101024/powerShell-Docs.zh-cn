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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363626"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="23970-102">GroupBy Element for View (Format)</span><span class="sxs-lookup"><span data-stu-id="23970-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="23970-103">定义如何显示新的对象组。</span><span class="sxs-lookup"><span data-stu-id="23970-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="23970-104">定义表、列表、宽或自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="23970-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="23970-105">View 元素（format） ViewDefinitions 元素（format） View 元素（format） GroupBy 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="23970-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="23970-106">语法</span><span class="sxs-lookup"><span data-stu-id="23970-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="23970-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="23970-107">Attributes and Elements</span></span>

<span data-ttu-id="23970-108">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="23970-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="23970-109">属性</span><span class="sxs-lookup"><span data-stu-id="23970-109">Attributes</span></span>

<span data-ttu-id="23970-110">无。</span><span class="sxs-lookup"><span data-stu-id="23970-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="23970-111">子元素</span><span class="sxs-lookup"><span data-stu-id="23970-111">Child Elements</span></span>

|<span data-ttu-id="23970-112">元素</span><span class="sxs-lookup"><span data-stu-id="23970-112">Element</span></span>|<span data-ttu-id="23970-113">描述</span><span class="sxs-lookup"><span data-stu-id="23970-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="23970-114">GroupBy 的 CustomControl 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="23970-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="23970-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="23970-115">Optional element.</span></span><br /><br /> <span data-ttu-id="23970-116">定义显示新组的自定义控件。</span><span class="sxs-lookup"><span data-stu-id="23970-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="23970-117">GroupBy 的 CustomControlName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="23970-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="23970-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="23970-118">Optional element.</span></span><br /><br /> <span data-ttu-id="23970-119">指定用于显示新组的控件的名称。</span><span class="sxs-lookup"><span data-stu-id="23970-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="23970-120">GroupBy 的标签元素（格式）</span><span class="sxs-lookup"><span data-stu-id="23970-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="23970-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="23970-121">Optional element.</span></span><br /><br /> <span data-ttu-id="23970-122">指定在遇到新组时显示的标签。</span><span class="sxs-lookup"><span data-stu-id="23970-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="23970-123">GroupBy 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="23970-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="23970-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="23970-124">Optional element.</span></span><br /><br /> <span data-ttu-id="23970-125">指定 .NET 属性，在新组的值发生更改时启动新组。</span><span class="sxs-lookup"><span data-stu-id="23970-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="23970-126">GroupBy 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="23970-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="23970-127">可选元素。</span><span class="sxs-lookup"><span data-stu-id="23970-127">Optional element.</span></span><br /><br /> <span data-ttu-id="23970-128">指定在新组的值发生更改时启动新组的脚本。</span><span class="sxs-lookup"><span data-stu-id="23970-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="23970-129">父元素</span><span class="sxs-lookup"><span data-stu-id="23970-129">Parent Elements</span></span>

|<span data-ttu-id="23970-130">元素</span><span class="sxs-lookup"><span data-stu-id="23970-130">Element</span></span>|<span data-ttu-id="23970-131">描述</span><span class="sxs-lookup"><span data-stu-id="23970-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="23970-132">View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="23970-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="23970-133">定义一个视图，该视图显示一个或多个 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="23970-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="23970-134">备注</span><span class="sxs-lookup"><span data-stu-id="23970-134">Remarks</span></span>

<span data-ttu-id="23970-135">定义如何显示新的对象组时，您必须指定将启动新组的属性或脚本。但是，不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="23970-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="23970-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="23970-136">See Also</span></span>

[<span data-ttu-id="23970-137">GroupBy 的 CustomControlName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="23970-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="23970-138">GroupBy 的标签元素（格式）</span><span class="sxs-lookup"><span data-stu-id="23970-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="23970-139">GroupBy 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="23970-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="23970-140">GroupBy 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="23970-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="23970-141">View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="23970-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="23970-142">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="23970-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
