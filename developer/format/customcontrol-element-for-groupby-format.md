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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066747"
---
# <a name="customcontrol-element-for-groupby-format"></a><span data-ttu-id="bdd47-102">CustomControl Element for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="bdd47-102">CustomControl Element for GroupBy (Format)</span></span>

<span data-ttu-id="bdd47-103">定义显示新组的自定义控件。</span><span class="sxs-lookup"><span data-stu-id="bdd47-103">Defines the custom control that displays the new group.</span></span>

<span data-ttu-id="bdd47-104">GroupBy （格式） 的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="bdd47-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bdd47-105">语法</span><span class="sxs-lookup"><span data-stu-id="bdd47-105">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
<CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bdd47-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="bdd47-106">Attributes and Elements</span></span>

<span data-ttu-id="bdd47-107">以下各节描述的特性、 子元素和父元素的`CustomControl`元素。</span><span class="sxs-lookup"><span data-stu-id="bdd47-107">The following sections describe the attributes, child elements, and parent element of the `CustomControl` element.</span></span> <span data-ttu-id="bdd47-108">可以指定任意数量的子元素，并按任何顺序列出它们。</span><span class="sxs-lookup"><span data-stu-id="bdd47-108">You can specify any number of child elements and list them in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="bdd47-109">属性</span><span class="sxs-lookup"><span data-stu-id="bdd47-109">Attributes</span></span>

<span data-ttu-id="bdd47-110">无。</span><span class="sxs-lookup"><span data-stu-id="bdd47-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bdd47-111">子元素</span><span class="sxs-lookup"><span data-stu-id="bdd47-111">Child Elements</span></span>

|<span data-ttu-id="bdd47-112">元素</span><span class="sxs-lookup"><span data-stu-id="bdd47-112">Element</span></span>|<span data-ttu-id="bdd47-113">说明</span><span class="sxs-lookup"><span data-stu-id="bdd47-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bdd47-114">GroupBy （格式） 的 CustomControl CustomEntries 元素</span><span class="sxs-lookup"><span data-stu-id="bdd47-114">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="bdd47-115">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="bdd47-115">Required element.</span></span><br /><br /> <span data-ttu-id="bdd47-116">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="bdd47-116">Provides the definitions for the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bdd47-117">父元素</span><span class="sxs-lookup"><span data-stu-id="bdd47-117">Parent Elements</span></span>

|<span data-ttu-id="bdd47-118">元素</span><span class="sxs-lookup"><span data-stu-id="bdd47-118">Element</span></span>|<span data-ttu-id="bdd47-119">说明</span><span class="sxs-lookup"><span data-stu-id="bdd47-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bdd47-120">视图 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="bdd47-120">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="bdd47-121">定义 Windows PowerShell 如何显示对象的新的组。</span><span class="sxs-lookup"><span data-stu-id="bdd47-121">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bdd47-122">备注</span><span class="sxs-lookup"><span data-stu-id="bdd47-122">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="bdd47-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bdd47-123">See Also</span></span>

[<span data-ttu-id="bdd47-124">GroupBy （格式） 的 CustomControl CustomEntries 元素</span><span class="sxs-lookup"><span data-stu-id="bdd47-124">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="bdd47-125">视图 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="bdd47-125">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="bdd47-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="bdd47-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
