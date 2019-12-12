---
title: 用于视图的 CustomControl 的 CustomEntries 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364076"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="4b947-102">CustomEntries Element for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="4b947-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="4b947-103">提供自定义控件视图的定义。</span><span class="sxs-lookup"><span data-stu-id="4b947-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="4b947-104">自定义控件视图必须指定一个或多个定义。</span><span class="sxs-lookup"><span data-stu-id="4b947-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="4b947-105">CustomControl for View 的 Configuration 元素（格式） ViewDefinitions 元素（format） CustomControl 元素（format） CustomEntries 元素（format）</span><span class="sxs-lookup"><span data-stu-id="4b947-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4b947-106">语法</span><span class="sxs-lookup"><span data-stu-id="4b947-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4b947-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="4b947-107">Attributes and Elements</span></span>

<span data-ttu-id="4b947-108">以下各节介绍了 `CustomControlEntries` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4b947-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="4b947-109">您必须指定一个或多个子元素。</span><span class="sxs-lookup"><span data-stu-id="4b947-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4b947-110">属性</span><span class="sxs-lookup"><span data-stu-id="4b947-110">Attributes</span></span>

<span data-ttu-id="4b947-111">无。</span><span class="sxs-lookup"><span data-stu-id="4b947-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4b947-112">子元素</span><span class="sxs-lookup"><span data-stu-id="4b947-112">Child Elements</span></span>

|<span data-ttu-id="4b947-113">元素</span><span class="sxs-lookup"><span data-stu-id="4b947-113">Element</span></span>|<span data-ttu-id="4b947-114">描述</span><span class="sxs-lookup"><span data-stu-id="4b947-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4b947-115">用于视图的 CustomEntries 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4b947-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="4b947-116">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="4b947-116">Required element.</span></span><br /><br /> <span data-ttu-id="4b947-117">提供自定义控件视图的定义。</span><span class="sxs-lookup"><span data-stu-id="4b947-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4b947-118">父元素</span><span class="sxs-lookup"><span data-stu-id="4b947-118">Parent Elements</span></span>

|<span data-ttu-id="4b947-119">元素</span><span class="sxs-lookup"><span data-stu-id="4b947-119">Element</span></span>|<span data-ttu-id="4b947-120">描述</span><span class="sxs-lookup"><span data-stu-id="4b947-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4b947-121">View 的 CustomControl 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="4b947-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="4b947-122">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="4b947-122">Required element.</span></span><br /><br /> <span data-ttu-id="4b947-123">定义视图的自定义控件格式。</span><span class="sxs-lookup"><span data-stu-id="4b947-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4b947-124">备注</span><span class="sxs-lookup"><span data-stu-id="4b947-124">Remarks</span></span>

<span data-ttu-id="4b947-125">在大多数情况下，控件只有一个定义，该定义在单个 `CustomEntry` 元素中定义。</span><span class="sxs-lookup"><span data-stu-id="4b947-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="4b947-126">但是，如果希望使用同一控件显示不同的 .NET 对象，则可以有多个定义。</span><span class="sxs-lookup"><span data-stu-id="4b947-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="4b947-127">在这些情况下，可以为每个对象或一组对象定义 `CustomEntry` 元素。</span><span class="sxs-lookup"><span data-stu-id="4b947-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b947-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4b947-128">See Also</span></span>

[<span data-ttu-id="4b947-129">View 的 CustomControl 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="4b947-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="4b947-130">用于视图的 CustomEntries 的 CustomEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4b947-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4b947-131">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="4b947-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
