---
title: 配置元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856323"
---
# <a name="configuration-element-format"></a><span data-ttu-id="e9dcd-102">Configuration Element (Format)</span><span class="sxs-lookup"><span data-stu-id="e9dcd-102">Configuration Element (Format)</span></span>

<span data-ttu-id="e9dcd-103">表示格式设置文件的顶级元素。</span><span class="sxs-lookup"><span data-stu-id="e9dcd-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="e9dcd-104">配置元素</span><span class="sxs-lookup"><span data-stu-id="e9dcd-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="e9dcd-105">语法</span><span class="sxs-lookup"><span data-stu-id="e9dcd-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="e9dcd-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="e9dcd-106">Attributes and Elements</span></span>

<span data-ttu-id="e9dcd-107">以下各节描述了特性、 子元素和父元素的`Configuration`元素。</span><span class="sxs-lookup"><span data-stu-id="e9dcd-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="e9dcd-108">此元素必须为每个格式设置文件的根元素和此元素必须包含至少一个子元素。</span><span class="sxs-lookup"><span data-stu-id="e9dcd-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e9dcd-109">特性</span><span class="sxs-lookup"><span data-stu-id="e9dcd-109">Attributes</span></span>

<span data-ttu-id="e9dcd-110">无。</span><span class="sxs-lookup"><span data-stu-id="e9dcd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e9dcd-111">子元素</span><span class="sxs-lookup"><span data-stu-id="e9dcd-111">Child Elements</span></span>

|<span data-ttu-id="e9dcd-112">元素</span><span class="sxs-lookup"><span data-stu-id="e9dcd-112">Element</span></span>|<span data-ttu-id="e9dcd-113">描述</span><span class="sxs-lookup"><span data-stu-id="e9dcd-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e9dcd-114">配置 （格式） 的控件元素</span><span class="sxs-lookup"><span data-stu-id="e9dcd-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="e9dcd-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="e9dcd-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e9dcd-116">定义可由格式设置文件的所有视图的公共控件。</span><span class="sxs-lookup"><span data-stu-id="e9dcd-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="e9dcd-117">DefaultSettings 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="e9dcd-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="e9dcd-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="e9dcd-118">Optional element.</span></span><br /><br /> <span data-ttu-id="e9dcd-119">定义应用于的格式设置文件的所有视图的常见设置。</span><span class="sxs-lookup"><span data-stu-id="e9dcd-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="e9dcd-120">SelectionSets 元素格式</span><span class="sxs-lookup"><span data-stu-id="e9dcd-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="e9dcd-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="e9dcd-121">Optional element.</span></span><br /><br /> <span data-ttu-id="e9dcd-122">定义可以使用的格式设置文件的所有视图的.NET 对象的公用集。</span><span class="sxs-lookup"><span data-stu-id="e9dcd-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="e9dcd-123">ViewDefinitions 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="e9dcd-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="e9dcd-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="e9dcd-124">Optional element.</span></span><br /><br /> <span data-ttu-id="e9dcd-125">定义用于显示对象的视图。</span><span class="sxs-lookup"><span data-stu-id="e9dcd-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e9dcd-126">父元素</span><span class="sxs-lookup"><span data-stu-id="e9dcd-126">Parent Elements</span></span>

<span data-ttu-id="e9dcd-127">无。</span><span class="sxs-lookup"><span data-stu-id="e9dcd-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="e9dcd-128">备注</span><span class="sxs-lookup"><span data-stu-id="e9dcd-128">Remarks</span></span>

<span data-ttu-id="e9dcd-129">格式设置文件定义对象的显示方式。</span><span class="sxs-lookup"><span data-stu-id="e9dcd-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="e9dcd-130">在大多数情况下，此根元素包含[ViewDefinitions](./viewdefinitions-element-format.md)定义表、 列表和格式设置文件的宽视图元素。</span><span class="sxs-lookup"><span data-stu-id="e9dcd-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="e9dcd-131">除了视图定义中，常见的选项集、 设置和控件，可以使用这些视图可以定义的格式设置文件。</span><span class="sxs-lookup"><span data-stu-id="e9dcd-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9dcd-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e9dcd-132">See Also</span></span>

[<span data-ttu-id="e9dcd-133">配置 （格式） 的控件元素</span><span class="sxs-lookup"><span data-stu-id="e9dcd-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="e9dcd-134">DefaultSettings 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="e9dcd-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="e9dcd-135">SelectionSets 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="e9dcd-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="e9dcd-136">ViewDefinitions 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="e9dcd-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="e9dcd-137">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="e9dcd-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
