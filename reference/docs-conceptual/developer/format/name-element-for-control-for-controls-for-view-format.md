---
title: 用于控件的控件的名称元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365096"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="fa76e-102">Name Element for Control for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="fa76e-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="fa76e-103">指定控件的名称。</span><span class="sxs-lookup"><span data-stu-id="fa76e-103">Specifies the name of the control.</span></span>

<span data-ttu-id="fa76e-104">配置元素（格式） ViewDefinitions 元素（格式） View 元素（格式）控件元素（格式）控件元素 for view （format） Name 元素（用于控件）的控件元素</span><span class="sxs-lookup"><span data-stu-id="fa76e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fa76e-105">语法</span><span class="sxs-lookup"><span data-stu-id="fa76e-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fa76e-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="fa76e-106">Attributes and Elements</span></span>

<span data-ttu-id="fa76e-107">以下各节介绍了 `Name` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fa76e-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fa76e-108">属性</span><span class="sxs-lookup"><span data-stu-id="fa76e-108">Attributes</span></span>

<span data-ttu-id="fa76e-109">无。</span><span class="sxs-lookup"><span data-stu-id="fa76e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fa76e-110">子元素</span><span class="sxs-lookup"><span data-stu-id="fa76e-110">Child Elements</span></span>

<span data-ttu-id="fa76e-111">无。</span><span class="sxs-lookup"><span data-stu-id="fa76e-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fa76e-112">父元素</span><span class="sxs-lookup"><span data-stu-id="fa76e-112">Parent Elements</span></span>

|<span data-ttu-id="fa76e-113">元素</span><span class="sxs-lookup"><span data-stu-id="fa76e-113">Element</span></span>|<span data-ttu-id="fa76e-114">描述</span><span class="sxs-lookup"><span data-stu-id="fa76e-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fa76e-115">视图控件的控件元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fa76e-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="fa76e-116">定义可供视图使用的控件以及用于引用控件的名称。</span><span class="sxs-lookup"><span data-stu-id="fa76e-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fa76e-117">文本值</span><span class="sxs-lookup"><span data-stu-id="fa76e-117">Text Value</span></span>

<span data-ttu-id="fa76e-118">指定用于引用控件的名称。</span><span class="sxs-lookup"><span data-stu-id="fa76e-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="fa76e-119">备注</span><span class="sxs-lookup"><span data-stu-id="fa76e-119">Remarks</span></span>

<span data-ttu-id="fa76e-120">此处指定的名称可以用在以下元素中以引用此控件。</span><span class="sxs-lookup"><span data-stu-id="fa76e-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="fa76e-121">创建表、列表、宽控件或自定义控件视图时，可通过以下元素指定控件： [view 的 GroupBy 元素（Format）](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="fa76e-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="fa76e-122">创建可由视图使用的另一个控件时，可以通过以下元素指定此控件：用于视图的[控件的 CustomItem 的 ExpressionBinding 元素（格式）](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="fa76e-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="fa76e-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa76e-123">See Also</span></span>

[<span data-ttu-id="fa76e-124">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fa76e-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="fa76e-125">用于视图的控件的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fa76e-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="fa76e-126">视图控件的控件元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fa76e-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="fa76e-127">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="fa76e-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
