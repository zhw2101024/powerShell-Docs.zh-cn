---
title: CustomEntry 元素的视图 （格式） 的 CustomControl CustomEntries |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac3c0a25-f2ca-4e28-b3dc-9cb06a76d92a
caps.latest.revision: 11
ms.openlocfilehash: 7804155bffeb1f0df8339f797bf59f8def56a3fc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066441"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="36c01-102">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="36c01-102">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="36c01-103">提供自定义控件视图的定义。</span><span class="sxs-lookup"><span data-stu-id="36c01-103">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="36c01-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl CustomEntries 视图 （格式） 的视图 （格式） CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="36c01-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="36c01-105">语法</span><span class="sxs-lookup"><span data-stu-id="36c01-105">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="36c01-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="36c01-106">Attributes and Elements</span></span>

<span data-ttu-id="36c01-107">以下各节描述了特性、 子元素和父元素的`CustomEntry`元素。</span><span class="sxs-lookup"><span data-stu-id="36c01-107">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="36c01-108">必须指定的定义显示的项。</span><span class="sxs-lookup"><span data-stu-id="36c01-108">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="36c01-109">属性</span><span class="sxs-lookup"><span data-stu-id="36c01-109">Attributes</span></span>

<span data-ttu-id="36c01-110">无。</span><span class="sxs-lookup"><span data-stu-id="36c01-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="36c01-111">子元素</span><span class="sxs-lookup"><span data-stu-id="36c01-111">Child Elements</span></span>

|<span data-ttu-id="36c01-112">元素</span><span class="sxs-lookup"><span data-stu-id="36c01-112">Element</span></span>|<span data-ttu-id="36c01-113">说明</span><span class="sxs-lookup"><span data-stu-id="36c01-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="36c01-114">视图 （格式） 的 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="36c01-114">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="36c01-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="36c01-115">Optional element.</span></span><br /><br /> <span data-ttu-id="36c01-116">定义使用的自定义控件视图或必须存在要使用此定义的条件的定义的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="36c01-116">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="36c01-117">视图 （格式） 的 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="36c01-117">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="36c01-118">定义自定义控件定义的控件。</span><span class="sxs-lookup"><span data-stu-id="36c01-118">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="36c01-119">父元素</span><span class="sxs-lookup"><span data-stu-id="36c01-119">Parent Elements</span></span>

|<span data-ttu-id="36c01-120">元素</span><span class="sxs-lookup"><span data-stu-id="36c01-120">Element</span></span>|<span data-ttu-id="36c01-121">说明</span><span class="sxs-lookup"><span data-stu-id="36c01-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="36c01-122">视图 （格式） 的 CustomControl CustomEntries 元素</span><span class="sxs-lookup"><span data-stu-id="36c01-122">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="36c01-123">提供了自定义控件视图的定义。</span><span class="sxs-lookup"><span data-stu-id="36c01-123">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="36c01-124">自定义控件视图必须指定一个或多个定义。</span><span class="sxs-lookup"><span data-stu-id="36c01-124">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="36c01-125">备注</span><span class="sxs-lookup"><span data-stu-id="36c01-125">Remarks</span></span>

<span data-ttu-id="36c01-126">在大多数情况下，只有一个定义需要为每个自定义控件视图，但可以有多个定义，如果你想要使用相同的视图以显示不同的.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="36c01-126">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="36c01-127">在这些情况下，可以为每个对象或对象集提供一个单独的定义。</span><span class="sxs-lookup"><span data-stu-id="36c01-127">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="36c01-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="36c01-128">See Also</span></span>

[<span data-ttu-id="36c01-129">视图 （格式） 的 CustomControl 元素</span><span class="sxs-lookup"><span data-stu-id="36c01-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="36c01-130">视图 （格式） 的 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="36c01-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="36c01-131">视图 （格式） 的 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="36c01-131">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="36c01-132">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="36c01-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
