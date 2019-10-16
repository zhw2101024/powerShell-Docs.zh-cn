---
title: 用于视图（格式）的 EntrySelectedBy 的 SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b594a064-746f-4900-99e4-7be7bf5aa5a2
caps.latest.revision: 7
ms.openlocfilehash: d540c99707f4e0796b2d408f2161a9208257ab32
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368346"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="a249d-102">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="a249d-102">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="a249d-103">指定一组使用此控件定义的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="a249d-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="a249d-104">定义可由视图使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="a249d-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="a249d-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 元素（format） Control 元素 for View （format） CustomControl 元素的控件元素，用于控件的 View （format） CustomEntries 元素CustomControl for view （format） CustomEntry 元素 for view （format）元素 for CustomEntries for view （format） EntrySelectedBy 元素 for view （format）元素 for CustomEntry for view （format） SelectionSetName 元素 for view （形式</span><span class="sxs-lookup"><span data-stu-id="a249d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a249d-106">语法</span><span class="sxs-lookup"><span data-stu-id="a249d-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="a249d-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="a249d-107">Attributes and Elements</span></span>

<span data-ttu-id="a249d-108">以下各节介绍了 `SelectionSetName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a249d-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a249d-109">属性</span><span class="sxs-lookup"><span data-stu-id="a249d-109">Attributes</span></span>

<span data-ttu-id="a249d-110">无</span><span class="sxs-lookup"><span data-stu-id="a249d-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="a249d-111">子元素</span><span class="sxs-lookup"><span data-stu-id="a249d-111">Child Elements</span></span>

<span data-ttu-id="a249d-112">无。</span><span class="sxs-lookup"><span data-stu-id="a249d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a249d-113">父元素</span><span class="sxs-lookup"><span data-stu-id="a249d-113">Parent Elements</span></span>

|<span data-ttu-id="a249d-114">元素</span><span class="sxs-lookup"><span data-stu-id="a249d-114">Element</span></span>|<span data-ttu-id="a249d-115">描述</span><span class="sxs-lookup"><span data-stu-id="a249d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a249d-116">用于视图的控件的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a249d-116">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="a249d-117">定义使用此控件定义的 .NET 类型或要使用此定义时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="a249d-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a249d-118">文本值</span><span class="sxs-lookup"><span data-stu-id="a249d-118">Text Value</span></span>

<span data-ttu-id="a249d-119">指定选择集的名称。</span><span class="sxs-lookup"><span data-stu-id="a249d-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="a249d-120">备注</span><span class="sxs-lookup"><span data-stu-id="a249d-120">Remarks</span></span>

<span data-ttu-id="a249d-121">每个控件定义都必须定义至少一个类型名称、选择集或选择条件。</span><span class="sxs-lookup"><span data-stu-id="a249d-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="a249d-122">当要定义在多个视图中使用的一组对象时，通常使用选择集。</span><span class="sxs-lookup"><span data-stu-id="a249d-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="a249d-123">有关定义选择集的详细信息，请参阅[定义选择集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="a249d-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a249d-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a249d-124">See Also</span></span>

[<span data-ttu-id="a249d-125">用于视图的控件的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a249d-125">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="a249d-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="a249d-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
