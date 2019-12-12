---
title: 视图控件的控件元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363466"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="6d28d-102">Control Element for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="6d28d-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="6d28d-103">定义可供视图使用的控件以及用于引用控件的名称。</span><span class="sxs-lookup"><span data-stu-id="6d28d-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="6d28d-104">Control 元素（Format） ViewDefinitions 元素（格式） View 元素（format） Control Control 元素 for View （format）控件元素</span><span class="sxs-lookup"><span data-stu-id="6d28d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6d28d-105">语法</span><span class="sxs-lookup"><span data-stu-id="6d28d-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6d28d-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="6d28d-106">Attributes and Elements</span></span>

<span data-ttu-id="6d28d-107">以下各节介绍了 `Control` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6d28d-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6d28d-108">属性</span><span class="sxs-lookup"><span data-stu-id="6d28d-108">Attributes</span></span>

<span data-ttu-id="6d28d-109">无。</span><span class="sxs-lookup"><span data-stu-id="6d28d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6d28d-110">子元素</span><span class="sxs-lookup"><span data-stu-id="6d28d-110">Child Elements</span></span>

|<span data-ttu-id="6d28d-111">元素</span><span class="sxs-lookup"><span data-stu-id="6d28d-111">Element</span></span>|<span data-ttu-id="6d28d-112">描述</span><span class="sxs-lookup"><span data-stu-id="6d28d-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6d28d-113">用于控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6d28d-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="6d28d-114">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="6d28d-114">Required element.</span></span><br /><br /> <span data-ttu-id="6d28d-115">指定控件的名称。</span><span class="sxs-lookup"><span data-stu-id="6d28d-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="6d28d-116">用于控件的控件的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6d28d-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="6d28d-117">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="6d28d-117">Required element.</span></span><br /><br /> <span data-ttu-id="6d28d-118">定义此视图使用的控件。</span><span class="sxs-lookup"><span data-stu-id="6d28d-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6d28d-119">父元素</span><span class="sxs-lookup"><span data-stu-id="6d28d-119">Parent Elements</span></span>

|<span data-ttu-id="6d28d-120">元素</span><span class="sxs-lookup"><span data-stu-id="6d28d-120">Element</span></span>|<span data-ttu-id="6d28d-121">描述</span><span class="sxs-lookup"><span data-stu-id="6d28d-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6d28d-122">Controls 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6d28d-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="6d28d-123">定义可供特定视图使用的视图控件。</span><span class="sxs-lookup"><span data-stu-id="6d28d-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6d28d-124">备注</span><span class="sxs-lookup"><span data-stu-id="6d28d-124">Remarks</span></span>

<span data-ttu-id="6d28d-125">此控件可由以下元素指定：</span><span class="sxs-lookup"><span data-stu-id="6d28d-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="6d28d-126">用于视图的控件的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6d28d-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="6d28d-127">用于 View 的 CustomControl 的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6d28d-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="6d28d-128">GroupBy 的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6d28d-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="6d28d-129">GroupBy 的 CustomControlName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="6d28d-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="6d28d-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6d28d-130">See Also</span></span>

[<span data-ttu-id="6d28d-131">用于控件的控件的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6d28d-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="6d28d-132">用于视图的控件的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6d28d-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="6d28d-133">用于 View 的 CustomControl 的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6d28d-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="6d28d-134">GroupBy 的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6d28d-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="6d28d-135">GroupBy 的 ExpressionBinding 的 CustomControlName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6d28d-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="6d28d-136">Controls 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6d28d-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="6d28d-137">用于控件的控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6d28d-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="6d28d-138">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="6d28d-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
