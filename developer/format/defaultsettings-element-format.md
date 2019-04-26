---
title: DefaultSettings 元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066339"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="386ee-102">DefaultSettings Element (Format)</span><span class="sxs-lookup"><span data-stu-id="386ee-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="386ee-103">定义应用于的格式设置文件的所有视图的常见设置。</span><span class="sxs-lookup"><span data-stu-id="386ee-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="386ee-104">常用的设置包括显示错误，表定义如何将扩展集合，和的详细信息中的文本换行。</span><span class="sxs-lookup"><span data-stu-id="386ee-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="386ee-105">配置元素 （格式） DefaultSettings 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="386ee-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="386ee-106">语法</span><span class="sxs-lookup"><span data-stu-id="386ee-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="386ee-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="386ee-107">Attributes and Elements</span></span>

<span data-ttu-id="386ee-108">以下各节描述了特性、 子元素和父元素的`DefaultSettings`元素。</span><span class="sxs-lookup"><span data-stu-id="386ee-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="386ee-109">属性</span><span class="sxs-lookup"><span data-stu-id="386ee-109">Attributes</span></span>

<span data-ttu-id="386ee-110">无。</span><span class="sxs-lookup"><span data-stu-id="386ee-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="386ee-111">子元素</span><span class="sxs-lookup"><span data-stu-id="386ee-111">Child Elements</span></span>

|<span data-ttu-id="386ee-112">元素</span><span class="sxs-lookup"><span data-stu-id="386ee-112">Element</span></span>|<span data-ttu-id="386ee-113">说明</span><span class="sxs-lookup"><span data-stu-id="386ee-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="386ee-114">DisplayError 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="386ee-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="386ee-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="386ee-115">Optional element.</span></span><br /><br /> <span data-ttu-id="386ee-116">指定在显示的一段数据的同时发生错误时显示的字符串 #ERR。</span><span class="sxs-lookup"><span data-stu-id="386ee-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="386ee-117">EnumerableExpansions 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="386ee-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="386ee-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="386ee-118">Optional element.</span></span><br /><br /> <span data-ttu-id="386ee-119">定义.NET 对象时它们显示在视图中展开的不同方法。</span><span class="sxs-lookup"><span data-stu-id="386ee-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="386ee-120">PropertyCountForTable （格式）</span><span class="sxs-lookup"><span data-stu-id="386ee-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="386ee-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="386ee-121">Optional element.</span></span><br /><br /> <span data-ttu-id="386ee-122">指定对象必须具有要在表视图中显示该对象的属性的最小数目。</span><span class="sxs-lookup"><span data-stu-id="386ee-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="386ee-123">ShowError 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="386ee-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="386ee-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="386ee-124">Optional element.</span></span><br /><br /> <span data-ttu-id="386ee-125">指定在出错时显示一段数据时，显示完整的错误记录。</span><span class="sxs-lookup"><span data-stu-id="386ee-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="386ee-126">WrapTables 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="386ee-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="386ee-127">可选元素。</span><span class="sxs-lookup"><span data-stu-id="386ee-127">Optional element.</span></span><br /><br /> <span data-ttu-id="386ee-128">指定是否不适合的列的宽度，表中的数据将移到下一行。</span><span class="sxs-lookup"><span data-stu-id="386ee-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="386ee-129">父元素</span><span class="sxs-lookup"><span data-stu-id="386ee-129">Parent Elements</span></span>

|<span data-ttu-id="386ee-130">元素</span><span class="sxs-lookup"><span data-stu-id="386ee-130">Element</span></span>|<span data-ttu-id="386ee-131">说明</span><span class="sxs-lookup"><span data-stu-id="386ee-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="386ee-132">配置元素</span><span class="sxs-lookup"><span data-stu-id="386ee-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="386ee-133">表示格式设置文件的顶级元素。</span><span class="sxs-lookup"><span data-stu-id="386ee-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="386ee-134">备注</span><span class="sxs-lookup"><span data-stu-id="386ee-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="386ee-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="386ee-135">See Also</span></span>

[<span data-ttu-id="386ee-136">配置元素</span><span class="sxs-lookup"><span data-stu-id="386ee-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="386ee-137">DisplayError 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="386ee-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="386ee-138">EnumerableExpansions 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="386ee-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="386ee-139">PropertyCountForTable （格式）</span><span class="sxs-lookup"><span data-stu-id="386ee-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="386ee-140">ShowError 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="386ee-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="386ee-141">WrapTables 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="386ee-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="386ee-142">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="386ee-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
