---
title: 脚本块元素 ListControl （格式） 的 ItemSelectionCondition |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064401"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="e9022-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e9022-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="e9022-103">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="e9022-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="e9022-104">当此脚本的计算结果为`true`、 满足该条件，以及使用列表项。</span><span class="sxs-lookup"><span data-stu-id="e9022-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="e9022-105">定义列表视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="e9022-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="e9022-106">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 ListEntries ListEntry ListControl （格式） Listitem 元素的 ListControl （格式） ListEntry 元素ListItem ListControl （格式） 的 ItemSelectionCondition ListControl （格式） 脚本块元素的列表控件 （格式） ItemSelectionCondition 元素 ListItems ListControl （格式） ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="e9022-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e9022-107">语法</span><span class="sxs-lookup"><span data-stu-id="e9022-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e9022-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e9022-108">Attributes and Elements</span></span>

<span data-ttu-id="e9022-109">以下各节描述了特性、 子元素和父元素的`ScriptBlock`元素。</span><span class="sxs-lookup"><span data-stu-id="e9022-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e9022-110">属性</span><span class="sxs-lookup"><span data-stu-id="e9022-110">Attributes</span></span>

<span data-ttu-id="e9022-111">无。</span><span class="sxs-lookup"><span data-stu-id="e9022-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e9022-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e9022-112">Child Elements</span></span>

<span data-ttu-id="e9022-113">无。</span><span class="sxs-lookup"><span data-stu-id="e9022-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e9022-114">父元素</span><span class="sxs-lookup"><span data-stu-id="e9022-114">Parent Elements</span></span>

|<span data-ttu-id="e9022-115">元素</span><span class="sxs-lookup"><span data-stu-id="e9022-115">Element</span></span>|<span data-ttu-id="e9022-116">说明</span><span class="sxs-lookup"><span data-stu-id="e9022-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e9022-117">ItemSelectionCondition ListControl （格式） 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="e9022-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="e9022-118">定义必须存在要使用此列表项的条件。</span><span class="sxs-lookup"><span data-stu-id="e9022-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e9022-119">文本值</span><span class="sxs-lookup"><span data-stu-id="e9022-119">Text Value</span></span>

<span data-ttu-id="e9022-120">指定计算的脚本。</span><span class="sxs-lookup"><span data-stu-id="e9022-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="e9022-121">备注</span><span class="sxs-lookup"><span data-stu-id="e9022-121">Remarks</span></span>

<span data-ttu-id="e9022-122">如果使用此元素时，不能指定`PropertyName`元素定义的选择条件时。</span><span class="sxs-lookup"><span data-stu-id="e9022-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9022-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e9022-123">See Also</span></span>

[<span data-ttu-id="e9022-124">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="e9022-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
