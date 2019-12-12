---
title: 用于配置的控件（格式）的 EntrySelectedBy 的 SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364786"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="aad61-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="aad61-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="aad61-103">指定一组使用此控件定义的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="aad61-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="aad61-104">此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。</span><span class="sxs-lookup"><span data-stu-id="aad61-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="aad61-105">Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format） CustomEntry 元素 for CustomControl for EntrySelectedBy 元素 for CustomEntry for 元素 for for 元素 for for SelectionSetName for control for control （Format）</span><span class="sxs-lookup"><span data-stu-id="aad61-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aad61-106">语法</span><span class="sxs-lookup"><span data-stu-id="aad61-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="aad61-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="aad61-107">Attributes and Elements</span></span>

<span data-ttu-id="aad61-108">以下各节介绍了 `SelectionSetName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="aad61-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aad61-109">属性</span><span class="sxs-lookup"><span data-stu-id="aad61-109">Attributes</span></span>

<span data-ttu-id="aad61-110">无</span><span class="sxs-lookup"><span data-stu-id="aad61-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="aad61-111">子元素</span><span class="sxs-lookup"><span data-stu-id="aad61-111">Child Elements</span></span>

<span data-ttu-id="aad61-112">无。</span><span class="sxs-lookup"><span data-stu-id="aad61-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="aad61-113">父元素</span><span class="sxs-lookup"><span data-stu-id="aad61-113">Parent Elements</span></span>

|<span data-ttu-id="aad61-114">元素</span><span class="sxs-lookup"><span data-stu-id="aad61-114">Element</span></span>|<span data-ttu-id="aad61-115">描述</span><span class="sxs-lookup"><span data-stu-id="aad61-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aad61-116">用于配置的控件的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="aad61-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="aad61-117">定义使用此控件定义的 .NET 类型或要使用此定义时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="aad61-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="aad61-118">文本值</span><span class="sxs-lookup"><span data-stu-id="aad61-118">Text Value</span></span>

<span data-ttu-id="aad61-119">指定选择集的名称。</span><span class="sxs-lookup"><span data-stu-id="aad61-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="aad61-120">备注</span><span class="sxs-lookup"><span data-stu-id="aad61-120">Remarks</span></span>

<span data-ttu-id="aad61-121">每个控件定义都必须定义至少一个类型名称、选择集或选择条件。</span><span class="sxs-lookup"><span data-stu-id="aad61-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="aad61-122">当要定义在多个视图中使用的一组对象时，通常使用选择集。</span><span class="sxs-lookup"><span data-stu-id="aad61-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="aad61-123">有关定义选择集的详细信息，请参阅[定义选择集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="aad61-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aad61-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aad61-124">See Also</span></span>

[<span data-ttu-id="aad61-125">用于配置的控件的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="aad61-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="aad61-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="aad61-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
