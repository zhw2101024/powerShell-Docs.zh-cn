---
title: GroupBy （格式） 的 CustomControl 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2472e256-8f4f-4288-8b67-a3300649dafa
caps.latest.revision: 9
ms.openlocfilehash: 2e84e770a345e272d4c5917b00afe7520840e1db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853743"
---
# <a name="customcontrol-element-for-groupby-format"></a><span data-ttu-id="7cb13-102">CustomControl Element for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7cb13-102">CustomControl Element for GroupBy (Format)</span></span>

<span data-ttu-id="7cb13-103">定义显示新组的自定义控件。</span><span class="sxs-lookup"><span data-stu-id="7cb13-103">Defines the custom control that displays the new group.</span></span>

<span data-ttu-id="7cb13-104">GroupBy （格式） 的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="7cb13-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7cb13-105">语法</span><span class="sxs-lookup"><span data-stu-id="7cb13-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
<CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7cb13-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="7cb13-106">Attributes and Elements</span></span>

<span data-ttu-id="7cb13-107">以下各节描述的特性、 子元素和父元素的`CustomControl`元素。</span><span class="sxs-lookup"><span data-stu-id="7cb13-107">The following sections describe the attributes, child elements, and parent element of the `CustomControl` element.</span></span> <span data-ttu-id="7cb13-108">可以指定任意数量的子元素，并按任何顺序列出它们。</span><span class="sxs-lookup"><span data-stu-id="7cb13-108">You can specify any number of child elements and list them in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="7cb13-109">特性</span><span class="sxs-lookup"><span data-stu-id="7cb13-109">Attributes</span></span>

<span data-ttu-id="7cb13-110">无。</span><span class="sxs-lookup"><span data-stu-id="7cb13-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7cb13-111">子元素</span><span class="sxs-lookup"><span data-stu-id="7cb13-111">Child Elements</span></span>

|<span data-ttu-id="7cb13-112">元素</span><span class="sxs-lookup"><span data-stu-id="7cb13-112">Element</span></span>|<span data-ttu-id="7cb13-113">描述</span><span class="sxs-lookup"><span data-stu-id="7cb13-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7cb13-114">GroupBy （格式） 的 CustomControl CustomEntries 元素</span><span class="sxs-lookup"><span data-stu-id="7cb13-114">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="7cb13-115">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="7cb13-115">Required element.</span></span><br /><br /> <span data-ttu-id="7cb13-116">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="7cb13-116">Provides the definitions for the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7cb13-117">父元素</span><span class="sxs-lookup"><span data-stu-id="7cb13-117">Parent Elements</span></span>

|<span data-ttu-id="7cb13-118">元素</span><span class="sxs-lookup"><span data-stu-id="7cb13-118">Element</span></span>|<span data-ttu-id="7cb13-119">描述</span><span class="sxs-lookup"><span data-stu-id="7cb13-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7cb13-120">视图 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="7cb13-120">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="7cb13-121">定义 Windows PowerShell 如何显示对象的新的组。</span><span class="sxs-lookup"><span data-stu-id="7cb13-121">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7cb13-122">备注</span><span class="sxs-lookup"><span data-stu-id="7cb13-122">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="7cb13-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7cb13-123">See Also</span></span>

[<span data-ttu-id="7cb13-124">GroupBy （格式） 的 CustomControl CustomEntries 元素</span><span class="sxs-lookup"><span data-stu-id="7cb13-124">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="7cb13-125">视图 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="7cb13-125">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="7cb13-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="7cb13-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
