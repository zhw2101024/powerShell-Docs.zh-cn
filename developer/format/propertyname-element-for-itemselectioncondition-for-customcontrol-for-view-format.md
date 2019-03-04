---
title: PropertyName 元素的视图 （格式） 的 CustomControl ItemSelectionCondition |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b12006-8d52-486b-91a3-e6224ca80e56
caps.latest.revision: 6
ms.openlocfilehash: 52d0b0816eaef6752220e0c3b1249e5a0e44a3ee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854783"
---
# <a name="propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="ae4fe-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="ae4fe-102">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="ae4fe-103">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="ae4fe-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="ae4fe-104">存在此属性时或当计算结果为`true`、 满足该条件，并使用该控件。</span><span class="sxs-lookup"><span data-stu-id="ae4fe-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="ae4fe-105">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="ae4fe-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="ae4fe-106">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl 视图 （格式） 的视图 （格式） CustomItem 元素 CustomEntries CustomEntry 元素CustomEntry 视图 （格式） 的视图 （格式） 的 ItemSelectionCondition PropertyName 元素 CustomControl 表达式绑定的视图 （格式） ItemSelectionCondition 元素 CustomControl CustomItem ExpressionBinding 元素视图 （格式为 CustomControl</span><span class="sxs-lookup"><span data-stu-id="ae4fe-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>

## <a name="syntax"></a><span data-ttu-id="ae4fe-107">语法</span><span class="sxs-lookup"><span data-stu-id="ae4fe-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ae4fe-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="ae4fe-108">Attributes and Elements</span></span>

<span data-ttu-id="ae4fe-109">以下各节描述了特性、 子元素和父元素的`PropertyName`元素。</span><span class="sxs-lookup"><span data-stu-id="ae4fe-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ae4fe-110">特性</span><span class="sxs-lookup"><span data-stu-id="ae4fe-110">Attributes</span></span>

<span data-ttu-id="ae4fe-111">无。</span><span class="sxs-lookup"><span data-stu-id="ae4fe-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ae4fe-112">子元素</span><span class="sxs-lookup"><span data-stu-id="ae4fe-112">Child Elements</span></span>

<span data-ttu-id="ae4fe-113">无。</span><span class="sxs-lookup"><span data-stu-id="ae4fe-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ae4fe-114">父元素</span><span class="sxs-lookup"><span data-stu-id="ae4fe-114">Parent Elements</span></span>

|<span data-ttu-id="ae4fe-115">元素</span><span class="sxs-lookup"><span data-stu-id="ae4fe-115">Element</span></span>|<span data-ttu-id="ae4fe-116">描述</span><span class="sxs-lookup"><span data-stu-id="ae4fe-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ae4fe-117">视图 （格式） 的表达式绑定的 CustomControl ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="ae4fe-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="ae4fe-118">定义要在使用此控件中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="ae4fe-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ae4fe-119">文本值</span><span class="sxs-lookup"><span data-stu-id="ae4fe-119">Text Value</span></span>

<span data-ttu-id="ae4fe-120">指定触发条件的.NET 属性的名称。</span><span class="sxs-lookup"><span data-stu-id="ae4fe-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="ae4fe-121">备注</span><span class="sxs-lookup"><span data-stu-id="ae4fe-121">Remarks</span></span>

<span data-ttu-id="ae4fe-122">如果使用此元素时，不能指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)元素定义的选择条件时。</span><span class="sxs-lookup"><span data-stu-id="ae4fe-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae4fe-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ae4fe-123">See Also</span></span>

[<span data-ttu-id="ae4fe-124">为视图 （格式） 的 CustomControl ItemSelectionCondition 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="ae4fe-124">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ae4fe-125">视图 （格式） 的表达式绑定的 CustomControl ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="ae4fe-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="ae4fe-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="ae4fe-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
