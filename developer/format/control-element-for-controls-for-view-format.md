---
title: 控件元素的控件的视图 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fd53f55-698d-4df5-bb9a-fe28dc3193e1
caps.latest.revision: 11
ms.openlocfilehash: df568ccb36a2646b983622cdf95718dd5cac62c3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853723"
---
# <a name="control-element-for-controls-for-view--format"></a><span data-ttu-id="501ba-102">Control Element for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="501ba-102">Control Element for Controls for View  (Format)</span></span>

<span data-ttu-id="501ba-103">定义可由该视图和用于引用该控件的名称的控件。</span><span class="sxs-lookup"><span data-stu-id="501ba-103">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>

<span data-ttu-id="501ba-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 控制元素 （格式） 控件元素的控件的视图 （格式）</span><span class="sxs-lookup"><span data-stu-id="501ba-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="501ba-105">语法</span><span class="sxs-lookup"><span data-stu-id="501ba-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="501ba-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="501ba-106">Attributes and Elements</span></span>

<span data-ttu-id="501ba-107">以下各节描述了特性、 子元素和父元素的`Control`元素。</span><span class="sxs-lookup"><span data-stu-id="501ba-107">The following sections describe the attributes, child elements, and the parent element of the `Control` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="501ba-108">特性</span><span class="sxs-lookup"><span data-stu-id="501ba-108">Attributes</span></span>

<span data-ttu-id="501ba-109">无。</span><span class="sxs-lookup"><span data-stu-id="501ba-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="501ba-110">子元素</span><span class="sxs-lookup"><span data-stu-id="501ba-110">Child Elements</span></span>

|<span data-ttu-id="501ba-111">元素</span><span class="sxs-lookup"><span data-stu-id="501ba-111">Element</span></span>|<span data-ttu-id="501ba-112">描述</span><span class="sxs-lookup"><span data-stu-id="501ba-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="501ba-113">控件的视图 （格式） 的名称元素</span><span class="sxs-lookup"><span data-stu-id="501ba-113">Name Element for Control for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="501ba-114">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="501ba-114">Required element.</span></span><br /><br /> <span data-ttu-id="501ba-115">指定控件的名称。</span><span class="sxs-lookup"><span data-stu-id="501ba-115">Specifies the name of the control.</span></span>|
|[<span data-ttu-id="501ba-116">控件的视图 （格式） 的控件的 CustomControl 元素</span><span class="sxs-lookup"><span data-stu-id="501ba-116">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)|<span data-ttu-id="501ba-117">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="501ba-117">Required element.</span></span><br /><br /> <span data-ttu-id="501ba-118">定义此视图使用的控件。</span><span class="sxs-lookup"><span data-stu-id="501ba-118">Defines the control used by this view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="501ba-119">父元素</span><span class="sxs-lookup"><span data-stu-id="501ba-119">Parent Elements</span></span>

|<span data-ttu-id="501ba-120">元素</span><span class="sxs-lookup"><span data-stu-id="501ba-120">Element</span></span>|<span data-ttu-id="501ba-121">描述</span><span class="sxs-lookup"><span data-stu-id="501ba-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="501ba-122">控件元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="501ba-122">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="501ba-123">定义可由特定视图的视图控件。</span><span class="sxs-lookup"><span data-stu-id="501ba-123">Defines the view controls that can be used by a specific view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="501ba-124">备注</span><span class="sxs-lookup"><span data-stu-id="501ba-124">Remarks</span></span>

<span data-ttu-id="501ba-125">此控件可以指定由以下元素：</span><span class="sxs-lookup"><span data-stu-id="501ba-125">This control can be specified by the following elements:</span></span>

- [<span data-ttu-id="501ba-126">ExpressionBinding 的 Controls 的视图 （格式） 的 CustomControlName 元素</span><span class="sxs-lookup"><span data-stu-id="501ba-126">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

- [<span data-ttu-id="501ba-127">为视图 （格式） 的 CustomControl ExpressionBinding 的 CustomControlName 元素</span><span class="sxs-lookup"><span data-stu-id="501ba-127">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

- [<span data-ttu-id="501ba-128">GroupBy （格式） 的 ExpressionBinding 的 CustomControlName 元素</span><span class="sxs-lookup"><span data-stu-id="501ba-128">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

- [<span data-ttu-id="501ba-129">GroupBy （格式） 的 CustomControlName 元素</span><span class="sxs-lookup"><span data-stu-id="501ba-129">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="501ba-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="501ba-130">See Also</span></span>

[<span data-ttu-id="501ba-131">控件的视图 （格式） 的控件的 CustomControl 元素</span><span class="sxs-lookup"><span data-stu-id="501ba-131">CustomControl Element for Control for Controls for View (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="501ba-132">ExpressionBinding 的 Controls 的视图 （格式） 的 CustomControlName 元素</span><span class="sxs-lookup"><span data-stu-id="501ba-132">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-controls-for-view-format.md)

[<span data-ttu-id="501ba-133">为视图 （格式） 的 CustomControl ExpressionBinding 的 CustomControlName 元素</span><span class="sxs-lookup"><span data-stu-id="501ba-133">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format.md)

[<span data-ttu-id="501ba-134">GroupBy （格式） 的 ExpressionBinding 的 CustomControlName 元素</span><span class="sxs-lookup"><span data-stu-id="501ba-134">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="501ba-135">GroupBy （格式） 的 ExpressionBinding 的 CustomControlName 元素</span><span class="sxs-lookup"><span data-stu-id="501ba-135">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[<span data-ttu-id="501ba-136">控件元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="501ba-136">Controls Element (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="501ba-137">控件的视图 （格式） 的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="501ba-137">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="501ba-138">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="501ba-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
