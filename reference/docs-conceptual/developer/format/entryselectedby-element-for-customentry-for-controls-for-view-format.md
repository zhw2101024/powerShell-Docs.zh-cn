---
title: 用于视图（格式）的 CustomEntry 的 EntrySelectedBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363886"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="6ceda-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="6ceda-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="6ceda-103">定义使用此控件定义的 .NET 类型或要使用此定义时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="6ceda-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="6ceda-104">定义可由视图使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="6ceda-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="6ceda-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 元素（format） Control 元素 for View （format） CustomControl 元素的控件元素，用于控件的 View （format） CustomEntries 元素CustomControl for view （format） CustomEntry 元素 for CustomEntries for view （format） EntrySelectedBy 元素 for view （format）的控件</span><span class="sxs-lookup"><span data-stu-id="6ceda-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6ceda-106">语法</span><span class="sxs-lookup"><span data-stu-id="6ceda-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6ceda-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="6ceda-107">Attributes and Elements</span></span>

<span data-ttu-id="6ceda-108">以下各节介绍 `EntrySelectedBy` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6ceda-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="6ceda-109">必须为定义至少指定一个类型、选择集或选择条件。</span><span class="sxs-lookup"><span data-stu-id="6ceda-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="6ceda-110">您可以使用的子元素数没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="6ceda-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="6ceda-111">属性</span><span class="sxs-lookup"><span data-stu-id="6ceda-111">Attributes</span></span>

<span data-ttu-id="6ceda-112">无。</span><span class="sxs-lookup"><span data-stu-id="6ceda-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6ceda-113">子元素</span><span class="sxs-lookup"><span data-stu-id="6ceda-113">Child Elements</span></span>

|<span data-ttu-id="6ceda-114">元素</span><span class="sxs-lookup"><span data-stu-id="6ceda-114">Element</span></span>|<span data-ttu-id="6ceda-115">描述</span><span class="sxs-lookup"><span data-stu-id="6ceda-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6ceda-116">用于视图的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6ceda-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="6ceda-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="6ceda-117">Optional element.</span></span><br /><br /> <span data-ttu-id="6ceda-118">定义要使用此定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="6ceda-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="6ceda-119">用于视图的控件的 EntrySelectedBy 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6ceda-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="6ceda-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="6ceda-120">Optional element.</span></span><br /><br /> <span data-ttu-id="6ceda-121">指定一组使用此控件定义的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="6ceda-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="6ceda-122">用于视图的控件的 EntrySelectedBy 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="6ceda-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="6ceda-123">可选元素。</span><span class="sxs-lookup"><span data-stu-id="6ceda-123">Optional element.</span></span><br /><br /> <span data-ttu-id="6ceda-124">指定使用控件的此定义的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="6ceda-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6ceda-125">父元素</span><span class="sxs-lookup"><span data-stu-id="6ceda-125">Parent Elements</span></span>

|<span data-ttu-id="6ceda-126">元素</span><span class="sxs-lookup"><span data-stu-id="6ceda-126">Element</span></span>|<span data-ttu-id="6ceda-127">描述</span><span class="sxs-lookup"><span data-stu-id="6ceda-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6ceda-128">用于视图的控件的 CustomEntries 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6ceda-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="6ceda-129">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="6ceda-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6ceda-130">备注</span><span class="sxs-lookup"><span data-stu-id="6ceda-130">Remarks</span></span>

<span data-ttu-id="6ceda-131">选择条件用于定义要使用的定义必须存在的条件，例如当对象具有特定属性或特定属性值或脚本计算结果为 `true`时。</span><span class="sxs-lookup"><span data-stu-id="6ceda-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="6ceda-132">有关选择条件的详细信息，请参阅[定义使用视图条目或项的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="6ceda-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6ceda-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6ceda-133">See Also</span></span>

[<span data-ttu-id="6ceda-134">用于视图的控件的 CustomEntries 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6ceda-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="6ceda-135">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="6ceda-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
