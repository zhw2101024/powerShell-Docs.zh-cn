---
title: GroupBy （格式） 的 ExpressionBinding 的 CustomControlName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854293"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="2ec35-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2ec35-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="2ec35-103">指定公共控件或视图控件的名称。</span><span class="sxs-lookup"><span data-stu-id="2ec35-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="2ec35-104">定义如何显示一组新对象时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="2ec35-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="2ec35-105">GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素CustomControl ExpressionBinding 的 GroupBy （格式） 的 GroupBy （格式） CustomControlName 元素 CustomItem GroupBy （格式） ExpressionBinding 元素 CustomEntry GroupBy （格式） CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="2ec35-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2ec35-106">语法</span><span class="sxs-lookup"><span data-stu-id="2ec35-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2ec35-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="2ec35-107">Attributes and Elements</span></span>

<span data-ttu-id="2ec35-108">以下各节描述了特性、 子元素和父元素的`CustomControlName`元素。</span><span class="sxs-lookup"><span data-stu-id="2ec35-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2ec35-109">特性</span><span class="sxs-lookup"><span data-stu-id="2ec35-109">Attributes</span></span>

<span data-ttu-id="2ec35-110">无。</span><span class="sxs-lookup"><span data-stu-id="2ec35-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2ec35-111">子元素</span><span class="sxs-lookup"><span data-stu-id="2ec35-111">Child Elements</span></span>

<span data-ttu-id="2ec35-112">无。</span><span class="sxs-lookup"><span data-stu-id="2ec35-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2ec35-113">父元素</span><span class="sxs-lookup"><span data-stu-id="2ec35-113">Parent Elements</span></span>

|<span data-ttu-id="2ec35-114">元素</span><span class="sxs-lookup"><span data-stu-id="2ec35-114">Element</span></span>|<span data-ttu-id="2ec35-115">描述</span><span class="sxs-lookup"><span data-stu-id="2ec35-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2ec35-116">GroupBy （格式） 的 CustomItem ExpressionBinding 元素</span><span class="sxs-lookup"><span data-stu-id="2ec35-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="2ec35-117">定义由控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="2ec35-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2ec35-118">文本值</span><span class="sxs-lookup"><span data-stu-id="2ec35-118">Text Value</span></span>

<span data-ttu-id="2ec35-119">指定控件的名称。</span><span class="sxs-lookup"><span data-stu-id="2ec35-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="2ec35-120">备注</span><span class="sxs-lookup"><span data-stu-id="2ec35-120">Remarks</span></span>

<span data-ttu-id="2ec35-121">可以创建可由格式设置文件的所有视图的公共控件和您可以创建可都由特定视图的视图控件。</span><span class="sxs-lookup"><span data-stu-id="2ec35-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="2ec35-122">以下元素指定这些控件的名称：</span><span class="sxs-lookup"><span data-stu-id="2ec35-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="2ec35-123">配置 （格式） 的控件的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="2ec35-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="2ec35-124">控件的视图 （格式） 的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="2ec35-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="2ec35-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2ec35-125">See Also</span></span>

[<span data-ttu-id="2ec35-126">配置 （格式） 的控件的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="2ec35-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="2ec35-127">控件的视图 （格式） 的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="2ec35-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="2ec35-128">GroupBy （格式） 的 CustomItem ExpressionBinding 元素</span><span class="sxs-lookup"><span data-stu-id="2ec35-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="2ec35-129">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="2ec35-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
