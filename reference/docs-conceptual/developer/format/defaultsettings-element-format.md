---
title: DefaultSettings 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41c56499-ee20-4821-830a-478fdcc33f83
caps.latest.revision: 11
ms.openlocfilehash: bc95c62222eb2806f92499257a397c2e4ec5dbab
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363866"
---
# <a name="defaultsettings-element-format"></a><span data-ttu-id="2c0be-102">DefaultSettings Element (Format)</span><span class="sxs-lookup"><span data-stu-id="2c0be-102">DefaultSettings Element (Format)</span></span>

<span data-ttu-id="2c0be-103">定义适用于格式设置文件的所有视图的常见设置。</span><span class="sxs-lookup"><span data-stu-id="2c0be-103">Defines common settings that apply to all the views of the formatting file.</span></span> <span data-ttu-id="2c0be-104">常见的设置包括显示错误、在表中环绕文本、定义集合的展开方式等。</span><span class="sxs-lookup"><span data-stu-id="2c0be-104">Common settings include displaying errors, wrapping text in tables, defining how collections are expanded, and more.</span></span>

<span data-ttu-id="2c0be-105">Configuration 元素（Format） DefaultSettings 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="2c0be-105">Configuration Element (Format) DefaultSettings Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2c0be-106">语法</span><span class="sxs-lookup"><span data-stu-id="2c0be-106">Syntax</span></span>

```xml
<DefaultSettings>
  <ShowError/>
  <DisplayError/>
 <PropertyCountForTable>NumberOfProperties</PropertyCountFortable>
  <WrapTables/>
  <EnumerableExpansions>...</EnumerableExpansions>
</DefaultSettings>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2c0be-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="2c0be-107">Attributes and Elements</span></span>

<span data-ttu-id="2c0be-108">以下各节介绍了 `DefaultSettings` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2c0be-108">The following sections describe attributes, child elements, and the parent element of the `DefaultSettings` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2c0be-109">属性</span><span class="sxs-lookup"><span data-stu-id="2c0be-109">Attributes</span></span>

<span data-ttu-id="2c0be-110">无。</span><span class="sxs-lookup"><span data-stu-id="2c0be-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2c0be-111">子元素</span><span class="sxs-lookup"><span data-stu-id="2c0be-111">Child Elements</span></span>

|<span data-ttu-id="2c0be-112">元素</span><span class="sxs-lookup"><span data-stu-id="2c0be-112">Element</span></span>|<span data-ttu-id="2c0be-113">描述</span><span class="sxs-lookup"><span data-stu-id="2c0be-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2c0be-114">DisplayError 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2c0be-114">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)|<span data-ttu-id="2c0be-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2c0be-115">Optional element.</span></span><br /><br /> <span data-ttu-id="2c0be-116">指定在显示一段数据的过程中出现错误时，显示字符串 #ERR。</span><span class="sxs-lookup"><span data-stu-id="2c0be-116">Specifies that the string #ERR is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="2c0be-117">EnumerableExpansions 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2c0be-117">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="2c0be-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2c0be-118">Optional element.</span></span><br /><br /> <span data-ttu-id="2c0be-119">定义 .NET 对象显示在视图中时的不同显示方式。</span><span class="sxs-lookup"><span data-stu-id="2c0be-119">Defines the different ways that .NET objects are expanded when they are displayed in a view.</span></span>|
|[<span data-ttu-id="2c0be-120">PropertyCountForTable （格式）</span><span class="sxs-lookup"><span data-stu-id="2c0be-120">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)|<span data-ttu-id="2c0be-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2c0be-121">Optional element.</span></span><br /><br /> <span data-ttu-id="2c0be-122">指定在表视图中显示对象时必须包含的属性的最小数目。</span><span class="sxs-lookup"><span data-stu-id="2c0be-122">Specifies the minimum number of properties that an object must have to display the object in a table view.</span></span>|
|[<span data-ttu-id="2c0be-123">ShowError 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2c0be-123">ShowError Element (Format)</span></span>](./showerror-element-format.md)|<span data-ttu-id="2c0be-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2c0be-124">Optional element.</span></span><br /><br /> <span data-ttu-id="2c0be-125">指定在显示一段数据的过程中出现错误时，显示完整的错误记录。</span><span class="sxs-lookup"><span data-stu-id="2c0be-125">Specifies that the full error record is displayed when an error occurs while displaying a piece of data.</span></span>|
|[<span data-ttu-id="2c0be-126">WrapTables 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2c0be-126">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)|<span data-ttu-id="2c0be-127">可选元素。</span><span class="sxs-lookup"><span data-stu-id="2c0be-127">Optional element.</span></span><br /><br /> <span data-ttu-id="2c0be-128">指定如果表中的数据无法适应列的宽度，则将其移到下一行。</span><span class="sxs-lookup"><span data-stu-id="2c0be-128">Specifies that data in a table is moved to the next line if it does not fit into the width of the column.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2c0be-129">父元素</span><span class="sxs-lookup"><span data-stu-id="2c0be-129">Parent Elements</span></span>

|<span data-ttu-id="2c0be-130">元素</span><span class="sxs-lookup"><span data-stu-id="2c0be-130">Element</span></span>|<span data-ttu-id="2c0be-131">描述</span><span class="sxs-lookup"><span data-stu-id="2c0be-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2c0be-132">配置元素</span><span class="sxs-lookup"><span data-stu-id="2c0be-132">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="2c0be-133">表示格式设置文件的顶级元素。</span><span class="sxs-lookup"><span data-stu-id="2c0be-133">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2c0be-134">备注</span><span class="sxs-lookup"><span data-stu-id="2c0be-134">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="2c0be-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2c0be-135">See Also</span></span>

[<span data-ttu-id="2c0be-136">配置元素</span><span class="sxs-lookup"><span data-stu-id="2c0be-136">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="2c0be-137">DisplayError 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2c0be-137">DisplayError Element (Format)</span></span>](./displayerror-element-format.md)

[<span data-ttu-id="2c0be-138">EnumerableExpansions 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2c0be-138">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)

[<span data-ttu-id="2c0be-139">PropertyCountForTable （格式）</span><span class="sxs-lookup"><span data-stu-id="2c0be-139">PropertyCountForTable (Format)</span></span>](./propertycountfortable-element-format.md)

[<span data-ttu-id="2c0be-140">ShowError 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2c0be-140">ShowError Element (Format)</span></span>](./showerror-element-format.md)

[<span data-ttu-id="2c0be-141">WrapTables 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="2c0be-141">WrapTables Element (Format)</span></span>](./wraptables-element-format.md)

[<span data-ttu-id="2c0be-142">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="2c0be-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
