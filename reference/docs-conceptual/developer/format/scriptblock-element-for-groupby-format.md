---
title: GroupBy （格式）的 ScriptBlock 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: 37a297228eb33ff75daf94a12635d42b52c6cc9f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364926"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="2261c-102">ScriptBlock Element for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2261c-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="2261c-103">指定在新组的值发生更改时启动新组的脚本。</span><span class="sxs-lookup"><span data-stu-id="2261c-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="2261c-104">GroupBy 的 View （format） ScriptBlock 元素的配置元素（格式） ViewDefinitions 元素（格式） GroupBy 元素（format）</span><span class="sxs-lookup"><span data-stu-id="2261c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2261c-105">语法</span><span class="sxs-lookup"><span data-stu-id="2261c-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2261c-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="2261c-106">Attributes and Elements</span></span>

<span data-ttu-id="2261c-107">以下各节介绍了 `ScriptBlock` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2261c-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2261c-108">属性</span><span class="sxs-lookup"><span data-stu-id="2261c-108">Attributes</span></span>

<span data-ttu-id="2261c-109">无。</span><span class="sxs-lookup"><span data-stu-id="2261c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2261c-110">子元素</span><span class="sxs-lookup"><span data-stu-id="2261c-110">Child Elements</span></span>

<span data-ttu-id="2261c-111">无。</span><span class="sxs-lookup"><span data-stu-id="2261c-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2261c-112">父元素</span><span class="sxs-lookup"><span data-stu-id="2261c-112">Parent Elements</span></span>

|<span data-ttu-id="2261c-113">元素</span><span class="sxs-lookup"><span data-stu-id="2261c-113">Element</span></span>|<span data-ttu-id="2261c-114">描述</span><span class="sxs-lookup"><span data-stu-id="2261c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2261c-115">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2261c-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="2261c-116">定义一组 .NET 对象的显示方式。</span><span class="sxs-lookup"><span data-stu-id="2261c-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2261c-117">文本值</span><span class="sxs-lookup"><span data-stu-id="2261c-117">Text Value</span></span>

<span data-ttu-id="2261c-118">指定要评估的脚本。</span><span class="sxs-lookup"><span data-stu-id="2261c-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="2261c-119">备注</span><span class="sxs-lookup"><span data-stu-id="2261c-119">Remarks</span></span>

<span data-ttu-id="2261c-120">每当此脚本的值发生更改时，PowerShell 就会启动一个新组。</span><span class="sxs-lookup"><span data-stu-id="2261c-120">PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="2261c-121">如果指定此元素，则不能指定[PropertyName](propertyname-element-for-groupby-format.md)元素来启动新组。</span><span class="sxs-lookup"><span data-stu-id="2261c-121">When this element is specified, you cannot specify the [PropertyName](propertyname-element-for-groupby-format.md) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="2261c-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2261c-122">See Also</span></span>

[<span data-ttu-id="2261c-123">GroupBy 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="2261c-123">PropertyName Element for GroupBy (Format)</span></span>](propertyname-element-for-groupby-format.md)

[<span data-ttu-id="2261c-124">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2261c-124">GroupBy Element for View (Format)</span></span>](groupby-element-for-view-format.md)

[<span data-ttu-id="2261c-125">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="2261c-125">Writing a PowerShell Formatting File</span></span>](writing-a-powershell-formatting-file.md)
