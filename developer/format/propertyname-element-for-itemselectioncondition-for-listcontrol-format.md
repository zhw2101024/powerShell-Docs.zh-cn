---
title: PropertyName 元素 ListControl （格式） 的 ItemSelectionCondition |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855533"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="9f76a-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="9f76a-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="9f76a-103">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="9f76a-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="9f76a-104">存在此属性时或当计算结果为`true`、 满足该条件，以及使用该视图。</span><span class="sxs-lookup"><span data-stu-id="9f76a-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="9f76a-105">定义列表视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="9f76a-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="9f76a-106">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 （格式） ListEntry 元素 ListControl （格式） 的 ListControl （格式） ListItem ListEntry Listitem 元素ListItems ListControl （格式） ItemSelectionCondition ListControl （格式） 的 ItemSelectionCondition ListControls PropertyName 元素 ListItem 元素的元素</span><span class="sxs-lookup"><span data-stu-id="9f76a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9f76a-107">语法</span><span class="sxs-lookup"><span data-stu-id="9f76a-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9f76a-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="9f76a-108">Attributes and Elements</span></span>

<span data-ttu-id="9f76a-109">以下各节描述了特性、 子元素和父元素的`PropertyName`元素。</span><span class="sxs-lookup"><span data-stu-id="9f76a-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9f76a-110">特性</span><span class="sxs-lookup"><span data-stu-id="9f76a-110">Attributes</span></span>

<span data-ttu-id="9f76a-111">无。</span><span class="sxs-lookup"><span data-stu-id="9f76a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9f76a-112">子元素</span><span class="sxs-lookup"><span data-stu-id="9f76a-112">Child Elements</span></span>

<span data-ttu-id="9f76a-113">无。</span><span class="sxs-lookup"><span data-stu-id="9f76a-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9f76a-114">父元素</span><span class="sxs-lookup"><span data-stu-id="9f76a-114">Parent Elements</span></span>

|<span data-ttu-id="9f76a-115">元素</span><span class="sxs-lookup"><span data-stu-id="9f76a-115">Element</span></span>|<span data-ttu-id="9f76a-116">描述</span><span class="sxs-lookup"><span data-stu-id="9f76a-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9f76a-117">ItemSelectionCondition ListControl （格式） 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="9f76a-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="9f76a-118">文本值</span><span class="sxs-lookup"><span data-stu-id="9f76a-118">Text Value</span></span>

<span data-ttu-id="9f76a-119">指定显示其值的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="9f76a-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="9f76a-120">备注</span><span class="sxs-lookup"><span data-stu-id="9f76a-120">Remarks</span></span>

<span data-ttu-id="9f76a-121">如果使用此元素时，不能指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)元素定义的选择条件时。</span><span class="sxs-lookup"><span data-stu-id="9f76a-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f76a-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9f76a-122">See Also</span></span>

[<span data-ttu-id="9f76a-123">ItemSelectionCondition 为 ListIControl （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="9f76a-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="9f76a-124">ItemSelectionCondition ListControl （格式） 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="9f76a-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="9f76a-125">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="9f76a-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
