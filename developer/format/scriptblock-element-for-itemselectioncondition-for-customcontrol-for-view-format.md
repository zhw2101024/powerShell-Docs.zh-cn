---
title: 脚本块元素的视图 （格式） 的 CustomControl ItemSelectionCondition |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 946cd2b5-ac37-4a13-bb49-29fbc70ec8d7
caps.latest.revision: 6
ms.openlocfilehash: 0c07ab0e5d04c4056a7e7215bfa55773bfccb41d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862233"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format"></a><span data-ttu-id="923ab-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="923ab-102">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

<span data-ttu-id="923ab-103">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="923ab-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="923ab-104">当此脚本的计算结果为`true`、 满足该条件，并使用该控件。</span><span class="sxs-lookup"><span data-stu-id="923ab-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="923ab-105">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="923ab-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="923ab-106">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl 视图 （格式） 的视图 （格式） CustomItem 元素 CustomEntries CustomEntry 元素CustomEntry CustomItem CustomControl CustomControl ItemSelectionCondition 的视图 （格式） 脚本块元素表达式绑定的视图 （格式） ItemSelectionCondition 元素的视图 （格式） ExpressionBinding 元素CustomControl 视图 （格式）</span><span class="sxs-lookup"><span data-stu-id="923ab-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format) ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="923ab-107">语法</span><span class="sxs-lookup"><span data-stu-id="923ab-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="923ab-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="923ab-108">Attributes and Elements</span></span>

<span data-ttu-id="923ab-109">以下各节描述了特性、 子元素和父元素的`ScriptBlock`元素。</span><span class="sxs-lookup"><span data-stu-id="923ab-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="923ab-110">特性</span><span class="sxs-lookup"><span data-stu-id="923ab-110">Attributes</span></span>

<span data-ttu-id="923ab-111">无。</span><span class="sxs-lookup"><span data-stu-id="923ab-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="923ab-112">子元素</span><span class="sxs-lookup"><span data-stu-id="923ab-112">Child Elements</span></span>

<span data-ttu-id="923ab-113">无。</span><span class="sxs-lookup"><span data-stu-id="923ab-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="923ab-114">父元素</span><span class="sxs-lookup"><span data-stu-id="923ab-114">Parent Elements</span></span>

|<span data-ttu-id="923ab-115">元素</span><span class="sxs-lookup"><span data-stu-id="923ab-115">Element</span></span>|<span data-ttu-id="923ab-116">描述</span><span class="sxs-lookup"><span data-stu-id="923ab-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="923ab-117">视图 （格式） 的表达式绑定的 CustomControl ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="923ab-117">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="923ab-118">定义要在使用此控件中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="923ab-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="923ab-119">文本值</span><span class="sxs-lookup"><span data-stu-id="923ab-119">Text Value</span></span>

<span data-ttu-id="923ab-120">指定计算的脚本。</span><span class="sxs-lookup"><span data-stu-id="923ab-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="923ab-121">备注</span><span class="sxs-lookup"><span data-stu-id="923ab-121">Remarks</span></span>

<span data-ttu-id="923ab-122">如果使用此元素时，不能指定[PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)元素定义的选择条件时。</span><span class="sxs-lookup"><span data-stu-id="923ab-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="923ab-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="923ab-123">See Also</span></span>

[<span data-ttu-id="923ab-124">属性名称的视图 （格式） 的 CustomControl ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="923ab-124">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="923ab-125">视图 （格式） 的表达式绑定的 CustomControl ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="923ab-125">ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="923ab-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="923ab-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
