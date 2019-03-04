---
title: WideEntry （格式） 的 EntrySelectedBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854973"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="e2a17-102">EntrySelectedBy Element for WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="e2a17-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="e2a17-103">定义使用宽视图或必须存在要使用此定义的条件的此定义的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="e2a17-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="e2a17-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） WideEntries 元素 （格式） WideEntry 元素 （格式） EntrySelectedBy 元素 WideEntry （格式）</span><span class="sxs-lookup"><span data-stu-id="e2a17-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e2a17-105">语法</span><span class="sxs-lookup"><span data-stu-id="e2a17-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e2a17-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="e2a17-106">Attributes and Elements</span></span>

<span data-ttu-id="e2a17-107">以下各节描述了特性、 子元素和父元素的`EntrySelectedBy`元素。</span><span class="sxs-lookup"><span data-stu-id="e2a17-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e2a17-108">特性</span><span class="sxs-lookup"><span data-stu-id="e2a17-108">Attributes</span></span>

<span data-ttu-id="e2a17-109">无。</span><span class="sxs-lookup"><span data-stu-id="e2a17-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e2a17-110">子元素</span><span class="sxs-lookup"><span data-stu-id="e2a17-110">Child Elements</span></span>

|<span data-ttu-id="e2a17-111">元素</span><span class="sxs-lookup"><span data-stu-id="e2a17-111">Element</span></span>|<span data-ttu-id="e2a17-112">描述</span><span class="sxs-lookup"><span data-stu-id="e2a17-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e2a17-113">WideEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="e2a17-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="e2a17-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="e2a17-114">Optional element.</span></span><br /><br /> <span data-ttu-id="e2a17-115">定义必须存在要使用此宽的视图定义的条件。</span><span class="sxs-lookup"><span data-stu-id="e2a17-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="e2a17-116">WideEntry （格式） 的 EntrySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="e2a17-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="e2a17-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="e2a17-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e2a17-118">指定一组使用此宽的视图定义的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="e2a17-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="e2a17-119">WideEntry （格式） 的 EntrySelectedBy 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="e2a17-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="e2a17-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="e2a17-120">Optional element.</span></span><br /><br /> <span data-ttu-id="e2a17-121">指定将使用此宽的视图定义的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="e2a17-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e2a17-122">父元素</span><span class="sxs-lookup"><span data-stu-id="e2a17-122">Parent Elements</span></span>

|<span data-ttu-id="e2a17-123">元素</span><span class="sxs-lookup"><span data-stu-id="e2a17-123">Element</span></span>|<span data-ttu-id="e2a17-124">描述</span><span class="sxs-lookup"><span data-stu-id="e2a17-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e2a17-125">WideEntry 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="e2a17-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="e2a17-126">提供了宽的视图的定义。</span><span class="sxs-lookup"><span data-stu-id="e2a17-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e2a17-127">备注</span><span class="sxs-lookup"><span data-stu-id="e2a17-127">Remarks</span></span>

<span data-ttu-id="e2a17-128">必须指定至少一个类型、 选择组或宽的视图定义的选择条件。</span><span class="sxs-lookup"><span data-stu-id="e2a17-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="e2a17-129">可以使用的子元素的数目没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="e2a17-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="e2a17-130">使用选择条件来定义要使用，例如当一个对象具有特定属性的定义中必须存在一个条件或特定属性值或脚本值的计算结果为`true`。</span><span class="sxs-lookup"><span data-stu-id="e2a17-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="e2a17-131">有关选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e2a17-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e2a17-132">有关较宽的视图的其他组件的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="e2a17-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2a17-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e2a17-133">See Also</span></span>

[<span data-ttu-id="e2a17-134">WideEntry 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="e2a17-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="e2a17-135">WideEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="e2a17-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="e2a17-136">WideEntry （格式） 的 EntrySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="e2a17-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="e2a17-137">WideEntry （格式） 的 EntrySelectedBy 的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="e2a17-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="e2a17-138">创建较宽的视图</span><span class="sxs-lookup"><span data-stu-id="e2a17-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e2a17-139">定义用于显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="e2a17-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e2a17-140">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="e2a17-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
