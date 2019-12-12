---
title: 用于控件的控件的名称元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362706"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="9daea-102">Name Element for Control for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="9daea-102">Name Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="9daea-103">指定控件的名称。</span><span class="sxs-lookup"><span data-stu-id="9daea-103">Specifies the name of the control.</span></span> <span data-ttu-id="9daea-104">此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。</span><span class="sxs-lookup"><span data-stu-id="9daea-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="9daea-105">Configuration 元素（格式）控制配置（format）名称元素控件的配置（格式）控件元素的元素，用于控件的配置（格式）</span><span class="sxs-lookup"><span data-stu-id="9daea-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) Name Element for Control for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9daea-106">语法</span><span class="sxs-lookup"><span data-stu-id="9daea-106">Syntax</span></span>

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="9daea-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="9daea-107">Attributes and Elements</span></span>

<span data-ttu-id="9daea-108">以下各节介绍了 `Name` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9daea-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9daea-109">属性</span><span class="sxs-lookup"><span data-stu-id="9daea-109">Attributes</span></span>

<span data-ttu-id="9daea-110">无。</span><span class="sxs-lookup"><span data-stu-id="9daea-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9daea-111">子元素</span><span class="sxs-lookup"><span data-stu-id="9daea-111">Child Elements</span></span>

<span data-ttu-id="9daea-112">无。</span><span class="sxs-lookup"><span data-stu-id="9daea-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9daea-113">父元素</span><span class="sxs-lookup"><span data-stu-id="9daea-113">Parent Elements</span></span>

|<span data-ttu-id="9daea-114">元素</span><span class="sxs-lookup"><span data-stu-id="9daea-114">Element</span></span>|<span data-ttu-id="9daea-115">描述</span><span class="sxs-lookup"><span data-stu-id="9daea-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9daea-116">用于配置控件的控件元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9daea-116">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="9daea-117">定义一个公共控件，该控件可供格式设置文件的所有视图和用于引用控件的名称使用。</span><span class="sxs-lookup"><span data-stu-id="9daea-117">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9daea-118">文本值</span><span class="sxs-lookup"><span data-stu-id="9daea-118">Text Value</span></span>

<span data-ttu-id="9daea-119">指定用于引用此控件的名称。</span><span class="sxs-lookup"><span data-stu-id="9daea-119">Specify the name that is used to reference this control.</span></span>

## <a name="remarks"></a><span data-ttu-id="9daea-120">备注</span><span class="sxs-lookup"><span data-stu-id="9daea-120">Remarks</span></span>

<span data-ttu-id="9daea-121">此处指定的名称可以用在以下元素中以引用此控件。</span><span class="sxs-lookup"><span data-stu-id="9daea-121">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="9daea-122">创建表、列表、宽控件或自定义控件视图时，可通过以下元素指定控件： [view 的 GroupBy 元素（Format）](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="9daea-122">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="9daea-123">创建另一个公共控件时，可以通过以下元素指定此控件：用于[配置的控件的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span><span class="sxs-lookup"><span data-stu-id="9daea-123">When creating another common control, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for Configuration (Format)](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)</span></span>

- <span data-ttu-id="9daea-124">创建可由视图使用的控件时，可以通过以下元素指定此控件：用于视图的控件的[CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="9daea-124">When creating a control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="9daea-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9daea-125">See Also</span></span>

[<span data-ttu-id="9daea-126">用于配置控件的控件元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9daea-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="9daea-127">用于配置的控件的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9daea-127">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="9daea-128">用于视图的控件的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9daea-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="9daea-129">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9daea-129">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="9daea-130">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="9daea-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
