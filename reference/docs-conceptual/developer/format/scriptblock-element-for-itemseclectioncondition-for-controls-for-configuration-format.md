---
title: 用于配置（格式）的控件的 ItemSeclectionCondition 的 ScriptBlock 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51f7aec9-7b01-4370-84f4-1e58508a851f
caps.latest.revision: 6
ms.openlocfilehash: e92b2dfff07358132c480c47c34279e5365fe400
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362116"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="2434e-102">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="2434e-102">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="2434e-103">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="2434e-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="2434e-104">如果此脚本的计算结果为 `true`，则满足条件，并使用控件。</span><span class="sxs-lookup"><span data-stu-id="2434e-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="2434e-105">此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。</span><span class="sxs-lookup"><span data-stu-id="2434e-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="2434e-106">Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format） CustomEntry 元素 for CustomControl for CustomItem 元素 for CustomEntry for 元素 for for ExpressionBinding for configuration CustomItem 元素 for for controlExpressionBinding 的 ItemSelectionCondition 元素，用于配置的控件的 ItemSelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2434e-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2434e-107">语法</span><span class="sxs-lookup"><span data-stu-id="2434e-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2434e-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="2434e-108">Attributes and Elements</span></span>

<span data-ttu-id="2434e-109">以下各节介绍了 `ScriptBlock` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2434e-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2434e-110">属性</span><span class="sxs-lookup"><span data-stu-id="2434e-110">Attributes</span></span>

<span data-ttu-id="2434e-111">无。</span><span class="sxs-lookup"><span data-stu-id="2434e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2434e-112">子元素</span><span class="sxs-lookup"><span data-stu-id="2434e-112">Child Elements</span></span>

<span data-ttu-id="2434e-113">无。</span><span class="sxs-lookup"><span data-stu-id="2434e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2434e-114">父元素</span><span class="sxs-lookup"><span data-stu-id="2434e-114">Parent Elements</span></span>

|<span data-ttu-id="2434e-115">元素</span><span class="sxs-lookup"><span data-stu-id="2434e-115">Element</span></span>|<span data-ttu-id="2434e-116">描述</span><span class="sxs-lookup"><span data-stu-id="2434e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2434e-117">用于配置的控件的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2434e-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="2434e-118">定义要使用此控件必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="2434e-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2434e-119">文本值</span><span class="sxs-lookup"><span data-stu-id="2434e-119">Text Value</span></span>

<span data-ttu-id="2434e-120">指定要评估的脚本。</span><span class="sxs-lookup"><span data-stu-id="2434e-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="2434e-121">备注</span><span class="sxs-lookup"><span data-stu-id="2434e-121">Remarks</span></span>

<span data-ttu-id="2434e-122">如果使用此元素，则在定义选择条件时，不能指定[PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="2434e-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="2434e-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2434e-123">See Also</span></span>

[<span data-ttu-id="2434e-124">用于配置的控件的 ItemSeclectionCondition 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2434e-124">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="2434e-125">用于配置的控件的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2434e-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="2434e-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="2434e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
