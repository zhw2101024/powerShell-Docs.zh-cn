---
title: ItemSelectionCondition 视图 （格式） 的控件的属性名称元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba3955bc-f3a1-4ef6-86ac-80ffc133ad1b
caps.latest.revision: 6
ms.openlocfilehash: 28ad31be4be7be20f1f43ea1b69ad5d294de86f6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075845"
---
# <a name="propertyname-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="65475-102">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="65475-102">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="65475-103">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="65475-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="65475-104">存在此属性时或当计算结果为`true`、 满足该条件，并使用该控件。</span><span class="sxs-lookup"><span data-stu-id="65475-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="65475-105">定义一个视图，可以使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="65475-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="65475-106">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控件元素 （格式） 控制元素的控件的视图 （格式） CustomEntries 元素的控件的控件的视图 （格式） CustomControl 元素CustomControl CustomEntries CustomEntry CustomItem 视图 （格式） 的控件的视图 （格式） ExpressionBinding 元素的控件的视图 （格式） CustomItem 元素的控件的视图 （格式） CustomEntry 元素ExpressionBinding ItemSelectionCondition 视图 （格式） 的控件的视图 （格式） PropertyName 元素的控件的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="65475-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="65475-107">语法</span><span class="sxs-lookup"><span data-stu-id="65475-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="65475-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="65475-108">Attributes and Elements</span></span>

<span data-ttu-id="65475-109">以下各节描述了特性、 子元素和父元素的`PropertyName`元素。</span><span class="sxs-lookup"><span data-stu-id="65475-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="65475-110">属性</span><span class="sxs-lookup"><span data-stu-id="65475-110">Attributes</span></span>

<span data-ttu-id="65475-111">无。</span><span class="sxs-lookup"><span data-stu-id="65475-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="65475-112">子元素</span><span class="sxs-lookup"><span data-stu-id="65475-112">Child Elements</span></span>

<span data-ttu-id="65475-113">无。</span><span class="sxs-lookup"><span data-stu-id="65475-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="65475-114">父元素</span><span class="sxs-lookup"><span data-stu-id="65475-114">Parent Elements</span></span>

|<span data-ttu-id="65475-115">元素</span><span class="sxs-lookup"><span data-stu-id="65475-115">Element</span></span>|<span data-ttu-id="65475-116">说明</span><span class="sxs-lookup"><span data-stu-id="65475-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="65475-117">ExpressionBinding 的 Controls 的视图 （格式） 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="65475-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="65475-118">定义要在使用此控件中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="65475-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="65475-119">文本值</span><span class="sxs-lookup"><span data-stu-id="65475-119">Text Value</span></span>

<span data-ttu-id="65475-120">指定触发条件的.NET 属性的名称。</span><span class="sxs-lookup"><span data-stu-id="65475-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="65475-121">备注</span><span class="sxs-lookup"><span data-stu-id="65475-121">Remarks</span></span>

<span data-ttu-id="65475-122">如果使用此元素时，不能指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)元素定义的选择条件时。</span><span class="sxs-lookup"><span data-stu-id="65475-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="65475-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="65475-123">See Also</span></span>

[<span data-ttu-id="65475-124">ItemSelectionCondition 的 Controls 的视图 （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="65475-124">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="65475-125">ExpressionBinding 的 Controls 的视图 （格式） 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="65475-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="65475-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="65475-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
