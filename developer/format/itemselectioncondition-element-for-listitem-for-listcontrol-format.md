---
title: ItemSelectionCondition ListControl （格式） 的 ListItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861863"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="e240e-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e240e-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="e240e-103">定义必须存在要使用此列表项的条件。</span><span class="sxs-lookup"><span data-stu-id="e240e-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="e240e-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 ListEntries ListEntry ListControl （格式） Listitem 元素的 ListControl （格式） ListEntry 元素ListControl （格式） ItemSelectionCondition ListControl （格式） 的 ListItem 元素 ListItems ListControl （格式） ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="e240e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e240e-105">语法</span><span class="sxs-lookup"><span data-stu-id="e240e-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e240e-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="e240e-106">Attributes and Elements</span></span>

<span data-ttu-id="e240e-107">以下各节描述了特性、 子元素和父元素的`ItemSelectionCondition`元素。</span><span class="sxs-lookup"><span data-stu-id="e240e-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e240e-108">特性</span><span class="sxs-lookup"><span data-stu-id="e240e-108">Attributes</span></span>

<span data-ttu-id="e240e-109">无。</span><span class="sxs-lookup"><span data-stu-id="e240e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e240e-110">子元素</span><span class="sxs-lookup"><span data-stu-id="e240e-110">Child Elements</span></span>

|<span data-ttu-id="e240e-111">元素</span><span class="sxs-lookup"><span data-stu-id="e240e-111">Element</span></span>|<span data-ttu-id="e240e-112">描述</span><span class="sxs-lookup"><span data-stu-id="e240e-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e240e-113">ListControl （格式） 的 ItemSelectionCondition PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="e240e-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="e240e-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="e240e-114">Optional element.</span></span><br /><br /> <span data-ttu-id="e240e-115">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="e240e-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="e240e-116">ItemSelectionCondition 的 ListControl （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="e240e-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="e240e-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="e240e-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e240e-118">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="e240e-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e240e-119">父元素</span><span class="sxs-lookup"><span data-stu-id="e240e-119">Parent Elements</span></span>

|<span data-ttu-id="e240e-120">元素</span><span class="sxs-lookup"><span data-stu-id="e240e-120">Element</span></span>|<span data-ttu-id="e240e-121">描述</span><span class="sxs-lookup"><span data-stu-id="e240e-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e240e-122">ListItems 的 ListControl （格式） 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="e240e-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="e240e-123">定义属性或其值显示在列表视图的行中的脚本。</span><span class="sxs-lookup"><span data-stu-id="e240e-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e240e-124">备注</span><span class="sxs-lookup"><span data-stu-id="e240e-124">Remarks</span></span>

<span data-ttu-id="e240e-125">您可以指定一个属性名称或用于这种情况的脚本，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="e240e-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="e240e-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e240e-126">See Also</span></span>

[<span data-ttu-id="e240e-127">ListItems 的 ListControl （格式） 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="e240e-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="e240e-128">ListControl （格式） 的 ItemSelectionCondition PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="e240e-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="e240e-129">ItemSelectionCondition 的 ListControl （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="e240e-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="e240e-130">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="e240e-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
