---
title: TableRowEntry 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3b4d9b-2b8c-4a3a-8887-6c606eb9d490
caps.latest.revision: 10
ms.openlocfilehash: 48011950ed64e78a84292762f2c7779003dc59fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364996"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="15090-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="15090-102">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="15090-103">指定触发条件的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="15090-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="15090-104">如果该属性存在，或其计算结果为 `true`，则满足条件，并使用表项。</span><span class="sxs-lookup"><span data-stu-id="15090-104">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="15090-105">用于 EntrySelectedBy 的配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（format） TableRowEntry 元素（格式）适用于 EntrySelectedBy 的 TableRowEntry （Format） PropertyName 元素的 SelectionCondition 元素，适用于 EntrySelectedBy 的 SelectionCondition for TableRowEntry （Format）</span><span class="sxs-lookup"><span data-stu-id="15090-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="15090-106">语法</span><span class="sxs-lookup"><span data-stu-id="15090-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="15090-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="15090-107">Attributes and Elements</span></span>

<span data-ttu-id="15090-108">以下各节介绍了 `PropertyName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="15090-108">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="15090-109">属性</span><span class="sxs-lookup"><span data-stu-id="15090-109">Attributes</span></span>

<span data-ttu-id="15090-110">无。</span><span class="sxs-lookup"><span data-stu-id="15090-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="15090-111">子元素</span><span class="sxs-lookup"><span data-stu-id="15090-111">Child Elements</span></span>

<span data-ttu-id="15090-112">无。</span><span class="sxs-lookup"><span data-stu-id="15090-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="15090-113">父元素</span><span class="sxs-lookup"><span data-stu-id="15090-113">Parent Elements</span></span>

|<span data-ttu-id="15090-114">元素</span><span class="sxs-lookup"><span data-stu-id="15090-114">Element</span></span>|<span data-ttu-id="15090-115">描述</span><span class="sxs-lookup"><span data-stu-id="15090-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="15090-116">TableRowEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="15090-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="15090-117">定义要使用此表项必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="15090-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="15090-118">文本值</span><span class="sxs-lookup"><span data-stu-id="15090-118">Text Value</span></span>

<span data-ttu-id="15090-119">指定 .NET 属性名称。</span><span class="sxs-lookup"><span data-stu-id="15090-119">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="15090-120">备注</span><span class="sxs-lookup"><span data-stu-id="15090-120">Remarks</span></span>

<span data-ttu-id="15090-121">选择条件必须指定至少一个属性名称或脚本块，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="15090-121">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="15090-122">有关如何使用选择条件的详细信息，请参阅[定义使用视图条目或项的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="15090-122">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="15090-123">有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="15090-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="15090-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="15090-124">See Also</span></span>

[<span data-ttu-id="15090-125">创建表视图</span><span class="sxs-lookup"><span data-stu-id="15090-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="15090-126">定义显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="15090-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="15090-127">TableRowEntry 的 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="15090-127">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="15090-128">TableRowEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="15090-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="15090-129">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="15090-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
