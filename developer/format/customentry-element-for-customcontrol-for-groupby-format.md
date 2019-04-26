---
title: GroupBy （格式） 的 CustomControl CustomEntry 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066465"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="e8a4d-102">CustomEntry Element for CustomControl for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="e8a4d-102">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="e8a4d-103">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-103">Provides a definition of the control.</span></span> <span data-ttu-id="e8a4d-104">定义如何显示一组新对象时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="e8a4d-105">GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素GroupBy （格式） 的 CustomControl</span><span class="sxs-lookup"><span data-stu-id="e8a4d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e8a4d-106">语法</span><span class="sxs-lookup"><span data-stu-id="e8a4d-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e8a4d-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e8a4d-107">Attributes and Elements</span></span>

<span data-ttu-id="e8a4d-108">以下各节描述了特性、 子元素和父元素的`CustomEntry`元素。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e8a4d-109">属性</span><span class="sxs-lookup"><span data-stu-id="e8a4d-109">Attributes</span></span>

<span data-ttu-id="e8a4d-110">无。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e8a4d-111">子元素</span><span class="sxs-lookup"><span data-stu-id="e8a4d-111">Child Elements</span></span>

|<span data-ttu-id="e8a4d-112">元素</span><span class="sxs-lookup"><span data-stu-id="e8a4d-112">Element</span></span>|<span data-ttu-id="e8a4d-113">说明</span><span class="sxs-lookup"><span data-stu-id="e8a4d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e8a4d-114">GroupBy （格式） 的 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="e8a4d-114">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="e8a4d-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e8a4d-116">定义使用此控件定义或要使用此定义中必须存在的条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="e8a4d-117">GroupBy （格式） 的 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="e8a4d-117">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="e8a4d-118">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-118">Required element.</span></span><br /><br /> <span data-ttu-id="e8a4d-119">定义该控件显示数据的方式。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e8a4d-120">父元素</span><span class="sxs-lookup"><span data-stu-id="e8a4d-120">Parent Elements</span></span>

|<span data-ttu-id="e8a4d-121">元素</span><span class="sxs-lookup"><span data-stu-id="e8a4d-121">Element</span></span>|<span data-ttu-id="e8a4d-122">说明</span><span class="sxs-lookup"><span data-stu-id="e8a4d-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e8a4d-123">GroupBy （格式） 的 CustomControl CustomEntries 元素</span><span class="sxs-lookup"><span data-stu-id="e8a4d-123">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="e8a4d-124">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e8a4d-125">备注</span><span class="sxs-lookup"><span data-stu-id="e8a4d-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="e8a4d-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e8a4d-126">See Also</span></span>

[<span data-ttu-id="e8a4d-127">GroupBy （格式） 的 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="e8a4d-127">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="e8a4d-128">GroupBy （格式） 的 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="e8a4d-128">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="e8a4d-129">GroupBy （格式） 的 CustomControl CustomEntries 元素</span><span class="sxs-lookup"><span data-stu-id="e8a4d-129">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="e8a4d-130">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="e8a4d-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
