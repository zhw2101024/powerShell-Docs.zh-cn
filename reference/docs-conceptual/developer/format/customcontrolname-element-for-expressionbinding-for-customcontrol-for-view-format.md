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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364106"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="9cb2c-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="9cb2c-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="9cb2c-103">指定公共控件或视图控件的名称。</span><span class="sxs-lookup"><span data-stu-id="9cb2c-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="9cb2c-104">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="9cb2c-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="9cb2c-105">CustomEntry for view （format） CustomEntries 元素 for view （format） CustomEntries 元素的 ViewDefinitions 元素（format） View 元素（format） CustomControl 元素（format）用于 CustomItem 的表达式绑定的 CustomItem （Format） CustomControlName 元素的 CustomEntry for View （Format） ExpressionBinding 元素的元素</span><span class="sxs-lookup"><span data-stu-id="9cb2c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9cb2c-106">语法</span><span class="sxs-lookup"><span data-stu-id="9cb2c-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9cb2c-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="9cb2c-107">Attributes and Elements</span></span>

<span data-ttu-id="9cb2c-108">以下各节介绍了 `CustomControlName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9cb2c-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9cb2c-109">属性</span><span class="sxs-lookup"><span data-stu-id="9cb2c-109">Attributes</span></span>

<span data-ttu-id="9cb2c-110">无。</span><span class="sxs-lookup"><span data-stu-id="9cb2c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9cb2c-111">子元素</span><span class="sxs-lookup"><span data-stu-id="9cb2c-111">Child Elements</span></span>

<span data-ttu-id="9cb2c-112">无。</span><span class="sxs-lookup"><span data-stu-id="9cb2c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9cb2c-113">父元素</span><span class="sxs-lookup"><span data-stu-id="9cb2c-113">Parent Elements</span></span>

|<span data-ttu-id="9cb2c-114">元素</span><span class="sxs-lookup"><span data-stu-id="9cb2c-114">Element</span></span>|<span data-ttu-id="9cb2c-115">描述</span><span class="sxs-lookup"><span data-stu-id="9cb2c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9cb2c-116">CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9cb2c-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="9cb2c-117">定义控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="9cb2c-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9cb2c-118">文本值</span><span class="sxs-lookup"><span data-stu-id="9cb2c-118">Text Value</span></span>

<span data-ttu-id="9cb2c-119">指定控件的名称。</span><span class="sxs-lookup"><span data-stu-id="9cb2c-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="9cb2c-120">备注</span><span class="sxs-lookup"><span data-stu-id="9cb2c-120">Remarks</span></span>

<span data-ttu-id="9cb2c-121">您可以创建可供格式设置文件的所有视图使用的公共控件，并可以创建可供特定视图使用的视图控件。</span><span class="sxs-lookup"><span data-stu-id="9cb2c-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="9cb2c-122">以下元素指定这些控件的名称。</span><span class="sxs-lookup"><span data-stu-id="9cb2c-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="9cb2c-123">用于控件的控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9cb2c-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="9cb2c-124">用于控件的控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9cb2c-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="9cb2c-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9cb2c-125">See Also</span></span>

[<span data-ttu-id="9cb2c-126">用于控件的控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9cb2c-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="9cb2c-127">用于控件的控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9cb2c-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="9cb2c-128">CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9cb2c-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="9cb2c-129">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="9cb2c-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
