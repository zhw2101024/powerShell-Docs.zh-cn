---
title: 用于视图（格式）的 CustomEntries 的 CustomEntry 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364046"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="6a277-102">CustomEntry Element for CustomEntries for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="6a277-102">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="6a277-103">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="6a277-103">Provides a definition of the control.</span></span> <span data-ttu-id="6a277-104">定义可由视图使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="6a277-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="6a277-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 元素（format） Control 元素 for View （format） CustomControl 元素的控件元素，用于控件的 View （format） CustomEntries 元素视图的 CustomControl for View （Format） CustomEntry 元素 for CustomEntries for View （Format）</span><span class="sxs-lookup"><span data-stu-id="6a277-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6a277-106">语法</span><span class="sxs-lookup"><span data-stu-id="6a277-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6a277-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="6a277-107">Attributes and Elements</span></span>

<span data-ttu-id="6a277-108">以下各节介绍了 `CustomEntry` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6a277-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6a277-109">属性</span><span class="sxs-lookup"><span data-stu-id="6a277-109">Attributes</span></span>

<span data-ttu-id="6a277-110">无。</span><span class="sxs-lookup"><span data-stu-id="6a277-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6a277-111">子元素</span><span class="sxs-lookup"><span data-stu-id="6a277-111">Child Elements</span></span>

|<span data-ttu-id="6a277-112">元素</span><span class="sxs-lookup"><span data-stu-id="6a277-112">Element</span></span>|<span data-ttu-id="6a277-113">描述</span><span class="sxs-lookup"><span data-stu-id="6a277-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a277-114">用于视图的控件的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6a277-114">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="6a277-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="6a277-115">Optional element.</span></span><br /><br /> <span data-ttu-id="6a277-116">定义使用此控件定义的 .NET 类型或要使用此定义时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="6a277-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="6a277-117">用于视图的控件的 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6a277-117">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="6a277-118">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="6a277-118">Required element.</span></span><br /><br /> <span data-ttu-id="6a277-119">定义控件显示数据的方式。</span><span class="sxs-lookup"><span data-stu-id="6a277-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6a277-120">父元素</span><span class="sxs-lookup"><span data-stu-id="6a277-120">Parent Elements</span></span>

|<span data-ttu-id="6a277-121">元素</span><span class="sxs-lookup"><span data-stu-id="6a277-121">Element</span></span>|<span data-ttu-id="6a277-122">描述</span><span class="sxs-lookup"><span data-stu-id="6a277-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a277-123">用于视图的 CustomControl 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6a277-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="6a277-124">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="6a277-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6a277-125">备注</span><span class="sxs-lookup"><span data-stu-id="6a277-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="6a277-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6a277-126">See Also</span></span>

[<span data-ttu-id="6a277-127">用于视图的 CustomControl 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6a277-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="6a277-128">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="6a277-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
