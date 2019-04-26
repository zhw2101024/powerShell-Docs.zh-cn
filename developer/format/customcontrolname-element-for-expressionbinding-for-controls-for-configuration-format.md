---
title: 配置 （格式） 的控件的 ExpressionBinding 的 CustomControlName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5242935-2782-4d23-84f5-2446b2b7ba83
caps.latest.revision: 8
ms.openlocfilehash: c9abd9f22907b87323c16d603a9f75bb3d375a03
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066628"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="52711-102">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="52711-102">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="52711-103">指定公共控件的名称。</span><span class="sxs-lookup"><span data-stu-id="52711-103">Specifies the name of a common control.</span></span> <span data-ttu-id="52711-104">定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。</span><span class="sxs-lookup"><span data-stu-id="52711-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="52711-105">配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素CustomControl 配置 （格式） 的控件的 Controls 的配置 （格式） CustomControlName CustomItem 配置 ExpressionBinding 元素 CustomEntry CustomItem 元素的控件的格式） CustomEntry 元素ExpressionBinding 的配置 （格式） 的控件的元素</span><span class="sxs-lookup"><span data-stu-id="52711-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="52711-106">语法</span><span class="sxs-lookup"><span data-stu-id="52711-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="52711-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="52711-107">Attributes and Elements</span></span>

<span data-ttu-id="52711-108">以下各节描述了特性、 子元素和父元素的`CustomControlName`元素。</span><span class="sxs-lookup"><span data-stu-id="52711-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="52711-109">属性</span><span class="sxs-lookup"><span data-stu-id="52711-109">Attributes</span></span>

<span data-ttu-id="52711-110">无。</span><span class="sxs-lookup"><span data-stu-id="52711-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="52711-111">子元素</span><span class="sxs-lookup"><span data-stu-id="52711-111">Child Elements</span></span>

<span data-ttu-id="52711-112">无。</span><span class="sxs-lookup"><span data-stu-id="52711-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="52711-113">父元素</span><span class="sxs-lookup"><span data-stu-id="52711-113">Parent Elements</span></span>

|<span data-ttu-id="52711-114">元素</span><span class="sxs-lookup"><span data-stu-id="52711-114">Element</span></span>|<span data-ttu-id="52711-115">说明</span><span class="sxs-lookup"><span data-stu-id="52711-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="52711-116">配置 （格式） 的控件的 CustomItem ExpressionBinding 元素</span><span class="sxs-lookup"><span data-stu-id="52711-116">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="52711-117">定义由控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="52711-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="52711-118">文本值</span><span class="sxs-lookup"><span data-stu-id="52711-118">Text Value</span></span>

<span data-ttu-id="52711-119">指定控件的名称。</span><span class="sxs-lookup"><span data-stu-id="52711-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="52711-120">备注</span><span class="sxs-lookup"><span data-stu-id="52711-120">Remarks</span></span>

<span data-ttu-id="52711-121">可以创建可由格式设置文件的所有视图的公共控件和您可以创建可都由特定视图的视图控件。</span><span class="sxs-lookup"><span data-stu-id="52711-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="52711-122">以下元素指定这些控件的名称：</span><span class="sxs-lookup"><span data-stu-id="52711-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="52711-123">配置 （格式） 的控件的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="52711-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="52711-124">控件的视图 （格式） 的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="52711-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="52711-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="52711-125">See Also</span></span>

[<span data-ttu-id="52711-126">配置 （格式） 的控件的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="52711-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="52711-127">控件的视图 （格式） 的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="52711-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="52711-128">配置 （格式） 的控件的 CustomItem ExpressionBinding 元素</span><span class="sxs-lookup"><span data-stu-id="52711-128">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="52711-129">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="52711-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
