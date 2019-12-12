---
title: WideEntry 的 EntrySelectedBy 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e0c98933-b7a5-4205-b811-06c0b0bf8988
caps.latest.revision: 9
ms.openlocfilehash: 54c7c261a23075721cd7bce75e530150dc0e0212
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363326"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="1aae9-102">EntrySelectedBy Element for WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="1aae9-102">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="1aae9-103">定义使用此类定义的 .NET 类型或使用此定义时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="1aae9-103">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="1aae9-104">用于 EntrySelectedBy 的配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（format） WideEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1aae9-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1aae9-105">语法</span><span class="sxs-lookup"><span data-stu-id="1aae9-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1aae9-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="1aae9-106">Attributes and Elements</span></span>

<span data-ttu-id="1aae9-107">以下各节介绍了 `EntrySelectedBy` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1aae9-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1aae9-108">属性</span><span class="sxs-lookup"><span data-stu-id="1aae9-108">Attributes</span></span>

<span data-ttu-id="1aae9-109">无。</span><span class="sxs-lookup"><span data-stu-id="1aae9-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1aae9-110">子元素</span><span class="sxs-lookup"><span data-stu-id="1aae9-110">Child Elements</span></span>

|<span data-ttu-id="1aae9-111">元素</span><span class="sxs-lookup"><span data-stu-id="1aae9-111">Element</span></span>|<span data-ttu-id="1aae9-112">描述</span><span class="sxs-lookup"><span data-stu-id="1aae9-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1aae9-113">WideEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1aae9-113">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="1aae9-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="1aae9-114">Optional element.</span></span><br /><br /> <span data-ttu-id="1aae9-115">定义要使用此宽视图定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="1aae9-115">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="1aae9-116">WideEntry 的 EntrySelectedBy 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1aae9-116">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="1aae9-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="1aae9-117">Optional element.</span></span><br /><br /> <span data-ttu-id="1aae9-118">指定一组使用此宽视图定义的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="1aae9-118">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="1aae9-119">WideEntry 的 EntrySelectedBy 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="1aae9-119">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="1aae9-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="1aae9-120">Optional element.</span></span><br /><br /> <span data-ttu-id="1aae9-121">指定使用此宽视图定义的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="1aae9-121">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1aae9-122">父元素</span><span class="sxs-lookup"><span data-stu-id="1aae9-122">Parent Elements</span></span>

|<span data-ttu-id="1aae9-123">元素</span><span class="sxs-lookup"><span data-stu-id="1aae9-123">Element</span></span>|<span data-ttu-id="1aae9-124">描述</span><span class="sxs-lookup"><span data-stu-id="1aae9-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1aae9-125">WideEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1aae9-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="1aae9-126">提供宽视图的定义。</span><span class="sxs-lookup"><span data-stu-id="1aae9-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1aae9-127">备注</span><span class="sxs-lookup"><span data-stu-id="1aae9-127">Remarks</span></span>

<span data-ttu-id="1aae9-128">对于宽视图定义，必须至少指定一个类型、选择集或选择条件。</span><span class="sxs-lookup"><span data-stu-id="1aae9-128">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="1aae9-129">您可以使用的子元素数没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="1aae9-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="1aae9-130">选择条件用于定义要使用的定义必须存在的条件，例如当对象具有特定属性或特定属性值或脚本值的计算结果为 `true`时。</span><span class="sxs-lookup"><span data-stu-id="1aae9-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="1aae9-131">有关选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="1aae9-131">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1aae9-132">有关大视图的其他组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="1aae9-132">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1aae9-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1aae9-133">See Also</span></span>

[<span data-ttu-id="1aae9-134">WideEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1aae9-134">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="1aae9-135">WideEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1aae9-135">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="1aae9-136">WideEntry 的 EntrySelectedBy 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1aae9-136">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="1aae9-137">WideEntry 的 EntrySelectedBy 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="1aae9-137">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="1aae9-138">创建宽视图</span><span class="sxs-lookup"><span data-stu-id="1aae9-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="1aae9-139">定义显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="1aae9-139">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1aae9-140">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="1aae9-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
