---
title: WideControl 的 SelectionCondition for EntrySelectedBy 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d6d43fa-c900-4e2f-952d-deccd584236f
caps.latest.revision: 11
ms.openlocfilehash: 6142350e3843a5feddcb5cee8901bbfa607d8d4c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368056"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="1e741-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="1e741-102">TypeName Element for SelectionCondition for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="1e741-103">指定触发条件的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="1e741-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="1e741-104">如果存在此类型，则使用定义。</span><span class="sxs-lookup"><span data-stu-id="1e741-104">When this type is present, the definition is used.</span></span>

<span data-ttu-id="1e741-105">配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（format） EntrySelectedBy 元素 for WideEntry （Format） SelectionCondition 元素 forEntrySelectedBy for WideEntry （Format） SelectionCondition for EntrySelectedBy for WideEntry 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="1e741-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1e741-106">语法</span><span class="sxs-lookup"><span data-stu-id="1e741-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1e741-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="1e741-107">Attributes and Elements</span></span>

<span data-ttu-id="1e741-108">以下各节介绍了 `TypeName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1e741-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1e741-109">属性</span><span class="sxs-lookup"><span data-stu-id="1e741-109">Attributes</span></span>

<span data-ttu-id="1e741-110">无。</span><span class="sxs-lookup"><span data-stu-id="1e741-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1e741-111">子元素</span><span class="sxs-lookup"><span data-stu-id="1e741-111">Child Elements</span></span>

<span data-ttu-id="1e741-112">无。</span><span class="sxs-lookup"><span data-stu-id="1e741-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1e741-113">父元素</span><span class="sxs-lookup"><span data-stu-id="1e741-113">Parent Elements</span></span>

|<span data-ttu-id="1e741-114">元素</span><span class="sxs-lookup"><span data-stu-id="1e741-114">Element</span></span>|<span data-ttu-id="1e741-115">描述</span><span class="sxs-lookup"><span data-stu-id="1e741-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1e741-116">WideEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1e741-116">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="1e741-117">定义要使用此宽项时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="1e741-117">Defines the condition that must exist for this wide entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1e741-118">文本值</span><span class="sxs-lookup"><span data-stu-id="1e741-118">Text Value</span></span>

<span data-ttu-id="1e741-119">指定 .NET 类型的完全限定名，如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="1e741-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="1e741-120">备注</span><span class="sxs-lookup"><span data-stu-id="1e741-120">Remarks</span></span>

<span data-ttu-id="1e741-121">选择条件可以指定 .NET 类型或选择集，但是不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="1e741-121">The selection condition can specify a .NET type or a selection set, but cannot specify both.</span></span> <span data-ttu-id="1e741-122">有关如何使用选择条件的详细信息，请参阅为[数据显示定义条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="1e741-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="1e741-123">有关大视图的其他组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="1e741-123">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1e741-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1e741-124">See Also</span></span>

[<span data-ttu-id="1e741-125">创建宽视图</span><span class="sxs-lookup"><span data-stu-id="1e741-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="1e741-126">定义显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="1e741-126">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="1e741-127">WideEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1e741-127">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="1e741-128">WideEntry 的 EntrySelectedBy 的 SelectionCondition 的 SelectionSetName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="1e741-128">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="1e741-129">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="1e741-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
