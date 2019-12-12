---
title: 用于配置的控件（格式）的 CustomEntry 的 EntrySelectedBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368766"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="cbb21-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="cbb21-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="cbb21-103">定义使用公共控件定义的 .NET 类型或要使用此控件必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="cbb21-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="cbb21-104">此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。</span><span class="sxs-lookup"><span data-stu-id="cbb21-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="cbb21-105">Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format） CustomEntry 元素 for CustomControl for EntrySelectedBy 元素 for 元素 for CustomEntry for control for control （Format）</span><span class="sxs-lookup"><span data-stu-id="cbb21-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cbb21-106">语法</span><span class="sxs-lookup"><span data-stu-id="cbb21-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cbb21-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="cbb21-107">Attributes and Elements</span></span>

<span data-ttu-id="cbb21-108">以下各节介绍了 `EntrySelectedBy` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cbb21-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cbb21-109">属性</span><span class="sxs-lookup"><span data-stu-id="cbb21-109">Attributes</span></span>

<span data-ttu-id="cbb21-110">无。</span><span class="sxs-lookup"><span data-stu-id="cbb21-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cbb21-111">子元素</span><span class="sxs-lookup"><span data-stu-id="cbb21-111">Child Elements</span></span>

|<span data-ttu-id="cbb21-112">元素</span><span class="sxs-lookup"><span data-stu-id="cbb21-112">Element</span></span>|<span data-ttu-id="cbb21-113">描述</span><span class="sxs-lookup"><span data-stu-id="cbb21-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cbb21-114">用于配置的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cbb21-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="cbb21-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="cbb21-115">Optional element.</span></span><br /><br /> <span data-ttu-id="cbb21-116">定义要使用的公共控件定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="cbb21-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="cbb21-117">用于配置的控件的 EntrySelectedBy 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cbb21-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="cbb21-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="cbb21-118">Optional element.</span></span><br /><br /> <span data-ttu-id="cbb21-119">指定一组使用此公共控件定义的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="cbb21-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="cbb21-120">用于配置的控件的 EntrySelectedBy 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cbb21-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="cbb21-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="cbb21-121">Optional element.</span></span><br /><br /> <span data-ttu-id="cbb21-122">指定使用此公共控件定义的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="cbb21-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cbb21-123">父元素</span><span class="sxs-lookup"><span data-stu-id="cbb21-123">Parent Elements</span></span>

|<span data-ttu-id="cbb21-124">元素</span><span class="sxs-lookup"><span data-stu-id="cbb21-124">Element</span></span>|<span data-ttu-id="cbb21-125">描述</span><span class="sxs-lookup"><span data-stu-id="cbb21-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cbb21-126">用于配置的控件的 CustomControl 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cbb21-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="cbb21-127">提供公共控件的定义。</span><span class="sxs-lookup"><span data-stu-id="cbb21-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cbb21-128">备注</span><span class="sxs-lookup"><span data-stu-id="cbb21-128">Remarks</span></span>

<span data-ttu-id="cbb21-129">每个定义至少必须指定一个 .NET 类型、选择集或选择条件。</span><span class="sxs-lookup"><span data-stu-id="cbb21-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="cbb21-130">对于可以指定的类型、选择集或选择条件的数量没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="cbb21-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="cbb21-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cbb21-131">See Also</span></span>

[<span data-ttu-id="cbb21-132">用于配置的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cbb21-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="cbb21-133">用于配置的控件的 EntrySelectedBy 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cbb21-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="cbb21-134">用于配置的控件的 CustomControl 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cbb21-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="cbb21-135">用于配置的控件的 EntrySelectedBy 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="cbb21-135">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="cbb21-136">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="cbb21-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
