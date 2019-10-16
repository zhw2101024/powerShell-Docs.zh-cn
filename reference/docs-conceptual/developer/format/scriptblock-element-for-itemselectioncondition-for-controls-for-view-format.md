---
title: 用于视图（格式）的控件的 ItemSelectionCondition 的 ScriptBlock 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4191157-bf01-4831-b221-6f8cc581cd53
caps.latest.revision: 6
ms.openlocfilehash: 0cbefbb48427b56d4ae2a5ae27c7726dcfad7b84
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364916"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-controls-for-view-format"></a><span data-ttu-id="e6018-102">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="e6018-102">ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="e6018-103">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="e6018-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="e6018-104">如果此脚本的计算结果为 `true`，则满足条件，并使用控件。</span><span class="sxs-lookup"><span data-stu-id="e6018-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="e6018-105">定义可由视图使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="e6018-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="e6018-106">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 元素（format） Control 元素 for View （format） CustomControl 元素的控件元素，用于控件的 View （format） CustomEntries 元素CustomControl for view （Format） CustomEntry 元素 for CustomEntries for view （format） CustomItem 元素 for CustomEntry for view （format）元素 for ExpressionBinding for view （format）的控件ExpressionBinding 的 ItemSelectionCondition 元素，用于视图的控件的 ItemSelectionCondition 的（格式） ScriptBlock 元素</span><span class="sxs-lookup"><span data-stu-id="e6018-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format) ScriptBlock Element for ItemSelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e6018-107">语法</span><span class="sxs-lookup"><span data-stu-id="e6018-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e6018-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="e6018-108">Attributes and Elements</span></span>

<span data-ttu-id="e6018-109">以下各节介绍了 `ScriptBlock` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e6018-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e6018-110">属性</span><span class="sxs-lookup"><span data-stu-id="e6018-110">Attributes</span></span>

<span data-ttu-id="e6018-111">无。</span><span class="sxs-lookup"><span data-stu-id="e6018-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e6018-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e6018-112">Child Elements</span></span>

<span data-ttu-id="e6018-113">无。</span><span class="sxs-lookup"><span data-stu-id="e6018-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e6018-114">父元素</span><span class="sxs-lookup"><span data-stu-id="e6018-114">Parent Elements</span></span>

|<span data-ttu-id="e6018-115">元素</span><span class="sxs-lookup"><span data-stu-id="e6018-115">Element</span></span>|<span data-ttu-id="e6018-116">描述</span><span class="sxs-lookup"><span data-stu-id="e6018-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e6018-117">用于视图的控件的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e6018-117">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)|<span data-ttu-id="e6018-118">定义要使用此控件必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="e6018-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e6018-119">文本值</span><span class="sxs-lookup"><span data-stu-id="e6018-119">Text Value</span></span>

<span data-ttu-id="e6018-120">指定要评估的脚本。</span><span class="sxs-lookup"><span data-stu-id="e6018-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="e6018-121">备注</span><span class="sxs-lookup"><span data-stu-id="e6018-121">Remarks</span></span>

<span data-ttu-id="e6018-122">如果使用此元素，则在定义选择条件时，不能指定[PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="e6018-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6018-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e6018-123">See Also</span></span>

[<span data-ttu-id="e6018-124">View 的 ItemSelectionCondition for Controls 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="e6018-124">PropertyName Element for ItemSelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="e6018-125">用于视图的控件的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="e6018-125">ItemSelectionCondition Element of ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="e6018-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="e6018-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
