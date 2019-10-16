---
title: 用于视图（格式）的 ExpressionBinding 的 CustomControlName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4b6ee11e-9086-41d2-afd3-42fb9f24da69
caps.latest.revision: 7
ms.openlocfilehash: bf1d57447f9018f1535af14466427aaeabc048f3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369146"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-view-format"></a><span data-ttu-id="1f359-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="1f359-102">CustomControlName Element for ExpressionBinding for Controls for View (Format)</span></span>

<span data-ttu-id="1f359-103">指定公共控件或视图控件的名称。</span><span class="sxs-lookup"><span data-stu-id="1f359-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="1f359-104">定义可由视图使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="1f359-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="1f359-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 元素（format） Control 元素 for View （format） CustomControl 元素的控件元素，用于控件的 View （format） CustomEntries 元素CustomControl for View （Format） CustomEntry 元素 for CustomEntries for view （format） CustomItem 元素 for CustomEntry for view （format）元素 for ExpressionBinding for view （format）View 的 ExpressionBindine 的元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1f359-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format) ExpressionBinding Element for CustomItem for Controls for View (Format) CustomControlName Element for ExpressionBindine for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1f359-106">语法</span><span class="sxs-lookup"><span data-stu-id="1f359-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1f359-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="1f359-107">Attributes and Elements</span></span>

<span data-ttu-id="1f359-108">以下各节介绍了 `CustomControlName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1f359-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1f359-109">属性</span><span class="sxs-lookup"><span data-stu-id="1f359-109">Attributes</span></span>

<span data-ttu-id="1f359-110">无。</span><span class="sxs-lookup"><span data-stu-id="1f359-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1f359-111">子元素</span><span class="sxs-lookup"><span data-stu-id="1f359-111">Child Elements</span></span>

<span data-ttu-id="1f359-112">无。</span><span class="sxs-lookup"><span data-stu-id="1f359-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1f359-113">父元素</span><span class="sxs-lookup"><span data-stu-id="1f359-113">Parent Elements</span></span>

|<span data-ttu-id="1f359-114">元素</span><span class="sxs-lookup"><span data-stu-id="1f359-114">Element</span></span>|<span data-ttu-id="1f359-115">描述</span><span class="sxs-lookup"><span data-stu-id="1f359-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1f359-116">用于视图的控件的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1f359-116">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="1f359-117">定义控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="1f359-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1f359-118">文本值</span><span class="sxs-lookup"><span data-stu-id="1f359-118">Text Value</span></span>

<span data-ttu-id="1f359-119">指定控件的名称。</span><span class="sxs-lookup"><span data-stu-id="1f359-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="1f359-120">备注</span><span class="sxs-lookup"><span data-stu-id="1f359-120">Remarks</span></span>

<span data-ttu-id="1f359-121">您可以创建可供格式设置文件的所有视图使用的公共控件，还可以创建可供特定视图使用的视图控件。</span><span class="sxs-lookup"><span data-stu-id="1f359-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="1f359-122">以下元素指定这些控件的名称：</span><span class="sxs-lookup"><span data-stu-id="1f359-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="1f359-123">用于控件的控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1f359-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="1f359-124">用于控件的控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1f359-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="1f359-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1f359-125">See Also</span></span>

[<span data-ttu-id="1f359-126">用于控件的控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1f359-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="1f359-127">用于控件的控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1f359-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="1f359-128">用于视图的控件的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1f359-128">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="1f359-129">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="1f359-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
