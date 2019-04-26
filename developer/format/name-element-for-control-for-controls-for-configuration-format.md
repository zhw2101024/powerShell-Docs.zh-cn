---
title: 命名元素的控件的控件配置 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065183"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="8fdbe-102">Name Element for Control for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="8fdbe-102">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="8fdbe-103">指定控件的名称。</span><span class="sxs-lookup"><span data-stu-id="8fdbe-103">Specifies the name of the control.</span></span> <span data-ttu-id="8fdbe-104">定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。</span><span class="sxs-lookup"><span data-stu-id="8fdbe-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="8fdbe-105">配置 （格式） 的配置 （格式） 的配置 （格式） 的控件的控件的名称元素的控件的控件元素的配置元素 （格式） 的 Controls 元素</span><span class="sxs-lookup"><span data-stu-id="8fdbe-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8fdbe-106">语法</span><span class="sxs-lookup"><span data-stu-id="8fdbe-106">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="8fdbe-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="8fdbe-107">Attributes and Elements</span></span>

<span data-ttu-id="8fdbe-108">以下各节描述了特性、 子元素和父元素的`Name`元素。</span><span class="sxs-lookup"><span data-stu-id="8fdbe-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8fdbe-109">属性</span><span class="sxs-lookup"><span data-stu-id="8fdbe-109">Attributes</span></span>

<span data-ttu-id="8fdbe-110">无。</span><span class="sxs-lookup"><span data-stu-id="8fdbe-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8fdbe-111">子元素</span><span class="sxs-lookup"><span data-stu-id="8fdbe-111">Child Elements</span></span>

<span data-ttu-id="8fdbe-112">无。</span><span class="sxs-lookup"><span data-stu-id="8fdbe-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8fdbe-113">父元素</span><span class="sxs-lookup"><span data-stu-id="8fdbe-113">Parent Elements</span></span>

|<span data-ttu-id="8fdbe-114">元素</span><span class="sxs-lookup"><span data-stu-id="8fdbe-114">Element</span></span>|<span data-ttu-id="8fdbe-115">说明</span><span class="sxs-lookup"><span data-stu-id="8fdbe-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8fdbe-116">配置 （格式） 的控件的控件元素</span><span class="sxs-lookup"><span data-stu-id="8fdbe-116">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="8fdbe-117">定义可由格式设置文件和名称，用于引用该控件的所有视图的公共控件。</span><span class="sxs-lookup"><span data-stu-id="8fdbe-117">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="8fdbe-118">文本值</span><span class="sxs-lookup"><span data-stu-id="8fdbe-118">Text Value</span></span>

<span data-ttu-id="8fdbe-119">指定用于引用此控件的名称。</span><span class="sxs-lookup"><span data-stu-id="8fdbe-119">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="8fdbe-120">备注</span><span class="sxs-lookup"><span data-stu-id="8fdbe-120">Remarks</span></span>

<span data-ttu-id="8fdbe-121">此处指定的名称可以在以下元素中，用于引用此控件。</span><span class="sxs-lookup"><span data-stu-id="8fdbe-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="8fdbe-122">在创建表、 列表、 宽或自定义控件视图时，可以通过下面的元素指定的控件：[视图 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="8fdbe-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="8fdbe-123">在创建另一个常见的控件时，此控件可以指定由以下元素：[配置 （格式） 的控件的 CustomItem ExpressionBinding 元素](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="8fdbe-123">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="8fdbe-124">当创建控件可以使用的视图时，此控件可以指定由以下元素：[ExpressionBinding CustomItem 视图 （格式） 的控件元素](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="8fdbe-124">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="8fdbe-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8fdbe-125">See Also</span></span>

[<span data-ttu-id="8fdbe-126">配置 （格式） 的控件的控件元素</span><span class="sxs-lookup"><span data-stu-id="8fdbe-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="8fdbe-127">配置 （格式） 的控件的 CustomItem ExpressionBinding 元素</span><span class="sxs-lookup"><span data-stu-id="8fdbe-127">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="8fdbe-128">ExpressionBinding CustomItem 视图 （格式） 的控件元素</span><span class="sxs-lookup"><span data-stu-id="8fdbe-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="8fdbe-129">视图 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="8fdbe-129">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="8fdbe-130">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="8fdbe-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
