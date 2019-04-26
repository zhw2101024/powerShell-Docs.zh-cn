---
title: 视图 （格式） 的控件的 CustomEntry EntrySelectedBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d80a7d-3797-4c46-ae74-ae5cda79b24f
caps.latest.revision: 8
ms.openlocfilehash: efb20c3f2077547e6eb3cb28240512b444f9c481
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066237"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="06019-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="06019-102">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="06019-103">定义使用此控件定义或要使用此定义中必须存在的条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="06019-103">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="06019-104">定义一个视图，可以使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="06019-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="06019-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl CustomEntries CustomEntry 视图 （格式） 的控件的视图 （格式） EntrySelectedBy 元素的控件的视图 （格式） CustomEntry 元素的控件</span><span class="sxs-lookup"><span data-stu-id="06019-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="06019-106">语法</span><span class="sxs-lookup"><span data-stu-id="06019-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="06019-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="06019-107">Attributes and Elements</span></span>

<span data-ttu-id="06019-108">以下各节描述了特性、 子元素和父元素的`EntrySelectedBy`元素。</span><span class="sxs-lookup"><span data-stu-id="06019-108">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="06019-109">必须指定至少一个类型、 选择集或选择条件的定义。</span><span class="sxs-lookup"><span data-stu-id="06019-109">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="06019-110">可以使用的子元素的数目没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="06019-110">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="06019-111">属性</span><span class="sxs-lookup"><span data-stu-id="06019-111">Attributes</span></span>

<span data-ttu-id="06019-112">无。</span><span class="sxs-lookup"><span data-stu-id="06019-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="06019-113">子元素</span><span class="sxs-lookup"><span data-stu-id="06019-113">Child Elements</span></span>

|<span data-ttu-id="06019-114">元素</span><span class="sxs-lookup"><span data-stu-id="06019-114">Element</span></span>|<span data-ttu-id="06019-115">说明</span><span class="sxs-lookup"><span data-stu-id="06019-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06019-116">视图 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="06019-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="06019-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="06019-117">Optional element.</span></span><br /><br /> <span data-ttu-id="06019-118">定义必须存在要使用此定义的条件。</span><span class="sxs-lookup"><span data-stu-id="06019-118">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="06019-119">视图 （格式） 的控件的 EntrySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="06019-119">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="06019-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="06019-120">Optional element.</span></span><br /><br /> <span data-ttu-id="06019-121">指定一组使用控件的此定义的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="06019-121">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="06019-122">EntrySelectedBy 视图 （格式） 的控件的类型名称元素</span><span class="sxs-lookup"><span data-stu-id="06019-122">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="06019-123">可选元素。</span><span class="sxs-lookup"><span data-stu-id="06019-123">Optional element.</span></span><br /><br /> <span data-ttu-id="06019-124">指定将使用该控件的此定义的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="06019-124">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="06019-125">父元素</span><span class="sxs-lookup"><span data-stu-id="06019-125">Parent Elements</span></span>

|<span data-ttu-id="06019-126">元素</span><span class="sxs-lookup"><span data-stu-id="06019-126">Element</span></span>|<span data-ttu-id="06019-127">说明</span><span class="sxs-lookup"><span data-stu-id="06019-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06019-128">视图 （格式） 的控件的 CustomEntries CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="06019-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="06019-129">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="06019-129">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="06019-130">备注</span><span class="sxs-lookup"><span data-stu-id="06019-130">Remarks</span></span>

<span data-ttu-id="06019-131">使用选择条件来定义的条件必须存在要使用的定义的例如当一个对象具有特定属性时，或者特定属性值或脚本的计算结果为`true`。</span><span class="sxs-lookup"><span data-stu-id="06019-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="06019-132">有关选择条件的详细信息，请参阅[时视图条目定义条件或使用项](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="06019-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="06019-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="06019-133">See Also</span></span>

[<span data-ttu-id="06019-134">视图 （格式） 的控件的 CustomEntries CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="06019-134">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="06019-135">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="06019-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
