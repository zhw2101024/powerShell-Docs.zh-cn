---
title: GroupBy （格式） 的脚本块元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30183927-6f0e-4717-b6f5-f07a6e134cfb
caps.latest.revision: 6
ms.openlocfilehash: f2f6b9af7740b1231881294c2f32bf97b5a1568b
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054419"
---
# <a name="scriptblock-element-for-groupby-format"></a><span data-ttu-id="60559-102">ScriptBlock Element for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="60559-102">ScriptBlock Element for GroupBy (Format)</span></span>

<span data-ttu-id="60559-103">指定其值发生更改时启动新的组的脚本。</span><span class="sxs-lookup"><span data-stu-id="60559-103">Specifies the script that starts a new group whenever its value changes.</span></span>

<span data-ttu-id="60559-104">视图 （格式） 的 GroupBy （格式） 的脚本块元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="60559-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) ScriptBlock Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="60559-105">语法</span><span class="sxs-lookup"><span data-stu-id="60559-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="60559-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="60559-106">Attributes and Elements</span></span>

<span data-ttu-id="60559-107">以下各节描述了特性、 子元素和父元素的`ScriptBlock`元素。</span><span class="sxs-lookup"><span data-stu-id="60559-107">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="60559-108">属性</span><span class="sxs-lookup"><span data-stu-id="60559-108">Attributes</span></span>

<span data-ttu-id="60559-109">无。</span><span class="sxs-lookup"><span data-stu-id="60559-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="60559-110">子元素</span><span class="sxs-lookup"><span data-stu-id="60559-110">Child Elements</span></span>

<span data-ttu-id="60559-111">无。</span><span class="sxs-lookup"><span data-stu-id="60559-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="60559-112">父元素</span><span class="sxs-lookup"><span data-stu-id="60559-112">Parent Elements</span></span>

|<span data-ttu-id="60559-113">元素</span><span class="sxs-lookup"><span data-stu-id="60559-113">Element</span></span>|<span data-ttu-id="60559-114">说明</span><span class="sxs-lookup"><span data-stu-id="60559-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="60559-115">视图 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="60559-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="60559-116">定义一组.NET 对象的显示方式。</span><span class="sxs-lookup"><span data-stu-id="60559-116">Defines how a group of .NET objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="60559-117">文本值</span><span class="sxs-lookup"><span data-stu-id="60559-117">Text Value</span></span>

<span data-ttu-id="60559-118">指定计算的脚本。</span><span class="sxs-lookup"><span data-stu-id="60559-118">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="60559-119">备注</span><span class="sxs-lookup"><span data-stu-id="60559-119">Remarks</span></span>

<span data-ttu-id="60559-120">此脚本的值发生更改时，Windows PowerShell 启动新的组。</span><span class="sxs-lookup"><span data-stu-id="60559-120">Windows PowerShell starts a new group whenever the value of this script changes.</span></span>

<span data-ttu-id="60559-121">当指定此元素时，不能指定[PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676)元素，用于启动新的组。</span><span class="sxs-lookup"><span data-stu-id="60559-121">When this element is specified, you cannot specify the [PropertyName](http://msdn.microsoft.com/en-us/396dede0-039a-4a87-a5ef-3ecabb729676) element to start a new group.</span></span>

## <a name="see-also"></a><span data-ttu-id="60559-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="60559-122">See Also</span></span>

[<span data-ttu-id="60559-123">GroupBy （格式） 的属性名称元素</span><span class="sxs-lookup"><span data-stu-id="60559-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="60559-124">视图 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="60559-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="60559-125">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="60559-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
