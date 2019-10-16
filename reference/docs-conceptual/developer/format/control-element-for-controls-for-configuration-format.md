---
title: 用于配置控件的控件元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369006"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="d3377-102">Control Element for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="d3377-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="d3377-103">定义一个公共控件，该控件可供格式设置文件的所有视图和用于引用控件的名称使用。</span><span class="sxs-lookup"><span data-stu-id="d3377-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="d3377-104">配置元素的配置元素（格式）控件元素的配置（format）控件元素的元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d3377-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d3377-105">语法</span><span class="sxs-lookup"><span data-stu-id="d3377-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d3377-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="d3377-106">Attributes and Elements</span></span>

<span data-ttu-id="d3377-107">以下各节介绍了 `Control` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d3377-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="d3377-108">必须仅指定每个子元素中的一个。</span><span class="sxs-lookup"><span data-stu-id="d3377-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d3377-109">属性</span><span class="sxs-lookup"><span data-stu-id="d3377-109">Attributes</span></span>

<span data-ttu-id="d3377-110">无。</span><span class="sxs-lookup"><span data-stu-id="d3377-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d3377-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d3377-111">Child Elements</span></span>

|<span data-ttu-id="d3377-112">元素</span><span class="sxs-lookup"><span data-stu-id="d3377-112">Element</span></span>|<span data-ttu-id="d3377-113">描述</span><span class="sxs-lookup"><span data-stu-id="d3377-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d3377-114">用于控件的控件的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d3377-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="d3377-115">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="d3377-115">Required element.</span></span><br /><br /> <span data-ttu-id="d3377-116">定义控件。</span><span class="sxs-lookup"><span data-stu-id="d3377-116">Defines the control.</span></span>|
|[<span data-ttu-id="d3377-117">用于控件配置的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d3377-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="d3377-118">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="d3377-118">Required element.</span></span><br /><br /> <span data-ttu-id="d3377-119">指定用于引用控件的名称。</span><span class="sxs-lookup"><span data-stu-id="d3377-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d3377-120">父元素</span><span class="sxs-lookup"><span data-stu-id="d3377-120">Parent Elements</span></span>

|<span data-ttu-id="d3377-121">元素</span><span class="sxs-lookup"><span data-stu-id="d3377-121">Element</span></span>|<span data-ttu-id="d3377-122">描述</span><span class="sxs-lookup"><span data-stu-id="d3377-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d3377-123">Control 的 Controls 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d3377-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="d3377-124">定义可由格式设置文件的所有视图或其他控件使用的公共控件。</span><span class="sxs-lookup"><span data-stu-id="d3377-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d3377-125">备注</span><span class="sxs-lookup"><span data-stu-id="d3377-125">Remarks</span></span>

<span data-ttu-id="d3377-126">可以在以下元素中引用为此控件指定的名称：</span><span class="sxs-lookup"><span data-stu-id="d3377-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="d3377-127">CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d3377-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="d3377-128">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d3377-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="d3377-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d3377-129">See Also</span></span>

[<span data-ttu-id="d3377-130">Control 的 Controls 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d3377-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="d3377-131">用于控件配置的 CustomControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d3377-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="d3377-132">CustomItem 的 ExpressionBinding 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d3377-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="d3377-133">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d3377-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="d3377-134">用于控件的控件的名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d3377-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="d3377-135">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="d3377-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
