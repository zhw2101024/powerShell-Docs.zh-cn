---
title: 用于配置的控件（格式）的 CustomControl 的 CustomEntries 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368816"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="68548-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="68548-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="68548-103">提供公共控件的定义。</span><span class="sxs-lookup"><span data-stu-id="68548-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="68548-104">此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。</span><span class="sxs-lookup"><span data-stu-id="68548-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="68548-105">Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（形式</span><span class="sxs-lookup"><span data-stu-id="68548-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="68548-106">语法</span><span class="sxs-lookup"><span data-stu-id="68548-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="68548-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="68548-107">Attributes and Elements</span></span>

<span data-ttu-id="68548-108">以下各节介绍了 `CustomEntries` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="68548-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="68548-109">您必须指定一个或多个子元素。</span><span class="sxs-lookup"><span data-stu-id="68548-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="68548-110">属性</span><span class="sxs-lookup"><span data-stu-id="68548-110">Attributes</span></span>

<span data-ttu-id="68548-111">无。</span><span class="sxs-lookup"><span data-stu-id="68548-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="68548-112">子元素</span><span class="sxs-lookup"><span data-stu-id="68548-112">Child Elements</span></span>

|<span data-ttu-id="68548-113">元素</span><span class="sxs-lookup"><span data-stu-id="68548-113">Element</span></span>|<span data-ttu-id="68548-114">描述</span><span class="sxs-lookup"><span data-stu-id="68548-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="68548-115">用于配置的控件的 CustomControl 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="68548-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="68548-116">提供公共控件的定义。</span><span class="sxs-lookup"><span data-stu-id="68548-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="68548-117">父元素</span><span class="sxs-lookup"><span data-stu-id="68548-117">Parent Elements</span></span>

|<span data-ttu-id="68548-118">元素</span><span class="sxs-lookup"><span data-stu-id="68548-118">Element</span></span>|<span data-ttu-id="68548-119">描述</span><span class="sxs-lookup"><span data-stu-id="68548-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="68548-120">用于控件配置的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="68548-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="68548-121">定义公共控件。</span><span class="sxs-lookup"><span data-stu-id="68548-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="68548-122">备注</span><span class="sxs-lookup"><span data-stu-id="68548-122">Remarks</span></span>

<span data-ttu-id="68548-123">在大多数情况下，控件只有一个定义，该定义在单个 @no__t 0 元素中定义。</span><span class="sxs-lookup"><span data-stu-id="68548-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="68548-124">但是，如果希望使用同一控件显示不同的 .NET 对象，则可以有多个定义。</span><span class="sxs-lookup"><span data-stu-id="68548-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="68548-125">在这些情况下，可以为每个对象或一组对象定义 `CustomEntry` 元素。</span><span class="sxs-lookup"><span data-stu-id="68548-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="68548-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="68548-126">See Also</span></span>

[<span data-ttu-id="68548-127">用于控件配置的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="68548-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="68548-128">用于配置的控件的 CustomControl 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="68548-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="68548-129">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="68548-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
