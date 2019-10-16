---
title: WideControl （Format）的 EntrySelectedBy 的 SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361976"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="44ef0-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="44ef0-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="44ef0-103">为定义指定一组 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="44ef0-103">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="44ef0-104">当显示其中一个对象时，将使用该定义。</span><span class="sxs-lookup"><span data-stu-id="44ef0-104">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="44ef0-105">配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（format） EntrySelectedBy 元素 for WideEntry （Format） SelectionSetName 元素 forEntrySelectedBy for WideEntry （Format）</span><span class="sxs-lookup"><span data-stu-id="44ef0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="44ef0-106">语法</span><span class="sxs-lookup"><span data-stu-id="44ef0-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="44ef0-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="44ef0-107">Attributes and Elements</span></span>

<span data-ttu-id="44ef0-108">以下各节介绍了 `SelectionSetName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="44ef0-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="44ef0-109">属性</span><span class="sxs-lookup"><span data-stu-id="44ef0-109">Attributes</span></span>

<span data-ttu-id="44ef0-110">无。</span><span class="sxs-lookup"><span data-stu-id="44ef0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="44ef0-111">子元素</span><span class="sxs-lookup"><span data-stu-id="44ef0-111">Child Elements</span></span>

<span data-ttu-id="44ef0-112">无。</span><span class="sxs-lookup"><span data-stu-id="44ef0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="44ef0-113">父元素</span><span class="sxs-lookup"><span data-stu-id="44ef0-113">Parent Elements</span></span>

|<span data-ttu-id="44ef0-114">元素</span><span class="sxs-lookup"><span data-stu-id="44ef0-114">Element</span></span>|<span data-ttu-id="44ef0-115">描述</span><span class="sxs-lookup"><span data-stu-id="44ef0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="44ef0-116">WideEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="44ef0-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="44ef0-117">定义使用此宽项的 .NET 类型或此项要使用的条件。</span><span class="sxs-lookup"><span data-stu-id="44ef0-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="44ef0-118">文本值</span><span class="sxs-lookup"><span data-stu-id="44ef0-118">Text Value</span></span>

<span data-ttu-id="44ef0-119">指定选择集的名称。</span><span class="sxs-lookup"><span data-stu-id="44ef0-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="44ef0-120">备注</span><span class="sxs-lookup"><span data-stu-id="44ef0-120">Remarks</span></span>

<span data-ttu-id="44ef0-121">每个定义必须指定一个类型名称、选择集或选择条件。</span><span class="sxs-lookup"><span data-stu-id="44ef0-121">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="44ef0-122">当要定义在多个视图中使用的一组对象时，通常使用选择集。</span><span class="sxs-lookup"><span data-stu-id="44ef0-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="44ef0-123">例如，您可能希望为同一组对象创建表视图和列表视图。</span><span class="sxs-lookup"><span data-stu-id="44ef0-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="44ef0-124">有关定义选择集的详细信息，请参阅为[视图定义对象集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="44ef0-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="44ef0-125">有关大视图的其他组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="44ef0-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="44ef0-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="44ef0-126">See Also</span></span>

[<span data-ttu-id="44ef0-127">创建宽视图</span><span class="sxs-lookup"><span data-stu-id="44ef0-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="44ef0-128">定义选择集</span><span class="sxs-lookup"><span data-stu-id="44ef0-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="44ef0-129">WideEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="44ef0-129">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="44ef0-130">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="44ef0-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
