---
title: 有关 WideControl （格式） 的 EntrySelectedBy SelectionCondition 的 TypeName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 0d7bbfd8be3bf2bd1af75a45ca4db016dfb6bff6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857953"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="4ccbc-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="4ccbc-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="4ccbc-103">指定触发条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="4ccbc-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="4ccbc-104">当存在此类型时，使用该定义。</span><span class="sxs-lookup"><span data-stu-id="4ccbc-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="4ccbc-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） WideEntries 元素 （格式） WideEntry 元素 （格式） EntrySelectedBy 元素 WideEntry （格式） SelectionCondition 元素EntrySelectedBy WideEntry （格式） 的 WideEntry （格式） 的 EntrySelectedBy SelectionCondition TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="4ccbc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4ccbc-106">语法</span><span class="sxs-lookup"><span data-stu-id="4ccbc-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4ccbc-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="4ccbc-107">Attributes and Elements</span></span>

<span data-ttu-id="4ccbc-108">以下各节描述了特性、 子元素和父元素的`TypeName`元素。</span><span class="sxs-lookup"><span data-stu-id="4ccbc-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4ccbc-109">特性</span><span class="sxs-lookup"><span data-stu-id="4ccbc-109">Attributes</span></span>

<span data-ttu-id="4ccbc-110">无。</span><span class="sxs-lookup"><span data-stu-id="4ccbc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4ccbc-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4ccbc-111">Child Elements</span></span>

<span data-ttu-id="4ccbc-112">无。</span><span class="sxs-lookup"><span data-stu-id="4ccbc-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4ccbc-113">父元素</span><span class="sxs-lookup"><span data-stu-id="4ccbc-113">Parent Elements</span></span>

|<span data-ttu-id="4ccbc-114">元素</span><span class="sxs-lookup"><span data-stu-id="4ccbc-114">Element</span></span>|<span data-ttu-id="4ccbc-115">描述</span><span class="sxs-lookup"><span data-stu-id="4ccbc-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4ccbc-116">WideEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="4ccbc-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="4ccbc-117">定义要使用此宽条目中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="4ccbc-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4ccbc-118">文本值</span><span class="sxs-lookup"><span data-stu-id="4ccbc-118">Text Value</span></span>

<span data-ttu-id="4ccbc-119">指定.NET 类型的完全限定的名称，例如`System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="4ccbc-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="4ccbc-120">备注</span><span class="sxs-lookup"><span data-stu-id="4ccbc-120">Remarks</span></span>

<span data-ttu-id="4ccbc-121">选择条件可以指定.NET 类型，或者选择设置，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="4ccbc-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="4ccbc-122">有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="4ccbc-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="4ccbc-123">有关较宽的视图的其他组件的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="4ccbc-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4ccbc-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4ccbc-124">See Also</span></span>

[<span data-ttu-id="4ccbc-125">时发生较宽的视图</span><span class="sxs-lookup"><span data-stu-id="4ccbc-125">Creatng a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="4ccbc-126">定义何时显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="4ccbc-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="4ccbc-127">WideEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="4ccbc-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="4ccbc-128">有关 WideEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="4ccbc-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="4ccbc-129">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="4ccbc-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
