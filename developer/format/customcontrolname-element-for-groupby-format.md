---
title: GroupBy （格式） 的 CustomControlName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 473d9b56-521b-479a-8010-67fe9f040063
caps.latest.revision: 8
ms.openlocfilehash: 3a386eff95044eae573c255a451c5c8b8f16714d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860303"
---
# <a name="customcontrolname-element-for-groupby-format"></a><span data-ttu-id="a9ed0-102">CustomControlName Element for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="a9ed0-102">CustomControlName Element for GroupBy (Format)</span></span>

<span data-ttu-id="a9ed0-103">指定用来显示新组的自定义控件的名称。</span><span class="sxs-lookup"><span data-stu-id="a9ed0-103">Specifies the name of a custom control that is used to display the new group.</span></span> <span data-ttu-id="a9ed0-104">定义表、 列表、 宽或自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="a9ed0-104">This element is used when defining a table, list, wide or custom control view.</span></span>

<span data-ttu-id="a9ed0-105">GroupBy （格式） 的视图 （格式） CustomControlName 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="a9ed0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControlName Element of GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a9ed0-106">语法</span><span class="sxs-lookup"><span data-stu-id="a9ed0-106">Syntax</span></span>

```xml
<CustomControlName>ControlName</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a9ed0-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="a9ed0-107">Attributes and Elements</span></span>

<span data-ttu-id="a9ed0-108">以下各节描述的特性、 子元素和父元素的`CustomControlName`元素。</span><span class="sxs-lookup"><span data-stu-id="a9ed0-108">The following sections describe the attributes, child elements, and parent elements of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a9ed0-109">特性</span><span class="sxs-lookup"><span data-stu-id="a9ed0-109">Attributes</span></span>

<span data-ttu-id="a9ed0-110">无。</span><span class="sxs-lookup"><span data-stu-id="a9ed0-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a9ed0-111">子元素</span><span class="sxs-lookup"><span data-stu-id="a9ed0-111">Child Elements</span></span>

<span data-ttu-id="a9ed0-112">无。</span><span class="sxs-lookup"><span data-stu-id="a9ed0-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a9ed0-113">父元素</span><span class="sxs-lookup"><span data-stu-id="a9ed0-113">Parent Elements</span></span>

|<span data-ttu-id="a9ed0-114">元素</span><span class="sxs-lookup"><span data-stu-id="a9ed0-114">Element</span></span>|<span data-ttu-id="a9ed0-115">描述</span><span class="sxs-lookup"><span data-stu-id="a9ed0-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a9ed0-116">视图 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="a9ed0-116">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="a9ed0-117">定义 Windows PowerShell 如何显示对象的新的组。</span><span class="sxs-lookup"><span data-stu-id="a9ed0-117">Defines how Windows PowerShell displays a new group of objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a9ed0-118">文本值</span><span class="sxs-lookup"><span data-stu-id="a9ed0-118">Text Value</span></span>

<span data-ttu-id="a9ed0-119">指定用来显示新组的自定义控件的名称。</span><span class="sxs-lookup"><span data-stu-id="a9ed0-119">Specify the name of the custom control that is used to display a new group.</span></span>

## <a name="remarks"></a><span data-ttu-id="a9ed0-120">备注</span><span class="sxs-lookup"><span data-stu-id="a9ed0-120">Remarks</span></span>

<span data-ttu-id="a9ed0-121">可以创建可由格式设置文件的所有视图的公共控件和您可以创建可都由特定视图的视图控件。</span><span class="sxs-lookup"><span data-stu-id="a9ed0-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="a9ed0-122">以下元素指定这些自定义控件的名称：</span><span class="sxs-lookup"><span data-stu-id="a9ed0-122">The following elements specify the names of these custom controls:</span></span>

- [<span data-ttu-id="a9ed0-123">配置 （格式） 的控件的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="a9ed0-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="a9ed0-124">控件的视图 （格式） 的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="a9ed0-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="a9ed0-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a9ed0-125">See Also</span></span>

[<span data-ttu-id="a9ed0-126">视图 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="a9ed0-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="a9ed0-127">配置 （格式） 的控件的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="a9ed0-127">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="a9ed0-128">控件的视图 （格式） 的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="a9ed0-128">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="a9ed0-129">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="a9ed0-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
