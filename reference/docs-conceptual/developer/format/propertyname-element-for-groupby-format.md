---
title: GroupBy 的 PropertyName 元素（Format） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362516"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="fe568-102">PropertyName Element for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="fe568-102">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="fe568-103">指定在新组的值发生更改时启动新组的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="fe568-103">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="fe568-104">对于 GroupBy （Format）的 View （Format） PropertyName 元素，Configuration 元素（Format） ViewDefinitions 元素（format） GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="fe568-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fe568-105">语法</span><span class="sxs-lookup"><span data-stu-id="fe568-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fe568-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="fe568-106">Attributes and Elements</span></span>

<span data-ttu-id="fe568-107">以下各节介绍了 `PropertyName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fe568-107">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fe568-108">属性</span><span class="sxs-lookup"><span data-stu-id="fe568-108">Attributes</span></span>

<span data-ttu-id="fe568-109">无。</span><span class="sxs-lookup"><span data-stu-id="fe568-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fe568-110">子元素</span><span class="sxs-lookup"><span data-stu-id="fe568-110">Child Elements</span></span>

<span data-ttu-id="fe568-111">无。</span><span class="sxs-lookup"><span data-stu-id="fe568-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fe568-112">父元素</span><span class="sxs-lookup"><span data-stu-id="fe568-112">Parent Elements</span></span>

|<span data-ttu-id="fe568-113">元素</span><span class="sxs-lookup"><span data-stu-id="fe568-113">Element</span></span>|<span data-ttu-id="fe568-114">描述</span><span class="sxs-lookup"><span data-stu-id="fe568-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fe568-115">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fe568-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="fe568-116">定义一组 .NET 对象的显示方式。</span><span class="sxs-lookup"><span data-stu-id="fe568-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fe568-117">文本值</span><span class="sxs-lookup"><span data-stu-id="fe568-117">Text Value</span></span>

<span data-ttu-id="fe568-118">指定 .NET 属性名称。</span><span class="sxs-lookup"><span data-stu-id="fe568-118">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="fe568-119">备注</span><span class="sxs-lookup"><span data-stu-id="fe568-119">Remarks</span></span>

<span data-ttu-id="fe568-120">每当此属性的值发生更改时，Windows PowerShell 就会启动一个新组。</span><span class="sxs-lookup"><span data-stu-id="fe568-120">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="fe568-121">如果指定此元素，则不能指定[ScriptBlock](./scriptblock-element-for-groupby-format.md)元素来启动新组。</span><span class="sxs-lookup"><span data-stu-id="fe568-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="fe568-122">示例</span><span class="sxs-lookup"><span data-stu-id="fe568-122">Example</span></span>

<span data-ttu-id="fe568-123">下面的示例演示如何在属性的值更改时启动新组。</span><span class="sxs-lookup"><span data-stu-id="fe568-123">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="fe568-124">有关包括此元素的完整格式化文件的示例，请参阅[宽视图（GroupBy）](./wide-view-groupby.md)。</span><span class="sxs-lookup"><span data-stu-id="fe568-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fe568-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fe568-125">See Also</span></span>

[<span data-ttu-id="fe568-126">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fe568-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="fe568-127">GroupBy 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fe568-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="fe568-128">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="fe568-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
