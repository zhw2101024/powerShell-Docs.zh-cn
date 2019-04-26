---
title: 视图 （格式） 的 CustomControl CustomEntries 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066509"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="e6f11-102">CustomEntries Element for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="e6f11-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="e6f11-103">提供了自定义控件视图的定义。</span><span class="sxs-lookup"><span data-stu-id="e6f11-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="e6f11-104">自定义控件视图必须指定一个或多个定义。</span><span class="sxs-lookup"><span data-stu-id="e6f11-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="e6f11-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl 视图 （格式）</span><span class="sxs-lookup"><span data-stu-id="e6f11-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e6f11-106">语法</span><span class="sxs-lookup"><span data-stu-id="e6f11-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e6f11-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e6f11-107">Attributes and Elements</span></span>

<span data-ttu-id="e6f11-108">以下各节描述了特性、 子元素和父元素的`CustomControlEntries`元素。</span><span class="sxs-lookup"><span data-stu-id="e6f11-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="e6f11-109">必须指定一个或多个子元素。</span><span class="sxs-lookup"><span data-stu-id="e6f11-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e6f11-110">属性</span><span class="sxs-lookup"><span data-stu-id="e6f11-110">Attributes</span></span>

<span data-ttu-id="e6f11-111">无。</span><span class="sxs-lookup"><span data-stu-id="e6f11-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e6f11-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e6f11-112">Child Elements</span></span>

|<span data-ttu-id="e6f11-113">元素</span><span class="sxs-lookup"><span data-stu-id="e6f11-113">Element</span></span>|<span data-ttu-id="e6f11-114">说明</span><span class="sxs-lookup"><span data-stu-id="e6f11-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e6f11-115">视图 （格式） 的 CustomEntries CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="e6f11-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="e6f11-116">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="e6f11-116">Required element.</span></span><br /><br /> <span data-ttu-id="e6f11-117">提供自定义控件视图的定义。</span><span class="sxs-lookup"><span data-stu-id="e6f11-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e6f11-118">父元素</span><span class="sxs-lookup"><span data-stu-id="e6f11-118">Parent Elements</span></span>

|<span data-ttu-id="e6f11-119">元素</span><span class="sxs-lookup"><span data-stu-id="e6f11-119">Element</span></span>|<span data-ttu-id="e6f11-120">说明</span><span class="sxs-lookup"><span data-stu-id="e6f11-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e6f11-121">视图 （格式） 的 CustomControl 元素</span><span class="sxs-lookup"><span data-stu-id="e6f11-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="e6f11-122">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="e6f11-122">Required element.</span></span><br /><br /> <span data-ttu-id="e6f11-123">定义自定义控件的视图格式。</span><span class="sxs-lookup"><span data-stu-id="e6f11-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e6f11-124">备注</span><span class="sxs-lookup"><span data-stu-id="e6f11-124">Remarks</span></span>

<span data-ttu-id="e6f11-125">在大多数情况下，控件具有只有一个定义，在单个定义`CustomEntry`元素。</span><span class="sxs-lookup"><span data-stu-id="e6f11-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="e6f11-126">但是很可能有多个定义，如果你想要使用相同的控件来显示不同的.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="e6f11-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="e6f11-127">在这些情况下，你可以定义`CustomEntry`元素为每个对象或对象集。</span><span class="sxs-lookup"><span data-stu-id="e6f11-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6f11-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e6f11-128">See Also</span></span>

[<span data-ttu-id="e6f11-129">视图 （格式） 的 CustomControl 元素</span><span class="sxs-lookup"><span data-stu-id="e6f11-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="e6f11-130">视图 （格式） 的 CustomEntries CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="e6f11-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e6f11-131">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="e6f11-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
