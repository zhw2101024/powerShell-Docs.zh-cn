---
title: ListControl 的 ItemSelectionCondition 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5e707ae-3c84-4ceb-ba31-56b3ffde6d6c
caps.latest.revision: 7
ms.openlocfilehash: b15e26e18126f69eee7c3a857f9a461d4bdf5848
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362386"
---
# <a name="propertyname-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="11c2c-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="11c2c-102">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="11c2c-103">指定触发条件的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="11c2c-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="11c2c-104">如果该属性存在，或其计算结果为 `true`，则满足条件，并使用视图。</span><span class="sxs-lookup"><span data-stu-id="11c2c-104">When this property is present or when it evaluates to `true`, the condition is met, and the view is used.</span></span> <span data-ttu-id="11c2c-105">定义列表视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="11c2c-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="11c2c-106">Configuration 元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（format） ListEntries 元素（format） ListEntry 元素 for ListControl （format）ListControls 的 ListItems for ListControl （Format） ItemSelectionCondition 元素的元素 for ItemSelectionCondition for ListControl 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="11c2c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControls PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="11c2c-107">语法</span><span class="sxs-lookup"><span data-stu-id="11c2c-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="11c2c-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="11c2c-108">Attributes and Elements</span></span>

<span data-ttu-id="11c2c-109">以下各节介绍了 `PropertyName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="11c2c-109">The following sections describe attributes, child elements, and the parent elements of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="11c2c-110">属性</span><span class="sxs-lookup"><span data-stu-id="11c2c-110">Attributes</span></span>

<span data-ttu-id="11c2c-111">无。</span><span class="sxs-lookup"><span data-stu-id="11c2c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="11c2c-112">子元素</span><span class="sxs-lookup"><span data-stu-id="11c2c-112">Child Elements</span></span>

<span data-ttu-id="11c2c-113">无。</span><span class="sxs-lookup"><span data-stu-id="11c2c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="11c2c-114">父元素</span><span class="sxs-lookup"><span data-stu-id="11c2c-114">Parent Elements</span></span>

|<span data-ttu-id="11c2c-115">元素</span><span class="sxs-lookup"><span data-stu-id="11c2c-115">Element</span></span>|<span data-ttu-id="11c2c-116">描述</span><span class="sxs-lookup"><span data-stu-id="11c2c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11c2c-117">ListControl 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="11c2c-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)||

## <a name="text-value"></a><span data-ttu-id="11c2c-118">文本值</span><span class="sxs-lookup"><span data-stu-id="11c2c-118">Text Value</span></span>

<span data-ttu-id="11c2c-119">指定显示其值的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="11c2c-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="11c2c-120">备注</span><span class="sxs-lookup"><span data-stu-id="11c2c-120">Remarks</span></span>

<span data-ttu-id="11c2c-121">如果使用此元素，则在定义选择条件时，不能指定[ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="11c2c-121">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="11c2c-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="11c2c-122">See Also</span></span>

[<span data-ttu-id="11c2c-123">ListIControl 的 ItemSelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="11c2c-123">ScriptBlock Element for ItemSelectionCondition for ListIControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="11c2c-124">ListControl 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="11c2c-124">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="11c2c-125">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="11c2c-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
