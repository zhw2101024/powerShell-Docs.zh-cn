---
title: 配置 （格式） 的控件的 CustomEntry EntrySelectedBy 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30abae8f-c7f7-479d-ad85-19e07ddef204
caps.latest.revision: 10
ms.openlocfilehash: 81eca4f66f0057074612f2d60482b45adc36357b
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059212"
---
# <a name="entryselectedby-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="030a1-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="030a1-102">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="030a1-103">定义使用公共控件或要在使用此控件中必须存在的条件的定义的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="030a1-103">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span> <span data-ttu-id="030a1-104">定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。</span><span class="sxs-lookup"><span data-stu-id="030a1-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="030a1-105">配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素CustomControl CustomEntry 的 Controls 的配置 （格式） 的配置 （格式） EntrySelectedBy 元素的控件的格式） CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="030a1-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="030a1-106">语法</span><span class="sxs-lookup"><span data-stu-id="030a1-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="030a1-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="030a1-107">Attributes and Elements</span></span>

<span data-ttu-id="030a1-108">以下各节描述了特性、 子元素和父元素的`EntrySelectedBy`元素。</span><span class="sxs-lookup"><span data-stu-id="030a1-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="030a1-109">属性</span><span class="sxs-lookup"><span data-stu-id="030a1-109">Attributes</span></span>

<span data-ttu-id="030a1-110">无。</span><span class="sxs-lookup"><span data-stu-id="030a1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="030a1-111">子元素</span><span class="sxs-lookup"><span data-stu-id="030a1-111">Child Elements</span></span>

|<span data-ttu-id="030a1-112">元素</span><span class="sxs-lookup"><span data-stu-id="030a1-112">Element</span></span>|<span data-ttu-id="030a1-113">说明</span><span class="sxs-lookup"><span data-stu-id="030a1-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="030a1-114">配置 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="030a1-114">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="030a1-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="030a1-115">Optional element.</span></span><br /><br /> <span data-ttu-id="030a1-116">定义必须存在要使用的常见控件定义的条件。</span><span class="sxs-lookup"><span data-stu-id="030a1-116">Defines the condition that must exist for the common control definition to be used.</span></span>|
|[<span data-ttu-id="030a1-117">配置 （格式） 的控件的 EntrySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="030a1-117">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="030a1-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="030a1-118">Optional element.</span></span><br /><br /> <span data-ttu-id="030a1-119">指定一组使用公共控件的此定义的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="030a1-119">Specifies a set of .NET types that use this definition of the common control.</span></span>|
|[<span data-ttu-id="030a1-120">EntrySelectedBy 配置 （格式） 的控件的类型名称元素</span><span class="sxs-lookup"><span data-stu-id="030a1-120">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="030a1-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="030a1-121">Optional element.</span></span><br /><br /> <span data-ttu-id="030a1-122">指定将使用公共控件的此定义的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="030a1-122">Specifies a .NET type that uses this definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="030a1-123">父元素</span><span class="sxs-lookup"><span data-stu-id="030a1-123">Parent Elements</span></span>

|<span data-ttu-id="030a1-124">元素</span><span class="sxs-lookup"><span data-stu-id="030a1-124">Element</span></span>|<span data-ttu-id="030a1-125">说明</span><span class="sxs-lookup"><span data-stu-id="030a1-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="030a1-126">配置 （格式） 的控件的 CustomControl CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="030a1-126">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="030a1-127">提供了一个常用的控件的定义。</span><span class="sxs-lookup"><span data-stu-id="030a1-127">Provides a definition of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="030a1-128">备注</span><span class="sxs-lookup"><span data-stu-id="030a1-128">Remarks</span></span>

<span data-ttu-id="030a1-129">至少，每个定义必须至少一个.NET 类型、 所选内容集或指定的选择条件。</span><span class="sxs-lookup"><span data-stu-id="030a1-129">At a minimum, each definition must have at least one .NET type, selection set, or selection condition specified.</span></span> <span data-ttu-id="030a1-130">没有任何最大限制为的类型、 所选内容集或可以指定的选择条件数。</span><span class="sxs-lookup"><span data-stu-id="030a1-130">There is no maximum limit to the number of types, selection sets, or selection conditions that you can specify.</span></span>

## <a name="see-also"></a><span data-ttu-id="030a1-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="030a1-131">See Also</span></span>

[<span data-ttu-id="030a1-132">配置 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="030a1-132">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="030a1-133">配置 （格式） 的控件的 EntrySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="030a1-133">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="030a1-134">配置 （格式） 的控件的 CustomControl CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="030a1-134">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="030a1-135">EntrySelectedBy 配置 （格式） 的控件的类型名称元素</span><span class="sxs-lookup"><span data-stu-id="030a1-135">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="030a1-136">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="030a1-136">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
