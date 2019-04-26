---
title: TableControl （格式） 的 EntrySelectedBy 的 SelectionCondition 的 TypeName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e97d56fb-4e35-447a-9282-26f10d0a4609
caps.latest.revision: 11
ms.openlocfilehash: fe65ac95cead7df0069ffdae666fb34b7309fbb6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083835"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="f9459-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f9459-102">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="f9459-103">指定触发条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="f9459-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="f9459-104">当存在此类型时，满足该条件，并使用表行。</span><span class="sxs-lookup"><span data-stu-id="f9459-104">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="f9459-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 （格式） TableRowEntry 元素 （格式） EntrySelectedBy 元素 TableRowEntry （格式）有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition TableRowEntry （格式） TypeName 元素 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="f9459-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f9459-106">语法</span><span class="sxs-lookup"><span data-stu-id="f9459-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f9459-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f9459-107">Attributes and Elements</span></span>

<span data-ttu-id="f9459-108">以下各节描述了特性、 子元素和父元素的`TypeName`元素。</span><span class="sxs-lookup"><span data-stu-id="f9459-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f9459-109">属性</span><span class="sxs-lookup"><span data-stu-id="f9459-109">Attributes</span></span>

<span data-ttu-id="f9459-110">无。</span><span class="sxs-lookup"><span data-stu-id="f9459-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f9459-111">子元素</span><span class="sxs-lookup"><span data-stu-id="f9459-111">Child Elements</span></span>

<span data-ttu-id="f9459-112">无。</span><span class="sxs-lookup"><span data-stu-id="f9459-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f9459-113">父元素</span><span class="sxs-lookup"><span data-stu-id="f9459-113">Parent Elements</span></span>

|<span data-ttu-id="f9459-114">元素</span><span class="sxs-lookup"><span data-stu-id="f9459-114">Element</span></span>|<span data-ttu-id="f9459-115">说明</span><span class="sxs-lookup"><span data-stu-id="f9459-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f9459-116">TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="f9459-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="f9459-117">定义要使用此表行中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="f9459-117">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f9459-118">文本值</span><span class="sxs-lookup"><span data-stu-id="f9459-118">Text Value</span></span>

<span data-ttu-id="f9459-119">指定.NET 类型的完全限定的名称，例如`System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="f9459-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="f9459-120">备注</span><span class="sxs-lookup"><span data-stu-id="f9459-120">Remarks</span></span>

<span data-ttu-id="f9459-121">选择条件可以指定任意数量的.NET 类型，或者选择设置，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="f9459-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="f9459-122">有关如何使用选择条件的详细信息，请参阅[时视图条目定义条件或使用项](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="f9459-122">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f9459-123">表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="f9459-123">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f9459-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f9459-124">See Also</span></span>

[<span data-ttu-id="f9459-125">创建表视图</span><span class="sxs-lookup"><span data-stu-id="f9459-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f9459-126">定义何时显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="f9459-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f9459-127">TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="f9459-127">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="f9459-128">有关 TableRowEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="f9459-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="f9459-129">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="f9459-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
