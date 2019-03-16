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
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055967"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="4efe9-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="4efe9-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="4efe9-103">指定触发条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="4efe9-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="4efe9-104">当存在此类型时，使用该定义。</span><span class="sxs-lookup"><span data-stu-id="4efe9-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="4efe9-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） WideEntries 元素 （格式） WideEntry 元素 （格式） EntrySelectedBy 元素 WideEntry （格式） SelectionCondition 元素EntrySelectedBy WideEntry （格式） 的 WideEntry （格式） 的 EntrySelectedBy SelectionCondition TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="4efe9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4efe9-106">语法</span><span class="sxs-lookup"><span data-stu-id="4efe9-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4efe9-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="4efe9-107">Attributes and Elements</span></span>

<span data-ttu-id="4efe9-108">以下各节描述了特性、 子元素和父元素的`TypeName`元素。</span><span class="sxs-lookup"><span data-stu-id="4efe9-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4efe9-109">属性</span><span class="sxs-lookup"><span data-stu-id="4efe9-109">Attributes</span></span>

<span data-ttu-id="4efe9-110">无。</span><span class="sxs-lookup"><span data-stu-id="4efe9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4efe9-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4efe9-111">Child Elements</span></span>

<span data-ttu-id="4efe9-112">无。</span><span class="sxs-lookup"><span data-stu-id="4efe9-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4efe9-113">父元素</span><span class="sxs-lookup"><span data-stu-id="4efe9-113">Parent Elements</span></span>

|<span data-ttu-id="4efe9-114">元素</span><span class="sxs-lookup"><span data-stu-id="4efe9-114">Element</span></span>|<span data-ttu-id="4efe9-115">说明</span><span class="sxs-lookup"><span data-stu-id="4efe9-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4efe9-116">WideEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="4efe9-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="4efe9-117">定义要使用此宽条目中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="4efe9-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4efe9-118">文本值</span><span class="sxs-lookup"><span data-stu-id="4efe9-118">Text Value</span></span>

<span data-ttu-id="4efe9-119">指定.NET 类型的完全限定的名称，例如`System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="4efe9-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="4efe9-120">备注</span><span class="sxs-lookup"><span data-stu-id="4efe9-120">Remarks</span></span>

<span data-ttu-id="4efe9-121">选择条件可以指定.NET 类型，或者选择设置，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="4efe9-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="4efe9-122">有关如何使用选择条件的详细信息，请参阅[定义的条件显示数据时](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="4efe9-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="4efe9-123">有关较宽的视图的其他组件的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="4efe9-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4efe9-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4efe9-124">See Also</span></span>

[<span data-ttu-id="4efe9-125">创建较宽的视图</span><span class="sxs-lookup"><span data-stu-id="4efe9-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="4efe9-126">定义何时显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="4efe9-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="4efe9-127">WideEntry （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="4efe9-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="4efe9-128">有关 WideEntry （格式） 的 EntrySelectedBy SelectionCondition SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="4efe9-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="4efe9-129">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="4efe9-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
