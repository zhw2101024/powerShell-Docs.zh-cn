---
title: 有关 ListControl （格式） 的 EntrySelectedBy SelectionCondition 的 TypeName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd025a3a-3780-40db-a068-873e7df38015
caps.latest.revision: 9
ms.openlocfilehash: 2b76b040b39088cc9c3b9d6890c38df3c533b39f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083852"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="9267c-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="9267c-102">TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="9267c-103">指定触发条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="9267c-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="9267c-104">当存在此类型时，才使用列表项。</span><span class="sxs-lookup"><span data-stu-id="9267c-104">When this type is present, the list entry is used.</span></span>

<span data-ttu-id="9267c-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 ListControl （格式） EntrySelectedBy 元素 ListEntries ListControl （格式） ListEntry 元素ListEntry ListControl （格式） 的 ListControl （格式） 的 EntrySelectedBy SelectionCondition TypeName 元素 EntrySelectedBy ListControl （格式） SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="9267c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format) SelectionCondition Element for EntrySelectedBy for ListControl (Format) TypeName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9267c-106">语法</span><span class="sxs-lookup"><span data-stu-id="9267c-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9267c-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="9267c-107">Attributes and Elements</span></span>

<span data-ttu-id="9267c-108">以下各节描述了特性、 子元素和父元素的`TypeName`元素。</span><span class="sxs-lookup"><span data-stu-id="9267c-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9267c-109">属性</span><span class="sxs-lookup"><span data-stu-id="9267c-109">Attributes</span></span>

<span data-ttu-id="9267c-110">无。</span><span class="sxs-lookup"><span data-stu-id="9267c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9267c-111">子元素</span><span class="sxs-lookup"><span data-stu-id="9267c-111">Child Elements</span></span>

<span data-ttu-id="9267c-112">无。</span><span class="sxs-lookup"><span data-stu-id="9267c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9267c-113">父元素</span><span class="sxs-lookup"><span data-stu-id="9267c-113">Parent Elements</span></span>

|<span data-ttu-id="9267c-114">元素</span><span class="sxs-lookup"><span data-stu-id="9267c-114">Element</span></span>|<span data-ttu-id="9267c-115">说明</span><span class="sxs-lookup"><span data-stu-id="9267c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9267c-116">ListControl （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="9267c-116">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="9267c-117">定义要使用此列表项中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="9267c-117">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9267c-118">文本值</span><span class="sxs-lookup"><span data-stu-id="9267c-118">Text Value</span></span>

<span data-ttu-id="9267c-119">指定.NET 类型的完全限定的名称，例如`System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="9267c-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="9267c-120">备注</span><span class="sxs-lookup"><span data-stu-id="9267c-120">Remarks</span></span>

<span data-ttu-id="9267c-121">选择条件可以指定任意数量的.NET 类型，或者选择设置，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="9267c-121">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="9267c-122">有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="9267c-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="9267c-123">有关其他详细信息的组件的列表视图中，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="9267c-123">For more information about other the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9267c-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9267c-124">See Also</span></span>

[<span data-ttu-id="9267c-125">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="9267c-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="9267c-126">定义何时显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="9267c-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9267c-127">ListControl （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="9267c-127">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="9267c-128">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="9267c-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
