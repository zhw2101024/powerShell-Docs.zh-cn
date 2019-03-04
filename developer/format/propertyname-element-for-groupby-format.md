---
title: GroupBy （格式） 的属性名称元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddcecc46-ac75-43fa-b03a-802a68524ec3
caps.latest.revision: 10
ms.openlocfilehash: da6ac5abe7acbbee8f57b3e81529664f81800b86
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863263"
---
# <a name="propertyname-element-for-groupby-format"></a><span data-ttu-id="a8b28-102">PropertyName Element for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a8b28-102">PropertyName Element for GroupBy (Format)</span></span>

<span data-ttu-id="a8b28-103">指定其值发生更改时启动新的组的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="a8b28-103">Specifies the .NET property that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="a8b28-104">视图 （格式） 的 GroupBy （格式） 的属性名称元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="a8b28-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) PropertyName Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a8b28-105">语法</span><span class="sxs-lookup"><span data-stu-id="a8b28-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a8b28-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="a8b28-106">Attributes and Elements</span></span>

<span data-ttu-id="a8b28-107">以下各节描述了特性、 子元素和父元素的`PropertyName`元素。</span><span class="sxs-lookup"><span data-stu-id="a8b28-107">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a8b28-108">特性</span><span class="sxs-lookup"><span data-stu-id="a8b28-108">Attributes</span></span>

<span data-ttu-id="a8b28-109">无。</span><span class="sxs-lookup"><span data-stu-id="a8b28-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a8b28-110">子元素</span><span class="sxs-lookup"><span data-stu-id="a8b28-110">Child Elements</span></span>

<span data-ttu-id="a8b28-111">无。</span><span class="sxs-lookup"><span data-stu-id="a8b28-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a8b28-112">父元素</span><span class="sxs-lookup"><span data-stu-id="a8b28-112">Parent Elements</span></span>

|<span data-ttu-id="a8b28-113">元素</span><span class="sxs-lookup"><span data-stu-id="a8b28-113">Element</span></span>|<span data-ttu-id="a8b28-114">描述</span><span class="sxs-lookup"><span data-stu-id="a8b28-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a8b28-115">视图 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="a8b28-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="a8b28-116">定义一组.NET 对象的显示方式。</span><span class="sxs-lookup"><span data-stu-id="a8b28-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a8b28-117">文本值</span><span class="sxs-lookup"><span data-stu-id="a8b28-117">Text Value</span></span>

<span data-ttu-id="a8b28-118">指定.NET 属性名称。</span><span class="sxs-lookup"><span data-stu-id="a8b28-118">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="a8b28-119">备注</span><span class="sxs-lookup"><span data-stu-id="a8b28-119">Remarks</span></span>

<span data-ttu-id="a8b28-120">此属性的值发生更改时，Windows PowerShell 启动新的组。</span><span class="sxs-lookup"><span data-stu-id="a8b28-120">Windows PowerShell starts a new group whenever the value of this property changes.</span></span>

<span data-ttu-id="a8b28-121">当指定此元素时，不能指定[ScriptBlock](./scriptblock-element-for-groupby-format.md)元素，用于启动新的组。</span><span class="sxs-lookup"><span data-stu-id="a8b28-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="example"></a><span data-ttu-id="a8b28-122">示例</span><span class="sxs-lookup"><span data-stu-id="a8b28-122">Example</span></span>

<span data-ttu-id="a8b28-123">下面的示例演示如何启动新的组的属性值发生更改时。</span><span class="sxs-lookup"><span data-stu-id="a8b28-123">The following example shows how to start a new group when the value of a property changes.</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="a8b28-124">有关完整的格式设置文件，其中包含此元素的示例，请参阅[宽的视图 (GroupBy)](./wide-view-groupby.md)。</span><span class="sxs-lookup"><span data-stu-id="a8b28-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a8b28-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a8b28-125">See Also</span></span>

[<span data-ttu-id="a8b28-126">视图 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="a8b28-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="a8b28-127">GroupBy （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="a8b28-127">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="a8b28-128">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="a8b28-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
