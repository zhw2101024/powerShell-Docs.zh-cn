---
title: GroupBy （Format）的 ExpressionBinding 的 CustomControlName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368906"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a><span data-ttu-id="9ed47-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="9ed47-102">CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

<span data-ttu-id="9ed47-103">指定公共控件或视图控件的名称。</span><span class="sxs-lookup"><span data-stu-id="9ed47-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="9ed47-104">此元素在定义如何显示新的对象组时使用。</span><span class="sxs-lookup"><span data-stu-id="9ed47-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="9ed47-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）CustomControl for groupby （format） CustomItem 元素 for CustomEntry for groupby （format） ExpressionBinding 元素 for CustomItem for groupby （format） CustomControlName 元素 for groupby （Format）</span><span class="sxs-lookup"><span data-stu-id="9ed47-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format) ExpressionBinding Element for CustomItem for GroupBy (Format) CustomControlName Element for ExpressionBinding for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9ed47-106">语法</span><span class="sxs-lookup"><span data-stu-id="9ed47-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9ed47-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="9ed47-107">Attributes and Elements</span></span>

<span data-ttu-id="9ed47-108">以下各节介绍了 `CustomControlName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9ed47-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9ed47-109">属性</span><span class="sxs-lookup"><span data-stu-id="9ed47-109">Attributes</span></span>

<span data-ttu-id="9ed47-110">无。</span><span class="sxs-lookup"><span data-stu-id="9ed47-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9ed47-111">子元素</span><span class="sxs-lookup"><span data-stu-id="9ed47-111">Child Elements</span></span>

<span data-ttu-id="9ed47-112">无。</span><span class="sxs-lookup"><span data-stu-id="9ed47-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9ed47-113">父元素</span><span class="sxs-lookup"><span data-stu-id="9ed47-113">Parent Elements</span></span>

|<span data-ttu-id="9ed47-114">元素</span><span class="sxs-lookup"><span data-stu-id="9ed47-114">Element</span></span>|<span data-ttu-id="9ed47-115">描述</span><span class="sxs-lookup"><span data-stu-id="9ed47-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9ed47-116">GroupBy 的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9ed47-116">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="9ed47-117">定义控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="9ed47-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9ed47-118">文本值</span><span class="sxs-lookup"><span data-stu-id="9ed47-118">Text Value</span></span>

<span data-ttu-id="9ed47-119">指定控件的名称。</span><span class="sxs-lookup"><span data-stu-id="9ed47-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="9ed47-120">备注</span><span class="sxs-lookup"><span data-stu-id="9ed47-120">Remarks</span></span>

<span data-ttu-id="9ed47-121">您可以创建可供格式设置文件的所有视图使用的公共控件，还可以创建可供特定视图使用的视图控件。</span><span class="sxs-lookup"><span data-stu-id="9ed47-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="9ed47-122">以下元素指定这些控件的名称：</span><span class="sxs-lookup"><span data-stu-id="9ed47-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="9ed47-123">用于控件的控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9ed47-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="9ed47-124">用于控件的控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9ed47-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="9ed47-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9ed47-125">See Also</span></span>

[<span data-ttu-id="9ed47-126">用于控件的控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9ed47-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="9ed47-127">用于控件的控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9ed47-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="9ed47-128">GroupBy 的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9ed47-128">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="9ed47-129">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="9ed47-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
