---
title: ListControl 的 ItemSelectionCondition 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c929a6df-d050-416a-9de0-e913dd5a035c
caps.latest.revision: 8
ms.openlocfilehash: a0768a9c1ac66cd9dcf1848c4b031ccbc722b4c2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362096"
---
# <a name="scriptblock-element-for-itemselectioncondition-for-listcontrol-format"></a><span data-ttu-id="7db36-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7db36-102">ScriptBlock Element for ItemSelectionCondition for ListControl (Format)</span></span>

<span data-ttu-id="7db36-103">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="7db36-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="7db36-104">如果此脚本的计算结果为 `true`，则满足条件，并使用列表项。</span><span class="sxs-lookup"><span data-stu-id="7db36-104">When this script is evaluated to `true`, the condition is met, and the list item is used.</span></span> <span data-ttu-id="7db36-105">定义列表视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="7db36-105">This element is used when defining a list view.</span></span>

<span data-ttu-id="7db36-106">用于 ListEntry 的 ListEntries for ListControl （Format） ListItems 元素的 ListControl （Format） ListEntry 元素的 Configuration Element （Format） ViewDefinitions 元素（格式） ListControl 元素（format） ListEntries 元素对于 ItemSelectionCondition for ListControl 的 ListControl （Format） ScriptBlock 元素的 ListItems 的 ListControl （格式）列表控件（Format） ItemSelectionCondition 元素的元素</span><span class="sxs-lookup"><span data-stu-id="7db36-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for List Control (Format) ItemSelectionCondition Element for ListItem for ListControl (Format) ScriptBlock Element for ItemSelectionCondition for ListControl  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7db36-107">语法</span><span class="sxs-lookup"><span data-stu-id="7db36-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7db36-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="7db36-108">Attributes and Elements</span></span>

<span data-ttu-id="7db36-109">以下各节介绍了 `ScriptBlock` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7db36-109">The following sections describe attributes, child elements, and the parent elements of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7db36-110">属性</span><span class="sxs-lookup"><span data-stu-id="7db36-110">Attributes</span></span>

<span data-ttu-id="7db36-111">无。</span><span class="sxs-lookup"><span data-stu-id="7db36-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7db36-112">子元素</span><span class="sxs-lookup"><span data-stu-id="7db36-112">Child Elements</span></span>

<span data-ttu-id="7db36-113">无。</span><span class="sxs-lookup"><span data-stu-id="7db36-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7db36-114">父元素</span><span class="sxs-lookup"><span data-stu-id="7db36-114">Parent Elements</span></span>

|<span data-ttu-id="7db36-115">元素</span><span class="sxs-lookup"><span data-stu-id="7db36-115">Element</span></span>|<span data-ttu-id="7db36-116">描述</span><span class="sxs-lookup"><span data-stu-id="7db36-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7db36-117">ListControl 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7db36-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="7db36-118">定义要使用此列表项必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="7db36-118">Defines the condition that must exist for this list item to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7db36-119">文本值</span><span class="sxs-lookup"><span data-stu-id="7db36-119">Text Value</span></span>

<span data-ttu-id="7db36-120">指定要评估的脚本。</span><span class="sxs-lookup"><span data-stu-id="7db36-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="7db36-121">备注</span><span class="sxs-lookup"><span data-stu-id="7db36-121">Remarks</span></span>

<span data-ttu-id="7db36-122">如果使用此元素，则在定义选择条件时，不能指定 `PropertyName` 元素。</span><span class="sxs-lookup"><span data-stu-id="7db36-122">If this element is used, you cannot specify the `PropertyName` element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="7db36-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7db36-123">See Also</span></span>

[<span data-ttu-id="7db36-124">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="7db36-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
