---
title: 用于 CustomControl for View （Format）的 ExpressionBinding 的 CustomControlName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364106"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="d8a8f-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="d8a8f-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="d8a8f-103">指定公共控件或视图控件的名称。</span><span class="sxs-lookup"><span data-stu-id="d8a8f-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="d8a8f-104">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="d8a8f-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="d8a8f-105">CustomEntry for view （format） CustomEntries 元素 for view （format） CustomEntries 元素的 ViewDefinitions 元素（format） View 元素（format） CustomControl 元素（format）用于 CustomItem 的表达式绑定的 CustomItem （Format） CustomControlName 元素的 CustomEntry for View （Format） ExpressionBinding 元素的元素</span><span class="sxs-lookup"><span data-stu-id="d8a8f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d8a8f-106">语法</span><span class="sxs-lookup"><span data-stu-id="d8a8f-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d8a8f-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="d8a8f-107">Attributes and Elements</span></span>

<span data-ttu-id="d8a8f-108">以下各节介绍了 `CustomControlName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d8a8f-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d8a8f-109">属性</span><span class="sxs-lookup"><span data-stu-id="d8a8f-109">Attributes</span></span>

<span data-ttu-id="d8a8f-110">无。</span><span class="sxs-lookup"><span data-stu-id="d8a8f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d8a8f-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d8a8f-111">Child Elements</span></span>

<span data-ttu-id="d8a8f-112">无。</span><span class="sxs-lookup"><span data-stu-id="d8a8f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d8a8f-113">父元素</span><span class="sxs-lookup"><span data-stu-id="d8a8f-113">Parent Elements</span></span>

|<span data-ttu-id="d8a8f-114">元素</span><span class="sxs-lookup"><span data-stu-id="d8a8f-114">Element</span></span>|<span data-ttu-id="d8a8f-115">描述</span><span class="sxs-lookup"><span data-stu-id="d8a8f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d8a8f-116">CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d8a8f-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="d8a8f-117">定义控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="d8a8f-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d8a8f-118">文本值</span><span class="sxs-lookup"><span data-stu-id="d8a8f-118">Text Value</span></span>

<span data-ttu-id="d8a8f-119">指定控件的名称。</span><span class="sxs-lookup"><span data-stu-id="d8a8f-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="d8a8f-120">备注</span><span class="sxs-lookup"><span data-stu-id="d8a8f-120">Remarks</span></span>

<span data-ttu-id="d8a8f-121">您可以创建可供格式设置文件的所有视图使用的公共控件，并可以创建可供特定视图使用的视图控件。</span><span class="sxs-lookup"><span data-stu-id="d8a8f-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="d8a8f-122">以下元素指定这些控件的名称。</span><span class="sxs-lookup"><span data-stu-id="d8a8f-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="d8a8f-123">用于控件的控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d8a8f-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="d8a8f-124">用于控件的控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d8a8f-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="d8a8f-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d8a8f-125">See Also</span></span>

[<span data-ttu-id="d8a8f-126">用于控件的控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d8a8f-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="d8a8f-127">用于控件的控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d8a8f-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="d8a8f-128">CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d8a8f-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="d8a8f-129">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="d8a8f-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
