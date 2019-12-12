---
title: 用于配置的控件（格式）的 ExpressionBinding 的 CustomControlName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5242935-2782-4d23-84f5-2446b2b7ba83
caps.latest.revision: 8
ms.openlocfilehash: c9abd9f22907b87323c16d603a9f75bb3d375a03
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364116"
---
# <a name="customcontrolname-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="6c107-102">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="6c107-102">CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="6c107-103">指定公共控件的名称。</span><span class="sxs-lookup"><span data-stu-id="6c107-103">Specifies the name of a common control.</span></span> <span data-ttu-id="6c107-104">此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。</span><span class="sxs-lookup"><span data-stu-id="6c107-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="6c107-105">Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format） CustomEntry 元素 for CustomControl for CustomItem 元素 for CustomEntry for 元素 for for 元素 for for ExpressionBinding for control for control for control CustomItem用于配置控件的 ExpressionBinding 的元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6c107-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) CustomControlName Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6c107-106">语法</span><span class="sxs-lookup"><span data-stu-id="6c107-106">Syntax</span></span>

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6c107-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="6c107-107">Attributes and Elements</span></span>

<span data-ttu-id="6c107-108">以下各节介绍了 `CustomControlName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6c107-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6c107-109">属性</span><span class="sxs-lookup"><span data-stu-id="6c107-109">Attributes</span></span>

<span data-ttu-id="6c107-110">无。</span><span class="sxs-lookup"><span data-stu-id="6c107-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6c107-111">子元素</span><span class="sxs-lookup"><span data-stu-id="6c107-111">Child Elements</span></span>

<span data-ttu-id="6c107-112">无。</span><span class="sxs-lookup"><span data-stu-id="6c107-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6c107-113">父元素</span><span class="sxs-lookup"><span data-stu-id="6c107-113">Parent Elements</span></span>

|<span data-ttu-id="6c107-114">元素</span><span class="sxs-lookup"><span data-stu-id="6c107-114">Element</span></span>|<span data-ttu-id="6c107-115">描述</span><span class="sxs-lookup"><span data-stu-id="6c107-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6c107-116">用于配置的控件的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6c107-116">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="6c107-117">定义控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="6c107-117">Defines the data that is displayed by the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6c107-118">文本值</span><span class="sxs-lookup"><span data-stu-id="6c107-118">Text Value</span></span>

<span data-ttu-id="6c107-119">指定控件的名称。</span><span class="sxs-lookup"><span data-stu-id="6c107-119">Specify the name of the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="6c107-120">备注</span><span class="sxs-lookup"><span data-stu-id="6c107-120">Remarks</span></span>

<span data-ttu-id="6c107-121">您可以创建可供格式设置文件的所有视图使用的公共控件，还可以创建可供特定视图使用的视图控件。</span><span class="sxs-lookup"><span data-stu-id="6c107-121">You can create common controls that can be used by all the views of a formatting file, and you can create view controls that can be used by a specific view.</span></span> <span data-ttu-id="6c107-122">以下元素指定这些控件的名称：</span><span class="sxs-lookup"><span data-stu-id="6c107-122">The following elements specify the names of these controls:</span></span>

- [<span data-ttu-id="6c107-123">用于控件的控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6c107-123">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

- [<span data-ttu-id="6c107-124">用于控件的控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6c107-124">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="6c107-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6c107-125">See Also</span></span>

[<span data-ttu-id="6c107-126">用于控件的控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6c107-126">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="6c107-127">用于控件的控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6c107-127">Name Element for Control for Controls for View (Format)</span></span>](./name-element-for-control-for-controls-for-view-format.md)

[<span data-ttu-id="6c107-128">用于配置的控件的 CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6c107-128">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="6c107-129">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="6c107-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
