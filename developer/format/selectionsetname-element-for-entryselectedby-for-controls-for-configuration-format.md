---
title: 配置 （格式） 的控件的 EntrySelectedBy SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42143d1e-7cda-4c4a-b568-fa1951bb9417
caps.latest.revision: 6
ms.openlocfilehash: 9060ee54d6f88c7f910b16cf5c9b87f37844b736
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860903"
---
# <a name="selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="1d26f-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="1d26f-102">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="1d26f-103">指定一组使用控件的此定义的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="1d26f-103">Specifies a set of .NET types that use this definition of the control.</span></span> <span data-ttu-id="1d26f-104">定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。</span><span class="sxs-lookup"><span data-stu-id="1d26f-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="1d26f-105">配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素CustomControl CustomEntry EntrySelectedBy 的 Controls 的配置 （格式） 的配置 （格式） SelectionSetName 元素的控件的配置 （格式） EntrySelectedBy 元素的控件的格式） CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="1d26f-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1d26f-106">语法</span><span class="sxs-lookup"><span data-stu-id="1d26f-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="1d26f-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="1d26f-107">Attributes and Elements</span></span>

<span data-ttu-id="1d26f-108">以下各节描述了特性、 子元素和父元素的`SelectionSetName`元素。</span><span class="sxs-lookup"><span data-stu-id="1d26f-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1d26f-109">特性</span><span class="sxs-lookup"><span data-stu-id="1d26f-109">Attributes</span></span>

<span data-ttu-id="1d26f-110">无</span><span class="sxs-lookup"><span data-stu-id="1d26f-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="1d26f-111">子元素</span><span class="sxs-lookup"><span data-stu-id="1d26f-111">Child Elements</span></span>

<span data-ttu-id="1d26f-112">无。</span><span class="sxs-lookup"><span data-stu-id="1d26f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1d26f-113">父元素</span><span class="sxs-lookup"><span data-stu-id="1d26f-113">Parent Elements</span></span>

|<span data-ttu-id="1d26f-114">元素</span><span class="sxs-lookup"><span data-stu-id="1d26f-114">Element</span></span>|<span data-ttu-id="1d26f-115">描述</span><span class="sxs-lookup"><span data-stu-id="1d26f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1d26f-116">配置 （格式） 的控件的 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="1d26f-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="1d26f-117">定义使用此控件定义或要使用此定义中必须存在的条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="1d26f-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1d26f-118">文本值</span><span class="sxs-lookup"><span data-stu-id="1d26f-118">Text Value</span></span>

<span data-ttu-id="1d26f-119">指定所选内容集的名称。</span><span class="sxs-lookup"><span data-stu-id="1d26f-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="1d26f-120">备注</span><span class="sxs-lookup"><span data-stu-id="1d26f-120">Remarks</span></span>

<span data-ttu-id="1d26f-121">每个控件定义必须至少一个类型名称、 选择集或定义的选择条件。</span><span class="sxs-lookup"><span data-stu-id="1d26f-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="1d26f-122">当你想要在多个视图中定义的一组使用的对象时通常使用的选项集。</span><span class="sxs-lookup"><span data-stu-id="1d26f-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="1d26f-123">有关定义的选项集的详细信息，请参阅[定义所选内容设置](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="1d26f-123">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d26f-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d26f-124">See Also</span></span>

[<span data-ttu-id="1d26f-125">配置 （格式） 的控件的 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="1d26f-125">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="1d26f-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="1d26f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
