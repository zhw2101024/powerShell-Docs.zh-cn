---
title: ExpressionBinding 的 Controls 的视图 （格式） 的 CustomControlName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855593"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="3cde5-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="3cde5-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="3cde5-103">指定公共控件或视图控件的名称。</span><span class="sxs-lookup"><span data-stu-id="3cde5-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="3cde5-104">定义一个视图，可以使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="3cde5-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="3cde5-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl CustomEntries CustomEntry 视图 （格式） 的控件的视图 （格式） CustomControlName CustomItem ExpressionBinding 元素的控件的视图 （格式） CustomItem 元素的控件的视图 （格式） CustomEntry 元素ExpressionBindine 视图 （格式） 的控件的元素</span><span class="sxs-lookup"><span data-stu-id="3cde5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3cde5-106">语法</span><span class="sxs-lookup"><span data-stu-id="3cde5-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3cde5-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="3cde5-107">Attributes and Elements</span></span>

<span data-ttu-id="3cde5-108">以下各节描述了特性、 子元素和父元素的`CustomControlName`元素。</span><span class="sxs-lookup"><span data-stu-id="3cde5-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3cde5-109">特性</span><span class="sxs-lookup"><span data-stu-id="3cde5-109">Attributes</span></span>

<span data-ttu-id="3cde5-110">无。</span><span class="sxs-lookup"><span data-stu-id="3cde5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3cde5-111">子元素</span><span class="sxs-lookup"><span data-stu-id="3cde5-111">Child Elements</span></span>

<span data-ttu-id="3cde5-112">无。</span><span class="sxs-lookup"><span data-stu-id="3cde5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3cde5-113">父元素</span><span class="sxs-lookup"><span data-stu-id="3cde5-113">Parent Elements</span></span>

|<span data-ttu-id="3cde5-114">元素</span><span class="sxs-lookup"><span data-stu-id="3cde5-114">Element</span></span>|<span data-ttu-id="3cde5-115">描述</span><span class="sxs-lookup"><span data-stu-id="3cde5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3cde5-116">ExpressionBinding CustomItem 视图 （格式） 的控件元素</span><span class="sxs-lookup"><span data-stu-id="3cde5-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="3cde5-117">定义由控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="3cde5-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3cde5-118">文本值</span><span class="sxs-lookup"><span data-stu-id="3cde5-118">Text Value</span></span>

<span data-ttu-id="3cde5-119">指定控件的名称。</span><span class="sxs-lookup"><span data-stu-id="3cde5-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="3cde5-120">备注</span><span class="sxs-lookup"><span data-stu-id="3cde5-120">Remarks</span></span>

<span data-ttu-id="3cde5-121">可以创建可由格式设置文件的所有视图的公共控件和您可以创建可都由特定视图的视图控件。</span><span class="sxs-lookup"><span data-stu-id="3cde5-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="3cde5-122">以下元素指定这些控件的名称：</span><span class="sxs-lookup"><span data-stu-id="3cde5-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="3cde5-123">配置 （格式） 的控件的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="3cde5-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="3cde5-124">控件的视图 （格式） 的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="3cde5-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="3cde5-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3cde5-125">See Also</span></span>

[<span data-ttu-id="3cde5-126">配置 （格式） 的控件的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="3cde5-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="3cde5-127">控件的视图 （格式） 的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="3cde5-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="3cde5-128">ExpressionBinding CustomItem 视图 （格式） 的控件元素</span><span class="sxs-lookup"><span data-stu-id="3cde5-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="3cde5-129">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="3cde5-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
