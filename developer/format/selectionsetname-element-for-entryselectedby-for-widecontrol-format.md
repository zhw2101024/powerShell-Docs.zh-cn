---
title: WideControl （格式） 的 EntrySelectedBy SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c9c6e18f-6cca-465c-bd20-3969e7897a96
caps.latest.revision: 10
ms.openlocfilehash: 6b6a4a4647412d11d947f1dc4ea12d1e05ff536e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856793"
---
# <a name="selectionsetname-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="d0e7e-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d0e7e-102">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="d0e7e-103">指定一组定义的.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="d0e7e-103">Specifies a set of .NET objects for the definition.</span></span> <span data-ttu-id="d0e7e-104">定义用于显示这些对象之一时。</span><span class="sxs-lookup"><span data-stu-id="d0e7e-104">The definition is used whenever one of these objects is displayed.</span></span>

<span data-ttu-id="d0e7e-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） WideEntries 元素 （格式） WideEntry 元素 （格式） EntrySelectedBy 元素 WideEntry （格式） SelectionSetName 元素EntrySelectedBy 为 WideEntry （格式） 的</span><span class="sxs-lookup"><span data-stu-id="d0e7e-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d0e7e-106">语法</span><span class="sxs-lookup"><span data-stu-id="d0e7e-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d0e7e-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="d0e7e-107">Attributes and Elements</span></span>

<span data-ttu-id="d0e7e-108">以下各节描述了特性、 子元素和父元素的`SelectionSetName`元素。</span><span class="sxs-lookup"><span data-stu-id="d0e7e-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d0e7e-109">特性</span><span class="sxs-lookup"><span data-stu-id="d0e7e-109">Attributes</span></span>

<span data-ttu-id="d0e7e-110">无。</span><span class="sxs-lookup"><span data-stu-id="d0e7e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d0e7e-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d0e7e-111">Child Elements</span></span>

<span data-ttu-id="d0e7e-112">无。</span><span class="sxs-lookup"><span data-stu-id="d0e7e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d0e7e-113">父元素</span><span class="sxs-lookup"><span data-stu-id="d0e7e-113">Parent Elements</span></span>

|<span data-ttu-id="d0e7e-114">元素</span><span class="sxs-lookup"><span data-stu-id="d0e7e-114">Element</span></span>|<span data-ttu-id="d0e7e-115">描述</span><span class="sxs-lookup"><span data-stu-id="d0e7e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d0e7e-116">WideEntry （格式） 的 EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="d0e7e-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="d0e7e-117">定义使用此宽的项或要使用此项必须存在的条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="d0e7e-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d0e7e-118">文本值</span><span class="sxs-lookup"><span data-stu-id="d0e7e-118">Text Value</span></span>

<span data-ttu-id="d0e7e-119">指定所选内容集的名称。</span><span class="sxs-lookup"><span data-stu-id="d0e7e-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0e7e-120">备注</span><span class="sxs-lookup"><span data-stu-id="d0e7e-120">Remarks</span></span>

<span data-ttu-id="d0e7e-121">每个定义必须指定一个类型名称、 选择集或选择条件。</span><span class="sxs-lookup"><span data-stu-id="d0e7e-121">Each definition must specify one type name, selection set, or selection condition.</span></span>

<span data-ttu-id="d0e7e-122">当你想要在多个视图中定义的一组使用的对象时通常使用的选项集。</span><span class="sxs-lookup"><span data-stu-id="d0e7e-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="d0e7e-123">例如，你可能想要创建的表视图和同一组对象的列表视图。</span><span class="sxs-lookup"><span data-stu-id="d0e7e-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="d0e7e-124">有关定义的选项集的详细信息，请参阅[定义设置的对象图](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="d0e7e-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="d0e7e-125">有关较宽的视图的其他组件的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d0e7e-125">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d0e7e-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d0e7e-126">See Also</span></span>

[<span data-ttu-id="d0e7e-127">创建较宽的视图</span><span class="sxs-lookup"><span data-stu-id="d0e7e-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d0e7e-128">定义的选项集</span><span class="sxs-lookup"><span data-stu-id="d0e7e-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="d0e7e-129">WideEntry （格式） 的 EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="d0e7e-129">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="d0e7e-130">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="d0e7e-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
