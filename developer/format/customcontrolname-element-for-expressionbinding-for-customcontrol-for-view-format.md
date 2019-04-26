---
title: 为视图 （格式） 的 CustomControl ExpressionBinding 的 CustomControlName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea821e8b-4d65-4263-b7e4-6aeca9f534c2
caps.latest.revision: 9
ms.openlocfilehash: b44ced75bbaac7c0744f347bdc97f87365b8fe39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066611"
---
# <a name="customcontrolname-element-for-expressionbinding-for-customcontrol-for-view-format"></a><span data-ttu-id="96c17-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="96c17-102">CustomControlName Element for ExpressionBinding for CustomControl for View (Format)</span></span>

<span data-ttu-id="96c17-103">指定公共控件或视图控件的名称。</span><span class="sxs-lookup"><span data-stu-id="96c17-103">Specifies the name of a common control or a view control.</span></span> <span data-ttu-id="96c17-104">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="96c17-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="96c17-105">视图 （格式） 的视图 （格式） 的视图 （格式） CustomItem CustomEntries CustomEntry 元素 CustomControl CustomEntries 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素CustomEntry CustomItem （格式） CustomControlName 元素 CustomItem （格式） 的表达式绑定的视图 （格式） ExpressionBinding 元素的元素</span><span class="sxs-lookup"><span data-stu-id="96c17-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem (Format) CustomControlName Element for Expression Binding for CustomItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="96c17-106">语法</span><span class="sxs-lookup"><span data-stu-id="96c17-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="96c17-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="96c17-107">Attributes and Elements</span></span>

<span data-ttu-id="96c17-108">以下各节描述了特性、 子元素和父元素的`CustomControlName`元素。</span><span class="sxs-lookup"><span data-stu-id="96c17-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="96c17-109">属性</span><span class="sxs-lookup"><span data-stu-id="96c17-109">Attributes</span></span>

<span data-ttu-id="96c17-110">无。</span><span class="sxs-lookup"><span data-stu-id="96c17-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="96c17-111">子元素</span><span class="sxs-lookup"><span data-stu-id="96c17-111">Child Elements</span></span>

<span data-ttu-id="96c17-112">无。</span><span class="sxs-lookup"><span data-stu-id="96c17-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="96c17-113">父元素</span><span class="sxs-lookup"><span data-stu-id="96c17-113">Parent Elements</span></span>

|<span data-ttu-id="96c17-114">元素</span><span class="sxs-lookup"><span data-stu-id="96c17-114">Element</span></span>|<span data-ttu-id="96c17-115">说明</span><span class="sxs-lookup"><span data-stu-id="96c17-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="96c17-116">ExpressionBinding CustomItem （格式） 的元素</span><span class="sxs-lookup"><span data-stu-id="96c17-116">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="96c17-117">定义由控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="96c17-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="96c17-118">文本值</span><span class="sxs-lookup"><span data-stu-id="96c17-118">Text Value</span></span>

<span data-ttu-id="96c17-119">指定控件的名称。</span><span class="sxs-lookup"><span data-stu-id="96c17-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="96c17-120">备注</span><span class="sxs-lookup"><span data-stu-id="96c17-120">Remarks</span></span>

<span data-ttu-id="96c17-121">可以创建可由格式设置文件的所有视图的公共控件和您可以创建可都由特定视图的视图控件。</span><span class="sxs-lookup"><span data-stu-id="96c17-121">You can create common controls that can be used by all the views of a formatting file and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="96c17-122">由以下元素指定这些控件的名称。</span><span class="sxs-lookup"><span data-stu-id="96c17-122">The names of these controls are specified by the following elements.</span></span>

- [<span data-ttu-id="96c17-123">配置 （格式） 的控件的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="96c17-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="96c17-124">控件的视图 （格式） 的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="96c17-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="96c17-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="96c17-125">See Also</span></span>

[<span data-ttu-id="96c17-126">配置 （格式） 的控件的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="96c17-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="96c17-127">控件的视图 （格式） 的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="96c17-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="96c17-128">ExpressionBinding CustomItem （格式） 的元素</span><span class="sxs-lookup"><span data-stu-id="96c17-128">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="96c17-129">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="96c17-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
