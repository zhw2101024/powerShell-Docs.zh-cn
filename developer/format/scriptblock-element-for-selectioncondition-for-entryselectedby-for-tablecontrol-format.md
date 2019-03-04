---
title: TableControl （格式） 的 EntrySelectedBy 的 SelectionCondition 的脚本块元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b11fbcf-3426-48ae-9319-2c847969f723
caps.latest.revision: 10
ms.openlocfilehash: 7afc834e68ef332bee1e23da782fb5c5527fcf54
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855573"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="7ae5f-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7ae5f-102">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="7ae5f-103">指定触发条件的脚本块。</span><span class="sxs-lookup"><span data-stu-id="7ae5f-103">Specifies the script block that triggers the condition.</span></span> <span data-ttu-id="7ae5f-104">当此脚本的计算结果为`true`、 满足该条件，以及使用的表项。</span><span class="sxs-lookup"><span data-stu-id="7ae5f-104">When this script is evaluated to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="7ae5f-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 （格式） TableRowEntry 元素 （格式） EntrySelectedBy 元素 TableRowEntry （格式）SelectionCondition EntrySelectedBy TableRowEntry （格式） 的 EntrySelectedBy 的 SelectionCondition TableRowEntry （格式） 脚本块元素的元素</span><span class="sxs-lookup"><span data-stu-id="7ae5f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7ae5f-106">语法</span><span class="sxs-lookup"><span data-stu-id="7ae5f-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7ae5f-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="7ae5f-107">Attributes and Elements</span></span>

<span data-ttu-id="7ae5f-108">以下各节描述了特性、 子元素和父元素的`ScriptBlock`元素。</span><span class="sxs-lookup"><span data-stu-id="7ae5f-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7ae5f-109">特性</span><span class="sxs-lookup"><span data-stu-id="7ae5f-109">Attributes</span></span>

<span data-ttu-id="7ae5f-110">无。</span><span class="sxs-lookup"><span data-stu-id="7ae5f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7ae5f-111">子元素</span><span class="sxs-lookup"><span data-stu-id="7ae5f-111">Child Elements</span></span>

<span data-ttu-id="7ae5f-112">无。</span><span class="sxs-lookup"><span data-stu-id="7ae5f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7ae5f-113">父元素</span><span class="sxs-lookup"><span data-stu-id="7ae5f-113">Parent Elements</span></span>

|<span data-ttu-id="7ae5f-114">元素</span><span class="sxs-lookup"><span data-stu-id="7ae5f-114">Element</span></span>|<span data-ttu-id="7ae5f-115">描述</span><span class="sxs-lookup"><span data-stu-id="7ae5f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7ae5f-116">TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="7ae5f-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="7ae5f-117">定义要使用此表条目中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="7ae5f-117">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7ae5f-118">文本值</span><span class="sxs-lookup"><span data-stu-id="7ae5f-118">Text Value</span></span>

<span data-ttu-id="7ae5f-119">指定计算的脚本。</span><span class="sxs-lookup"><span data-stu-id="7ae5f-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="7ae5f-120">备注</span><span class="sxs-lookup"><span data-stu-id="7ae5f-120">Remarks</span></span>

<span data-ttu-id="7ae5f-121">选择条件必须指定至少一个脚本块或属性名称，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="7ae5f-121">The selection condition must specify at least one script block or property name, but cannot specify both.</span></span> <span data-ttu-id="7ae5f-122">有关如何使用选择条件的详细信息，请参阅[时视图条目定义条件或使用项](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7ae5f-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="7ae5f-123">表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="7ae5f-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7ae5f-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7ae5f-124">See Also</span></span>

[<span data-ttu-id="7ae5f-125">创建表视图</span><span class="sxs-lookup"><span data-stu-id="7ae5f-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="7ae5f-126">定义何时显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="7ae5f-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7ae5f-127">有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="7ae5f-127">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="7ae5f-128">TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="7ae5f-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="7ae5f-129">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="7ae5f-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
