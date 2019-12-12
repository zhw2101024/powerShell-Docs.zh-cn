---
title: 用于 CustomControl for View （Format）的 CustomItem 的 ExpressionBinding 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f5ebea5-ee9c-4b90-a116-12a1daa28fc7
caps.latest.revision: 7
ms.openlocfilehash: 226bbea1d7613ad3099e05e8caa9817ff16c1f42
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363146"
---
# <a name="expressionbinding-element-for-customitem-for-customcontrol-for-view-format"></a><span data-ttu-id="27a28-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="27a28-102">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

<span data-ttu-id="27a28-103">定义控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="27a28-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="27a28-104">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="27a28-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="27a28-105">Configuration Element （Format） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素 for View （format） CustomEntries 元素 for CustomControl for CustomEntry for CustomEntries for View （Format） CustomControl 元素 for view （Format） CustomItem 元素 for CustomEntry for CustomControl for view （Format） ExpressionBinding 元素 for CustomItem for CustomControl for View （Format）</span><span class="sxs-lookup"><span data-stu-id="27a28-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="27a28-106">语法</span><span class="sxs-lookup"><span data-stu-id="27a28-106">Syntax</span></span>

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="27a28-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="27a28-107">Attributes and Elements</span></span>

<span data-ttu-id="27a28-108">以下各节介绍了 `ExpressionBinding` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="27a28-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="27a28-109">属性</span><span class="sxs-lookup"><span data-stu-id="27a28-109">Attributes</span></span>

<span data-ttu-id="27a28-110">无。</span><span class="sxs-lookup"><span data-stu-id="27a28-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="27a28-111">子元素</span><span class="sxs-lookup"><span data-stu-id="27a28-111">Child Elements</span></span>

|<span data-ttu-id="27a28-112">元素</span><span class="sxs-lookup"><span data-stu-id="27a28-112">Element</span></span>|<span data-ttu-id="27a28-113">描述</span><span class="sxs-lookup"><span data-stu-id="27a28-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="27a28-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="27a28-114">Optional element.</span></span><br /><br /> <span data-ttu-id="27a28-115">定义此控件使用的控件。</span><span class="sxs-lookup"><span data-stu-id="27a28-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="27a28-116">用于 View 的 CustomControl 的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="27a28-116">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="27a28-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="27a28-117">Optional element.</span></span><br /><br /> <span data-ttu-id="27a28-118">指定公共控件或视图控件的名称。</span><span class="sxs-lookup"><span data-stu-id="27a28-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="27a28-119">用于 View 的 CustomControl 的 ExpressionBinding 的 EnumerateCollection 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="27a28-119">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="27a28-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="27a28-120">Optional element.</span></span><br /><br /> <span data-ttu-id="27a28-121">指定显示集合的元素。</span><span class="sxs-lookup"><span data-stu-id="27a28-121">Specified that the elements of collections are displayed.</span></span>|
|[<span data-ttu-id="27a28-122">用于 View 的 CustomControl 的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="27a28-122">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)|<span data-ttu-id="27a28-123">可选元素。</span><span class="sxs-lookup"><span data-stu-id="27a28-123">Optional element.</span></span><br /><br /> <span data-ttu-id="27a28-124">定义要使用此控件必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="27a28-124">Defines the condition that must exist for this control to be used.</span></span>|
|[<span data-ttu-id="27a28-125">View 的 ExpressionBinding for CustomControl 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="27a28-125">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="27a28-126">可选元素。</span><span class="sxs-lookup"><span data-stu-id="27a28-126">Optional element.</span></span><br /><br /> <span data-ttu-id="27a28-127">指定其值由控件显示的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="27a28-127">Specifies the .NET property whose value is displayed by the control.</span></span>|
|[<span data-ttu-id="27a28-128">用于 View 的 ExpressionBinding for CustomCustomControl 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="27a28-128">ScriptBlock Element for ExpressionBinding for CustomCustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)|<span data-ttu-id="27a28-129">可选元素。</span><span class="sxs-lookup"><span data-stu-id="27a28-129">Optional element.</span></span><br /><br /> <span data-ttu-id="27a28-130">指定其值由控件显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="27a28-130">Specifies the script whose value is displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="27a28-131">父元素</span><span class="sxs-lookup"><span data-stu-id="27a28-131">Parent Elements</span></span>

|<span data-ttu-id="27a28-132">元素</span><span class="sxs-lookup"><span data-stu-id="27a28-132">Element</span></span>|<span data-ttu-id="27a28-133">描述</span><span class="sxs-lookup"><span data-stu-id="27a28-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="27a28-134">用于 View 的 CustomControl 的 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="27a28-134">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="27a28-135">定义自定义控件视图显示的数据及其显示方式。</span><span class="sxs-lookup"><span data-stu-id="27a28-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="27a28-136">备注</span><span class="sxs-lookup"><span data-stu-id="27a28-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="27a28-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="27a28-137">See Also</span></span>

[<span data-ttu-id="27a28-138">用于 View 的 CustomControl 的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="27a28-138">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="27a28-139">用于 View 的 CustomControl 的 ExpressionBinding 的 EnumerateCollection 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="27a28-139">EnumerateCollection Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="27a28-140">用于 View 的 CustomControl 的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="27a28-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

[<span data-ttu-id="27a28-141">View 的 ExpressionBinding for CustomControl 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="27a28-141">PropertyName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./propertyname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="27a28-142">用于 View 的 ExpressionBinding for CustomControl 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="27a28-142">ScriptBlock Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="27a28-143">用于 View 的 CustomControl 的 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="27a28-143">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="27a28-144">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="27a28-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
