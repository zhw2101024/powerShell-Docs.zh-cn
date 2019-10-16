---
title: ListControl 的 ItemSelectionCondition 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2668aea-37e9-4753-a4e9-7980ae5ec2eb
caps.latest.revision: 10
ms.openlocfilehash: 6bc0ccbcc5bd62429f63ed220da66dc66f44f7ca
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365186"
---
# <a name="itemselectioncondition-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="02654-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="02654-102">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="02654-103">定义要使用此列表项必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="02654-103">Defines the condition that must exist for this list item to be used.</span></span>

<span data-ttu-id="02654-104">用于 ListEntry 的 ListEntries for ListControl （Format） ListItems 元素的 ListControl （Format） ListEntry 元素的 Configuration Element （Format） ViewDefinitions 元素（格式） ListControl 元素（format） ListEntries 元素对于 ListItems for ListControl （Format） ItemSelectionCondition 元素的 ListControl （格式） "" 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="02654-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="02654-105">语法</span><span class="sxs-lookup"><span data-stu-id="02654-105">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="02654-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="02654-106">Attributes and Elements</span></span>

<span data-ttu-id="02654-107">以下各节介绍了 `ItemSelectionCondition` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="02654-107">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="02654-108">属性</span><span class="sxs-lookup"><span data-stu-id="02654-108">Attributes</span></span>

<span data-ttu-id="02654-109">无。</span><span class="sxs-lookup"><span data-stu-id="02654-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="02654-110">子元素</span><span class="sxs-lookup"><span data-stu-id="02654-110">Child Elements</span></span>

|<span data-ttu-id="02654-111">元素</span><span class="sxs-lookup"><span data-stu-id="02654-111">Element</span></span>|<span data-ttu-id="02654-112">描述</span><span class="sxs-lookup"><span data-stu-id="02654-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="02654-113">ListControl 的 ItemSelectionCondition 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="02654-113">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="02654-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="02654-114">Optional element.</span></span><br /><br /> <span data-ttu-id="02654-115">指定触发条件的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="02654-115">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="02654-116">ListControl 的 ItemSelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="02654-116">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)|<span data-ttu-id="02654-117">可选元素。</span><span class="sxs-lookup"><span data-stu-id="02654-117">Optional element.</span></span><br /><br /> <span data-ttu-id="02654-118">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="02654-118">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="02654-119">父元素</span><span class="sxs-lookup"><span data-stu-id="02654-119">Parent Elements</span></span>

|<span data-ttu-id="02654-120">元素</span><span class="sxs-lookup"><span data-stu-id="02654-120">Element</span></span>|<span data-ttu-id="02654-121">描述</span><span class="sxs-lookup"><span data-stu-id="02654-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="02654-122">ListControl 的 ListItems 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="02654-122">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="02654-123">定义其值显示在列表视图的行中的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="02654-123">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="02654-124">备注</span><span class="sxs-lookup"><span data-stu-id="02654-124">Remarks</span></span>

<span data-ttu-id="02654-125">您可以为此条件指定一个属性名称或脚本，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="02654-125">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="02654-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="02654-126">See Also</span></span>

[<span data-ttu-id="02654-127">ListControl 的 ListItems 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="02654-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="02654-128">ListControl 的 ItemSelectionCondition 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="02654-128">PropertyName Element for ItemSelectionCondition for ListControl (Format)</span></span>](./propertyname-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="02654-129">ListControl 的 ItemSelectionCondition 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="02654-129">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-listcontrol-format.md)

[<span data-ttu-id="02654-130">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="02654-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
