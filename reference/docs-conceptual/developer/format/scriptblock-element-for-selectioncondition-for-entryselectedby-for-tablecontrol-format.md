---
title: 用于 TableControl 的 EntrySelectedBy 的 SelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368576"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="d4b10-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d4b10-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="d4b10-103">指定触发条件的脚本块。</span><span class="sxs-lookup"><span data-stu-id="d4b10-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="d4b10-104">如果此脚本的计算结果为 `true`，则满足条件，并使用表项。</span><span class="sxs-lookup"><span data-stu-id="d4b10-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="d4b10-105">用于 EntrySelectedBy 的配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（format） TableRowEntry 元素（格式）SelectionCondition for EntrySelectedBy 的 TableRowEntry （Format） ScriptBlock 元素的 EntrySelectedBy 的 SelectionCondition 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="d4b10-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d4b10-106">语法</span><span class="sxs-lookup"><span data-stu-id="d4b10-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d4b10-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="d4b10-107">Attributes and Elements</span></span>

<span data-ttu-id="d4b10-108">以下各节介绍了 `ScriptBlock` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d4b10-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d4b10-109">属性</span><span class="sxs-lookup"><span data-stu-id="d4b10-109">Attributes</span></span>

<span data-ttu-id="d4b10-110">无。</span><span class="sxs-lookup"><span data-stu-id="d4b10-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d4b10-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d4b10-111">Child Elements</span></span>

<span data-ttu-id="d4b10-112">无。</span><span class="sxs-lookup"><span data-stu-id="d4b10-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d4b10-113">父元素</span><span class="sxs-lookup"><span data-stu-id="d4b10-113">Parent Elements</span></span>

|<span data-ttu-id="d4b10-114">元素</span><span class="sxs-lookup"><span data-stu-id="d4b10-114">Element</span></span>|<span data-ttu-id="d4b10-115">描述</span><span class="sxs-lookup"><span data-stu-id="d4b10-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d4b10-116">TableRowEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d4b10-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="d4b10-117">定义要使用此表项必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="d4b10-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d4b10-118">文本值</span><span class="sxs-lookup"><span data-stu-id="d4b10-118">Text Value</span></span>

<span data-ttu-id="d4b10-119">指定要评估的脚本。</span><span class="sxs-lookup"><span data-stu-id="d4b10-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="d4b10-120">备注</span><span class="sxs-lookup"><span data-stu-id="d4b10-120">Remarks</span></span>

<span data-ttu-id="d4b10-121">选择条件必须指定至少一个脚本块或属性名称，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="d4b10-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="d4b10-122">有关如何使用选择条件的详细信息，请参阅[定义使用视图条目或项的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="d4b10-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="d4b10-123">有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d4b10-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d4b10-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4b10-124">See Also</span></span>

[<span data-ttu-id="d4b10-125">创建表视图</span><span class="sxs-lookup"><span data-stu-id="d4b10-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d4b10-126">定义显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="d4b10-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d4b10-127">TableRowEntry 的 SelectionCondition for EntrySelectedBy 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="d4b10-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="d4b10-128">TableRowEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d4b10-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="d4b10-129">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="d4b10-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
