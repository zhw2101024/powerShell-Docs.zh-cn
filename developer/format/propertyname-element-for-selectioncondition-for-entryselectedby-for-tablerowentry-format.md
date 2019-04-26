---
title: PropertyName 元素为 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064656"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="a6389-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="a6389-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="a6389-103">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="a6389-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="a6389-104">存在此属性时或当计算结果为`true`、 满足该条件，以及使用的表项。</span><span class="sxs-lookup"><span data-stu-id="a6389-104">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="a6389-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 （格式） TableRowEntry 元素 （格式） EntrySelectedBy 元素 TableRowEntry （格式）有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition TableRowEntry （格式） PropertyName 元素 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="a6389-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a6389-106">语法</span><span class="sxs-lookup"><span data-stu-id="a6389-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a6389-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="a6389-107">Attributes and Elements</span></span>

<span data-ttu-id="a6389-108">以下各节描述了特性、 子元素和父元素的`PropertyName`元素。</span><span class="sxs-lookup"><span data-stu-id="a6389-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a6389-109">属性</span><span class="sxs-lookup"><span data-stu-id="a6389-109">Attributes</span></span>

<span data-ttu-id="a6389-110">无。</span><span class="sxs-lookup"><span data-stu-id="a6389-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a6389-111">子元素</span><span class="sxs-lookup"><span data-stu-id="a6389-111">Child Elements</span></span>

<span data-ttu-id="a6389-112">无。</span><span class="sxs-lookup"><span data-stu-id="a6389-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a6389-113">父元素</span><span class="sxs-lookup"><span data-stu-id="a6389-113">Parent Elements</span></span>

|<span data-ttu-id="a6389-114">元素</span><span class="sxs-lookup"><span data-stu-id="a6389-114">Element</span></span>|<span data-ttu-id="a6389-115">说明</span><span class="sxs-lookup"><span data-stu-id="a6389-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a6389-116">TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="a6389-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="a6389-117">定义要使用此表条目中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="a6389-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a6389-118">文本值</span><span class="sxs-lookup"><span data-stu-id="a6389-118">Text Value</span></span>

<span data-ttu-id="a6389-119">指定.NET 属性名称。</span><span class="sxs-lookup"><span data-stu-id="a6389-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="a6389-120">备注</span><span class="sxs-lookup"><span data-stu-id="a6389-120">Remarks</span></span>

<span data-ttu-id="a6389-121">选择条件必须指定至少一个属性名称或脚本块，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="a6389-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="a6389-122">有关如何使用选择条件的详细信息，请参阅[时视图条目定义条件或使用项](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a6389-122">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a6389-123">表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="a6389-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a6389-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a6389-124">See Also</span></span>

[<span data-ttu-id="a6389-125">创建表视图</span><span class="sxs-lookup"><span data-stu-id="a6389-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a6389-126">定义何时显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="a6389-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a6389-127">有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="a6389-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a6389-128">TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="a6389-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a6389-129">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="a6389-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
