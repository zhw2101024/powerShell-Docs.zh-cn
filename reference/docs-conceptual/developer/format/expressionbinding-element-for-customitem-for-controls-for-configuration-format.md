---
title: 用于配置的控件（格式）的 CustomItem 的 ExpressionBinding 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6649d07-4762-4602-9b4b-d9e2e9e63312
caps.latest.revision: 13
ms.openlocfilehash: 531ff447f8407a737131a38351d7e4c6e7da90fb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363186"
---
# <a name="expressionbinding-element-for-customitem-for-controls-for-configuration-format"></a><span data-ttu-id="46c03-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="46c03-102">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

<span data-ttu-id="46c03-103">定义控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="46c03-103">Defines the data that is displayed by the control.</span></span> <span data-ttu-id="46c03-104">此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。</span><span class="sxs-lookup"><span data-stu-id="46c03-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="46c03-105">Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format） CustomEntry 元素 for CustomControl for CustomItem 元素 for CustomEntry for 元素 for for ExpressionBinding for configuration CustomItem 元素 for for control</span><span class="sxs-lookup"><span data-stu-id="46c03-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="46c03-106">语法</span><span class="sxs-lookup"><span data-stu-id="46c03-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="46c03-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="46c03-107">Attributes and Elements</span></span>

<span data-ttu-id="46c03-108">以下各节介绍了 `ExpressionBinding` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="46c03-108">The following sections describe attributes, child elements, and the parent element of the `ExpressionBinding` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="46c03-109">属性</span><span class="sxs-lookup"><span data-stu-id="46c03-109">Attributes</span></span>

<span data-ttu-id="46c03-110">无。</span><span class="sxs-lookup"><span data-stu-id="46c03-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="46c03-111">子元素</span><span class="sxs-lookup"><span data-stu-id="46c03-111">Child Elements</span></span>

|<span data-ttu-id="46c03-112">元素</span><span class="sxs-lookup"><span data-stu-id="46c03-112">Element</span></span>|<span data-ttu-id="46c03-113">描述</span><span class="sxs-lookup"><span data-stu-id="46c03-113">Description</span></span>|
|-------------|-----------------|
|`CustomControl Element`|<span data-ttu-id="46c03-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="46c03-114">Optional element.</span></span><br /><br /> <span data-ttu-id="46c03-115">定义此控件使用的控件。</span><span class="sxs-lookup"><span data-stu-id="46c03-115">Defines a control that is used by this control.</span></span>|
|[<span data-ttu-id="46c03-116">用于配置的控件的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="46c03-116">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="46c03-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="46c03-117">Optional element.</span></span><br /><br /> <span data-ttu-id="46c03-118">指定公共控件或视图控件的名称。</span><span class="sxs-lookup"><span data-stu-id="46c03-118">Specifies the name of a common control or a view control.</span></span>|
|[<span data-ttu-id="46c03-119">用于配置的控件的 ExpressionBinding 的 EnumerateCollection 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="46c03-119">EnumerateCollection Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./enumeratecollection-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="46c03-120">可选元素。</span><span class="sxs-lookup"><span data-stu-id="46c03-120">Optional element.</span></span><br /><br /> <span data-ttu-id="46c03-121">指定控件所显示的集合元素。</span><span class="sxs-lookup"><span data-stu-id="46c03-121">Specified that the elements of collections are displayed by the control.</span></span>|
|[<span data-ttu-id="46c03-122">用于配置的控件的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="46c03-122">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="46c03-123">可选元素。</span><span class="sxs-lookup"><span data-stu-id="46c03-123">Optional element.</span></span><br /><br /> <span data-ttu-id="46c03-124">定义要使用此公共控件必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="46c03-124">Defines the condition that must exist for this common control to be used.</span></span>|
|[<span data-ttu-id="46c03-125">用于配置的控件的 ExpressionBinding 的 PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="46c03-125">PropertyName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./propertyname-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="46c03-126">可选元素。</span><span class="sxs-lookup"><span data-stu-id="46c03-126">Optional element.</span></span><br /><br /> <span data-ttu-id="46c03-127">指定 .NET 属性，其值由公共控件显示。</span><span class="sxs-lookup"><span data-stu-id="46c03-127">Specifies the .NET property whose value is displayed by the common control.</span></span>|
|[<span data-ttu-id="46c03-128">用于配置的控件的 ExpressionBinding 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="46c03-128">ScriptBlock Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="46c03-129">可选元素。</span><span class="sxs-lookup"><span data-stu-id="46c03-129">Optional element.</span></span><br /><br /> <span data-ttu-id="46c03-130">指定其值由公共控件显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="46c03-130">Specifies the script whose value is displayed by the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="46c03-131">父元素</span><span class="sxs-lookup"><span data-stu-id="46c03-131">Parent Elements</span></span>

|<span data-ttu-id="46c03-132">元素</span><span class="sxs-lookup"><span data-stu-id="46c03-132">Element</span></span>|<span data-ttu-id="46c03-133">描述</span><span class="sxs-lookup"><span data-stu-id="46c03-133">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="46c03-134">用于配置控件的 CustomEntry 的 CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="46c03-134">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="46c03-135">定义自定义控件视图显示的数据及其显示方式。</span><span class="sxs-lookup"><span data-stu-id="46c03-135">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="46c03-136">备注</span><span class="sxs-lookup"><span data-stu-id="46c03-136">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="46c03-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="46c03-137">See Also</span></span>

[<span data-ttu-id="46c03-138">用于配置控件的 CustomEntry 的 CustomItem 元素</span><span class="sxs-lookup"><span data-stu-id="46c03-138">CustomItem Element for CustomEntry for Controls for Configuration</span></span>](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="46c03-139">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="46c03-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
