---
title: 配置 （格式） 的控件的 CustomControl CustomEntry 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066458"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="3d0c1-102">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="3d0c1-102">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="3d0c1-103">提供了一个常用的控件的定义。</span><span class="sxs-lookup"><span data-stu-id="3d0c1-103">Provides a definition of the common control.</span></span> <span data-ttu-id="3d0c1-104">定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。</span><span class="sxs-lookup"><span data-stu-id="3d0c1-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="3d0c1-105">配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素CustomControl 配置 （格式） 的控件的格式） CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="3d0c1-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3d0c1-106">语法</span><span class="sxs-lookup"><span data-stu-id="3d0c1-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="3d0c1-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="3d0c1-107">Attributes and Elements</span></span>

<span data-ttu-id="3d0c1-108">以下各节描述了特性、 子元素和父元素的`CustomEntry`元素。</span><span class="sxs-lookup"><span data-stu-id="3d0c1-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="3d0c1-109">必须指定的定义显示的项。</span><span class="sxs-lookup"><span data-stu-id="3d0c1-109">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="3d0c1-110">属性</span><span class="sxs-lookup"><span data-stu-id="3d0c1-110">Attributes</span></span>

<span data-ttu-id="3d0c1-111">无。</span><span class="sxs-lookup"><span data-stu-id="3d0c1-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3d0c1-112">子元素</span><span class="sxs-lookup"><span data-stu-id="3d0c1-112">Child Elements</span></span>

|<span data-ttu-id="3d0c1-113">元素</span><span class="sxs-lookup"><span data-stu-id="3d0c1-113">Element</span></span>|<span data-ttu-id="3d0c1-114">说明</span><span class="sxs-lookup"><span data-stu-id="3d0c1-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3d0c1-115">配置 （格式） 的控件的 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="3d0c1-115">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="3d0c1-116">可选元素。</span><span class="sxs-lookup"><span data-stu-id="3d0c1-116">Optional element.</span></span><br /><br /> <span data-ttu-id="3d0c1-117">定义使用公共控件或要在使用此控件中必须存在的条件的定义的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="3d0c1-117">Defines the .NET types that use the definition of the common control or the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="3d0c1-118">有关配置控件 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="3d0c1-118">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="3d0c1-119">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="3d0c1-119">Required element.</span></span><br /><br /> <span data-ttu-id="3d0c1-120">定义由控件显示的数据和显示方式。</span><span class="sxs-lookup"><span data-stu-id="3d0c1-120">Defines what data is displayed by the control and how it is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3d0c1-121">父元素</span><span class="sxs-lookup"><span data-stu-id="3d0c1-121">Parent Elements</span></span>

|<span data-ttu-id="3d0c1-122">元素</span><span class="sxs-lookup"><span data-stu-id="3d0c1-122">Element</span></span>|<span data-ttu-id="3d0c1-123">说明</span><span class="sxs-lookup"><span data-stu-id="3d0c1-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3d0c1-124">配置 （格式） 的 CustomControl CustomEntries 元素</span><span class="sxs-lookup"><span data-stu-id="3d0c1-124">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="3d0c1-125">提供了一个常用的控件的定义。</span><span class="sxs-lookup"><span data-stu-id="3d0c1-125">Provides the definitions of the common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3d0c1-126">备注</span><span class="sxs-lookup"><span data-stu-id="3d0c1-126">Remarks</span></span>

<span data-ttu-id="3d0c1-127">在大多数情况下，只有一个定义需要为每个常见的自定义控件，但可以有多个定义，如果你想要使用相同的控件来显示不同的.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="3d0c1-127">In most cases, only one definition is required for each common custom control, but it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="3d0c1-128">在这些情况下，可以为每个对象或对象集提供一个单独的定义。</span><span class="sxs-lookup"><span data-stu-id="3d0c1-128">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d0c1-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3d0c1-129">See Also</span></span>

[<span data-ttu-id="3d0c1-130">配置 （格式） 的 CustomControl CustomEntries 元素</span><span class="sxs-lookup"><span data-stu-id="3d0c1-130">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="3d0c1-131">有关配置控件 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="3d0c1-131">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="3d0c1-132">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="3d0c1-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
