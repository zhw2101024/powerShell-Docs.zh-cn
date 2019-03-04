---
title: 视图 （格式） 的控件的 CustomControl CustomEntries 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861803"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a><span data-ttu-id="c1243-102">CustomEntries Element for CustomControl for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="c1243-102">CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

<span data-ttu-id="c1243-103">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="c1243-103">Provides the definitions for the control.</span></span> <span data-ttu-id="c1243-104">定义一个视图，可以使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="c1243-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="c1243-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl 的 Controls 的视图 （格式）</span><span class="sxs-lookup"><span data-stu-id="c1243-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c1243-106">语法</span><span class="sxs-lookup"><span data-stu-id="c1243-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c1243-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="c1243-107">Attributes and Elements</span></span>

<span data-ttu-id="c1243-108">以下各节描述了特性、 子元素和父元素的`CustomEntries`元素。</span><span class="sxs-lookup"><span data-stu-id="c1243-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="c1243-109">可以指定的子元素的数目没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="c1243-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="c1243-110">特性</span><span class="sxs-lookup"><span data-stu-id="c1243-110">Attributes</span></span>

<span data-ttu-id="c1243-111">无。</span><span class="sxs-lookup"><span data-stu-id="c1243-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c1243-112">子元素</span><span class="sxs-lookup"><span data-stu-id="c1243-112">Child Elements</span></span>

|<span data-ttu-id="c1243-113">元素</span><span class="sxs-lookup"><span data-stu-id="c1243-113">Element</span></span>|<span data-ttu-id="c1243-114">描述</span><span class="sxs-lookup"><span data-stu-id="c1243-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1243-115">视图 （格式） 的控件的 CustomEntries CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="c1243-115">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="c1243-116">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="c1243-116">Required element.</span></span><br /><br /> <span data-ttu-id="c1243-117">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="c1243-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c1243-118">父元素</span><span class="sxs-lookup"><span data-stu-id="c1243-118">Parent Elements</span></span>

|<span data-ttu-id="c1243-119">元素</span><span class="sxs-lookup"><span data-stu-id="c1243-119">Element</span></span>|<span data-ttu-id="c1243-120">描述</span><span class="sxs-lookup"><span data-stu-id="c1243-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c1243-121">控件的视图 （格式） 的控件的 CustomControl 元素</span><span class="sxs-lookup"><span data-stu-id="c1243-121">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="c1243-122">定义视图所使用的控件。</span><span class="sxs-lookup"><span data-stu-id="c1243-122">Defines the control used by the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c1243-123">备注</span><span class="sxs-lookup"><span data-stu-id="c1243-123">Remarks</span></span>

<span data-ttu-id="c1243-124">在大多数情况下，控件具有只有一个定义，指定在单个`CustomEntry`元素。</span><span class="sxs-lookup"><span data-stu-id="c1243-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="c1243-125">但是，就可以提供多个定义，如果你想要使用相同的控件来显示不同的.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="c1243-125">However, it is possible to provide multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="c1243-126">在这些情况下，你可以定义`CustomEntry`元素为每个对象或对象集。</span><span class="sxs-lookup"><span data-stu-id="c1243-126">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1243-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c1243-127">See Also</span></span>

[<span data-ttu-id="c1243-128">视图 （格式） 的控件的 CustomEntries CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="c1243-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="c1243-129">控件的视图 （格式） 的控件的 CustomControl 元素</span><span class="sxs-lookup"><span data-stu-id="c1243-129">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="c1243-130">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="c1243-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
