---
title: 视图 （格式） 的 CustomControl 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2edac16c-0b30-4985-ac84-0821aa9a9f6d
caps.latest.revision: 12
ms.openlocfilehash: bd0f7ca4de8dede97d1553cd62884ea45876e0c7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861253"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="e7aab-102">CustomControl Element for View (Format)</span><span class="sxs-lookup"><span data-stu-id="e7aab-102">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="e7aab-103">定义自定义控件的视图格式。</span><span class="sxs-lookup"><span data-stu-id="e7aab-103">Defines a custom control format for the view.</span></span>

<span data-ttu-id="e7aab-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="e7aab-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e7aab-105">语法</span><span class="sxs-lookup"><span data-stu-id="e7aab-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e7aab-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="e7aab-106">Attributes and Elements</span></span>

<span data-ttu-id="e7aab-107">以下各节描述了特性、 子元素和父元素的`CustomControl`元素。</span><span class="sxs-lookup"><span data-stu-id="e7aab-107">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="e7aab-108">必须指定一个子元素。</span><span class="sxs-lookup"><span data-stu-id="e7aab-108">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e7aab-109">特性</span><span class="sxs-lookup"><span data-stu-id="e7aab-109">Attributes</span></span>

<span data-ttu-id="e7aab-110">无。</span><span class="sxs-lookup"><span data-stu-id="e7aab-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e7aab-111">子元素</span><span class="sxs-lookup"><span data-stu-id="e7aab-111">Child Elements</span></span>

|<span data-ttu-id="e7aab-112">元素</span><span class="sxs-lookup"><span data-stu-id="e7aab-112">Element</span></span>|<span data-ttu-id="e7aab-113">描述</span><span class="sxs-lookup"><span data-stu-id="e7aab-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e7aab-114">视图 （格式） 的 CustomControl CustomEntries 元素</span><span class="sxs-lookup"><span data-stu-id="e7aab-114">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="e7aab-115">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="e7aab-115">Required element.</span></span><br /><br /> <span data-ttu-id="e7aab-116">提供了自定义控件视图的定义。</span><span class="sxs-lookup"><span data-stu-id="e7aab-116">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e7aab-117">父元素</span><span class="sxs-lookup"><span data-stu-id="e7aab-117">Parent Elements</span></span>

|<span data-ttu-id="e7aab-118">元素</span><span class="sxs-lookup"><span data-stu-id="e7aab-118">Element</span></span>|<span data-ttu-id="e7aab-119">描述</span><span class="sxs-lookup"><span data-stu-id="e7aab-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e7aab-120">视图元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="e7aab-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="e7aab-121">定义用于显示一个或多个.NET 对象的视图。</span><span class="sxs-lookup"><span data-stu-id="e7aab-121">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e7aab-122">备注</span><span class="sxs-lookup"><span data-stu-id="e7aab-122">Remarks</span></span>

<span data-ttu-id="e7aab-123">在大多数情况下，只有一个定义需要为每个控件视图，但可以提供多个定义，如果你想要使用相同的视图以显示不同的.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="e7aab-123">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="e7aab-124">在这些情况下，可以为每个对象或对象集提供一个单独的定义。</span><span class="sxs-lookup"><span data-stu-id="e7aab-124">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="e7aab-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7aab-125">See Also</span></span>

[<span data-ttu-id="e7aab-126">视图 （格式） 的 CustomControl CustomEntries 元素</span><span class="sxs-lookup"><span data-stu-id="e7aab-126">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="e7aab-127">视图元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="e7aab-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="e7aab-128">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="e7aab-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
