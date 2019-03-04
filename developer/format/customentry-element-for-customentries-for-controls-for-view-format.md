---
title: 视图 （格式） 的控件的 CustomEntries CustomEntry 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858773"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="c0d57-102">CustomEntry Element for CustomEntries for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="c0d57-102">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="c0d57-103">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="c0d57-103">Provides a definition of the control.</span></span> <span data-ttu-id="c0d57-104">定义一个视图，可以使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="c0d57-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="c0d57-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl CustomEntries 视图 （格式） 的控件的视图 （格式） CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="c0d57-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c0d57-106">语法</span><span class="sxs-lookup"><span data-stu-id="c0d57-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c0d57-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="c0d57-107">Attributes and Elements</span></span>

<span data-ttu-id="c0d57-108">以下各节描述了特性、 子元素和父元素的`CustomEntry`元素。</span><span class="sxs-lookup"><span data-stu-id="c0d57-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c0d57-109">属性</span><span class="sxs-lookup"><span data-stu-id="c0d57-109">Attributes</span></span>

<span data-ttu-id="c0d57-110">无。</span><span class="sxs-lookup"><span data-stu-id="c0d57-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c0d57-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c0d57-111">Child Elements</span></span>

|<span data-ttu-id="c0d57-112">元素</span><span class="sxs-lookup"><span data-stu-id="c0d57-112">Element</span></span>|<span data-ttu-id="c0d57-113">说明</span><span class="sxs-lookup"><span data-stu-id="c0d57-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0d57-114">视图 （格式） 的控件的 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="c0d57-114">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="c0d57-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="c0d57-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c0d57-116">定义使用此控件定义或要使用此定义中必须存在的条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="c0d57-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="c0d57-117">视图 （格式） 的控件的 CustomEntry CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="c0d57-117">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="c0d57-118">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="c0d57-118">Required element.</span></span><br /><br /> <span data-ttu-id="c0d57-119">定义该控件显示数据的方式。</span><span class="sxs-lookup"><span data-stu-id="c0d57-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c0d57-120">父元素</span><span class="sxs-lookup"><span data-stu-id="c0d57-120">Parent Elements</span></span>

|<span data-ttu-id="c0d57-121">元素</span><span class="sxs-lookup"><span data-stu-id="c0d57-121">Element</span></span>|<span data-ttu-id="c0d57-122">说明</span><span class="sxs-lookup"><span data-stu-id="c0d57-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0d57-123">视图 （格式） 的 CustomControl CustomEntries 元素</span><span class="sxs-lookup"><span data-stu-id="c0d57-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="c0d57-124">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="c0d57-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c0d57-125">备注</span><span class="sxs-lookup"><span data-stu-id="c0d57-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="c0d57-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c0d57-126">See Also</span></span>

[<span data-ttu-id="c0d57-127">视图 （格式） 的 CustomControl CustomEntries 元素</span><span class="sxs-lookup"><span data-stu-id="c0d57-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c0d57-128">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="c0d57-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
