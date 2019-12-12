---
title: GroupBy 的 ItemSelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58d25835-4636-4c58-9f6c-0332b9318051
caps.latest.revision: 6
ms.openlocfilehash: 4045196e306e766cd805b3e7ae31bfcb3de184ee
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364826"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-groupby-format"></a><span data-ttu-id="9d17e-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9d17e-102">ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="9d17e-103">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="9d17e-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="9d17e-104">如果此脚本的计算结果为 `true`，则满足条件，并使用控件。</span><span class="sxs-lookup"><span data-stu-id="9d17e-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="9d17e-105">此元素在定义如何显示新的对象组时使用。</span><span class="sxs-lookup"><span data-stu-id="9d17e-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="9d17e-106">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）CustomControl for GroupBy （format） CustomItem 元素 for CustomEntry for groupby （format） ExpressionBinding 元素 for CustomItem for groupby （format） ScriptBlock 元素 for ItemSelectionCondition for groupby （format） ScriptBlock 元素ItemSelectionCondition for GroupBy （Format）</span><span class="sxs-lookup"><span data-stu-id="9d17e-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format) ScriptBlock Element for ItemSelectionCondition for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9d17e-107">语法</span><span class="sxs-lookup"><span data-stu-id="9d17e-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9d17e-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="9d17e-108">Attributes and Elements</span></span>

<span data-ttu-id="9d17e-109">以下各节介绍了 `ScriptBlock` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9d17e-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9d17e-110">属性</span><span class="sxs-lookup"><span data-stu-id="9d17e-110">Attributes</span></span>

<span data-ttu-id="9d17e-111">无。</span><span class="sxs-lookup"><span data-stu-id="9d17e-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9d17e-112">子元素</span><span class="sxs-lookup"><span data-stu-id="9d17e-112">Child Elements</span></span>

<span data-ttu-id="9d17e-113">无。</span><span class="sxs-lookup"><span data-stu-id="9d17e-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9d17e-114">父元素</span><span class="sxs-lookup"><span data-stu-id="9d17e-114">Parent Elements</span></span>

|<span data-ttu-id="9d17e-115">元素</span><span class="sxs-lookup"><span data-stu-id="9d17e-115">Element</span></span>|<span data-ttu-id="9d17e-116">描述</span><span class="sxs-lookup"><span data-stu-id="9d17e-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9d17e-117">GroupBy 的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9d17e-117">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|<span data-ttu-id="9d17e-118">定义要使用此控件必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="9d17e-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9d17e-119">文本值</span><span class="sxs-lookup"><span data-stu-id="9d17e-119">Text Value</span></span>

<span data-ttu-id="9d17e-120">指定要评估的脚本。</span><span class="sxs-lookup"><span data-stu-id="9d17e-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="9d17e-121">备注</span><span class="sxs-lookup"><span data-stu-id="9d17e-121">Remarks</span></span>

<span data-ttu-id="9d17e-122">如果使用此元素，则在定义选择条件时，不能指定[PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="9d17e-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-groupby-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d17e-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9d17e-123">See Also</span></span>

[<span data-ttu-id="9d17e-124">GroupBy 的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9d17e-124">ItemSelectionCondition Element for ExpressionBinding for GroupBy (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="9d17e-125">GroupBy 的 ItemSelectionCondition 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="9d17e-125">PropertyName Element for ItemSelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-groupby-format.md)

[<span data-ttu-id="9d17e-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="9d17e-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
