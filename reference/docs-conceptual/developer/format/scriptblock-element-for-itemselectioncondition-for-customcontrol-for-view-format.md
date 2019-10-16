---
title: CustomControl 的 ItemSelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362066"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="68648-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="68648-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="68648-103">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="68648-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="68648-104">如果此脚本的计算结果为 `true`，则满足条件，并使用控件。</span><span class="sxs-lookup"><span data-stu-id="68648-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="68648-105">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="68648-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="68648-106">用于 CustomEntry 的 CustomControl for view （format） CustomEntries 元素的 ViewDefinitions 元素（format） View 元素（format） CustomControl 元素（format） CustomEntries 元素CustomEntry for View （Format） ExpressionBinding 元素 for CustomItem for CustomControl for view （format） ItemSelectionCondition 元素 for CustomControl for View （Format） ScriptBlock 元素 for ItemSelectionCondition forCustomControl for View （Format）</span><span class="sxs-lookup"><span data-stu-id="68648-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="68648-107">语法</span><span class="sxs-lookup"><span data-stu-id="68648-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="68648-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="68648-108">Attributes and Elements</span></span>

<span data-ttu-id="68648-109">以下各节介绍了 `ScriptBlock` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="68648-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="68648-110">属性</span><span class="sxs-lookup"><span data-stu-id="68648-110">Attributes</span></span>

<span data-ttu-id="68648-111">无。</span><span class="sxs-lookup"><span data-stu-id="68648-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="68648-112">子元素</span><span class="sxs-lookup"><span data-stu-id="68648-112">Child Elements</span></span>

<span data-ttu-id="68648-113">无。</span><span class="sxs-lookup"><span data-stu-id="68648-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="68648-114">父元素</span><span class="sxs-lookup"><span data-stu-id="68648-114">Parent Elements</span></span>

|<span data-ttu-id="68648-115">元素</span><span class="sxs-lookup"><span data-stu-id="68648-115">Element</span></span>|<span data-ttu-id="68648-116">描述</span><span class="sxs-lookup"><span data-stu-id="68648-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="68648-117">用于视图的 CustomControl 的表达式绑定的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="68648-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="68648-118">定义要使用此控件必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="68648-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="68648-119">文本值</span><span class="sxs-lookup"><span data-stu-id="68648-119">Text Value</span></span>

<span data-ttu-id="68648-120">指定要评估的脚本。</span><span class="sxs-lookup"><span data-stu-id="68648-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="68648-121">备注</span><span class="sxs-lookup"><span data-stu-id="68648-121">Remarks</span></span>

<span data-ttu-id="68648-122">如果使用此元素，则在定义选择条件时，不能指定[PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="68648-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="68648-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="68648-123">See Also</span></span>

[<span data-ttu-id="68648-124">View 的 ItemSelectionCondition for CustomControl 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="68648-124">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="68648-125">用于视图的 CustomControl 的表达式绑定的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="68648-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="68648-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="68648-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
