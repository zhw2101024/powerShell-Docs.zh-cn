---
title: TableControl 的 SelectionCondition for EntrySelectedBy 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361466"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="5204e-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5204e-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="5204e-103">指定触发条件的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="5204e-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="5204e-104">如果存在此类型，则满足条件，并使用表行。</span><span class="sxs-lookup"><span data-stu-id="5204e-104">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="5204e-105">用于 EntrySelectedBy 的配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（format） TableRowEntry 元素（格式）适用于 EntrySelectedBy for TableRowEntry （Format） TypeName 元素的 SelectionCondition 元素 for SelectionCondition for EntrySelectedBy for TableRowEntry （Format）</span><span class="sxs-lookup"><span data-stu-id="5204e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5204e-106">语法</span><span class="sxs-lookup"><span data-stu-id="5204e-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5204e-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="5204e-107">Attributes and Elements</span></span>

<span data-ttu-id="5204e-108">以下各节介绍了 `TypeName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5204e-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5204e-109">属性</span><span class="sxs-lookup"><span data-stu-id="5204e-109">Attributes</span></span>

<span data-ttu-id="5204e-110">无。</span><span class="sxs-lookup"><span data-stu-id="5204e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5204e-111">子元素</span><span class="sxs-lookup"><span data-stu-id="5204e-111">Child Elements</span></span>

<span data-ttu-id="5204e-112">无。</span><span class="sxs-lookup"><span data-stu-id="5204e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5204e-113">父元素</span><span class="sxs-lookup"><span data-stu-id="5204e-113">Parent Elements</span></span>

|<span data-ttu-id="5204e-114">元素</span><span class="sxs-lookup"><span data-stu-id="5204e-114">Element</span></span>|<span data-ttu-id="5204e-115">描述</span><span class="sxs-lookup"><span data-stu-id="5204e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5204e-116">TableRowEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5204e-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="5204e-117">定义要使用此表行必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="5204e-117">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5204e-118">文本值</span><span class="sxs-lookup"><span data-stu-id="5204e-118">Text Value</span></span>

<span data-ttu-id="5204e-119">指定 .NET 类型的完全限定名，如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="5204e-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="5204e-120">备注</span><span class="sxs-lookup"><span data-stu-id="5204e-120">Remarks</span></span>

<span data-ttu-id="5204e-121">选择条件可以指定任意数量的 .NET 类型或选择集，但是不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="5204e-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="5204e-122">有关如何使用选择条件的详细信息，请参阅[定义使用视图条目或项的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="5204e-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="5204e-123">有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="5204e-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5204e-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5204e-124">See Also</span></span>

[<span data-ttu-id="5204e-125">创建表视图</span><span class="sxs-lookup"><span data-stu-id="5204e-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="5204e-126">定义显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="5204e-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="5204e-127">TableRowEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5204e-127">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="5204e-128">TableRowEntry 的 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="5204e-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="5204e-129">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="5204e-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
