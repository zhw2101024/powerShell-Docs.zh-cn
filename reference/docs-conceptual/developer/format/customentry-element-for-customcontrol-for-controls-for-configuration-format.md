---
title: 用于配置的控件（格式）的 CustomControl 的 CustomEntry 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364066"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="5cddb-102">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="5cddb-102">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="5cddb-103">提供公共控件的定义。</span><span class="sxs-lookup"><span data-stu-id="5cddb-103">Provides a definition of the common control.</span></span> <span data-ttu-id="5cddb-104">此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。</span><span class="sxs-lookup"><span data-stu-id="5cddb-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="5cddb-105">Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format）用于配置的控件的 CustomControl 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5cddb-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5cddb-106">语法</span><span class="sxs-lookup"><span data-stu-id="5cddb-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="5cddb-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="5cddb-107">Attributes and Elements</span></span>

<span data-ttu-id="5cddb-108">以下各节介绍了 `CustomEntry` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5cddb-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="5cddb-109">您必须指定由定义显示的项。</span><span class="sxs-lookup"><span data-stu-id="5cddb-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="5cddb-110">属性</span><span class="sxs-lookup"><span data-stu-id="5cddb-110">Attributes</span></span>

<span data-ttu-id="5cddb-111">无。</span><span class="sxs-lookup"><span data-stu-id="5cddb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5cddb-112">子元素</span><span class="sxs-lookup"><span data-stu-id="5cddb-112">Child Elements</span></span>

|<span data-ttu-id="5cddb-113">元素</span><span class="sxs-lookup"><span data-stu-id="5cddb-113">Element</span></span>|<span data-ttu-id="5cddb-114">描述</span><span class="sxs-lookup"><span data-stu-id="5cddb-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5cddb-115">用于配置的控件的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5cddb-115">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="5cddb-116">可选元素。</span><span class="sxs-lookup"><span data-stu-id="5cddb-116">Optional element.</span></span><br /><br /> <span data-ttu-id="5cddb-117">定义使用公共控件定义的 .NET 类型或要使用此控件必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="5cddb-117">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="5cddb-118">用于配置控件的 CustomEntry 的 CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="5cddb-118">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="5cddb-119">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="5cddb-119">Required element.</span></span><br /><br /> <span data-ttu-id="5cddb-120">定义控件显示的数据及其显示方式。</span><span class="sxs-lookup"><span data-stu-id="5cddb-120">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5cddb-121">父元素</span><span class="sxs-lookup"><span data-stu-id="5cddb-121">Parent Elements</span></span>

|<span data-ttu-id="5cddb-122">元素</span><span class="sxs-lookup"><span data-stu-id="5cddb-122">Element</span></span>|<span data-ttu-id="5cddb-123">描述</span><span class="sxs-lookup"><span data-stu-id="5cddb-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5cddb-124">用于配置的 CustomControl 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5cddb-124">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="5cddb-125">提供公共控件的定义。</span><span class="sxs-lookup"><span data-stu-id="5cddb-125">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5cddb-126">备注</span><span class="sxs-lookup"><span data-stu-id="5cddb-126">Remarks</span></span>

<span data-ttu-id="5cddb-127">在大多数情况下，每个公共自定义控件只需要一个定义，但如果您希望使用同一控件显示不同的 .NET 对象，则可以有多个定义。</span><span class="sxs-lookup"><span data-stu-id="5cddb-127">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="5cddb-128">在这些情况下，可以为每个对象或一组对象提供单独的定义。</span><span class="sxs-lookup"><span data-stu-id="5cddb-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="5cddb-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5cddb-129">See Also</span></span>

[<span data-ttu-id="5cddb-130">用于配置的 CustomControl 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5cddb-130">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="5cddb-131">用于配置控件的 CustomEntry 的 CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="5cddb-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="5cddb-132">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="5cddb-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
