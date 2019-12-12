---
title: GroupBy （格式）的 CustomControl 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2472e256-8f4f-4288-8b67-a3300649dafa
caps.latest.revision: 9
ms.openlocfilehash: 2e84e770a345e272d4c5917b00afe7520840e1db
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368956"
---
# <a name="customcontrol-element-for-groupby-format"></a><span data-ttu-id="5481f-102">CustomControl Element for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5481f-102">CustomControl Element for GroupBy (Format)</span></span>

<span data-ttu-id="5481f-103">定义显示新组的自定义控件。</span><span class="sxs-lookup"><span data-stu-id="5481f-103">Defines the custom control that displays the new group.</span></span>

<span data-ttu-id="5481f-104">GroupBy （format）的 View （format） CustomControl 元素的 ViewDefinitions 元素（format） View 元素（format） GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="5481f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5481f-105">语法</span><span class="sxs-lookup"><span data-stu-id="5481f-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
<CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5481f-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="5481f-106">Attributes and Elements</span></span>

<span data-ttu-id="5481f-107">以下各节介绍 `CustomControl` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5481f-107">The following sections describe the attributes, child elements, and parent element of the `CustomControl` element.</span></span> <span data-ttu-id="5481f-108">可以指定任意数量的子元素，并以任意顺序列出它们。</span><span class="sxs-lookup"><span data-stu-id="5481f-108">You can specify any number of child elements and list them in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="5481f-109">属性</span><span class="sxs-lookup"><span data-stu-id="5481f-109">Attributes</span></span>

<span data-ttu-id="5481f-110">无。</span><span class="sxs-lookup"><span data-stu-id="5481f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5481f-111">子元素</span><span class="sxs-lookup"><span data-stu-id="5481f-111">Child Elements</span></span>

|<span data-ttu-id="5481f-112">元素</span><span class="sxs-lookup"><span data-stu-id="5481f-112">Element</span></span>|<span data-ttu-id="5481f-113">描述</span><span class="sxs-lookup"><span data-stu-id="5481f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5481f-114">GroupBy 的 CustomControl 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5481f-114">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="5481f-115">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="5481f-115">Required element.</span></span><br /><br /> <span data-ttu-id="5481f-116">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="5481f-116">Provides the definitions for the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5481f-117">父元素</span><span class="sxs-lookup"><span data-stu-id="5481f-117">Parent Elements</span></span>

|<span data-ttu-id="5481f-118">元素</span><span class="sxs-lookup"><span data-stu-id="5481f-118">Element</span></span>|<span data-ttu-id="5481f-119">描述</span><span class="sxs-lookup"><span data-stu-id="5481f-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5481f-120">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5481f-120">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="5481f-121">定义 Windows PowerShell 如何显示一组新的对象。</span><span class="sxs-lookup"><span data-stu-id="5481f-121">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5481f-122">备注</span><span class="sxs-lookup"><span data-stu-id="5481f-122">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="5481f-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5481f-123">See Also</span></span>

[<span data-ttu-id="5481f-124">GroupBy 的 CustomControl 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5481f-124">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="5481f-125">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5481f-125">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="5481f-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="5481f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
