---
title: 配置 （格式） 的控件的 SelectionCondition SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7dcaeadb-4e79-47a0-96e2-8952af26abbe
caps.latest.revision: 7
ms.openlocfilehash: 5db35a8094ea2bb966c8d6a96802c72f64c05c17
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063995"
---
# <a name="selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="b2845-102">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="b2845-102">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="b2845-103">指定.NET 类型的触发器条件的集。</span><span class="sxs-lookup"><span data-stu-id="b2845-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="b2845-104">当存在任何此集中的类型时，满足该条件，并使用此控件显示该对象。</span><span class="sxs-lookup"><span data-stu-id="b2845-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this control.</span></span> <span data-ttu-id="b2845-105">定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。</span><span class="sxs-lookup"><span data-stu-id="b2845-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="b2845-106">配置 （格式） 的配置 （格式） 的 Controls 的 CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素配置 （格式） 的 Controls 的配置 （格式） 的 Controls 的配置 （格式） 的 Controls 的 EntrySelectedBy SelectionCondition 元素 CustomEntry EntrySelectedBy 元素 CustomControl CustomEntry 元素SelectionCondition 的 Controls 的配置 （格式） 的配置 （格式） SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="b2845-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b2845-107">语法</span><span class="sxs-lookup"><span data-stu-id="b2845-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b2845-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b2845-108">Attributes and Elements</span></span>

<span data-ttu-id="b2845-109">以下各节描述了特性、 子元素和父元素的`SelectionSetName`元素。</span><span class="sxs-lookup"><span data-stu-id="b2845-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b2845-110">属性</span><span class="sxs-lookup"><span data-stu-id="b2845-110">Attributes</span></span>

<span data-ttu-id="b2845-111">无。</span><span class="sxs-lookup"><span data-stu-id="b2845-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b2845-112">子元素</span><span class="sxs-lookup"><span data-stu-id="b2845-112">Child Elements</span></span>

<span data-ttu-id="b2845-113">无。</span><span class="sxs-lookup"><span data-stu-id="b2845-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b2845-114">父元素</span><span class="sxs-lookup"><span data-stu-id="b2845-114">Parent Elements</span></span>

|<span data-ttu-id="b2845-115">元素</span><span class="sxs-lookup"><span data-stu-id="b2845-115">Element</span></span>|<span data-ttu-id="b2845-116">说明</span><span class="sxs-lookup"><span data-stu-id="b2845-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b2845-117">配置 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="b2845-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="b2845-118">定义必须存在要使用的控件定义的条件。</span><span class="sxs-lookup"><span data-stu-id="b2845-118">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b2845-119">文本值</span><span class="sxs-lookup"><span data-stu-id="b2845-119">Text Value</span></span>

<span data-ttu-id="b2845-120">指定所选内容集的名称。</span><span class="sxs-lookup"><span data-stu-id="b2845-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2845-121">备注</span><span class="sxs-lookup"><span data-stu-id="b2845-121">Remarks</span></span>

<span data-ttu-id="b2845-122">所选内容集是常见的可以使用的格式设置文件定义任何视图的.NET 对象分组。</span><span class="sxs-lookup"><span data-stu-id="b2845-122">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="b2845-123">有关创建和引用所选内容集的详细信息，请参阅[定义设置的对象](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="b2845-123">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="b2845-124">选择条件可以指定所选内容集或.NET 类型，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="b2845-124">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="b2845-125">有关如何使用选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="b2845-125">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b2845-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2845-126">See Also</span></span>

[<span data-ttu-id="b2845-127">配置 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="b2845-127">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="b2845-128">定义何时显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="b2845-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b2845-129">定义的选项集</span><span class="sxs-lookup"><span data-stu-id="b2845-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="b2845-130">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="b2845-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
