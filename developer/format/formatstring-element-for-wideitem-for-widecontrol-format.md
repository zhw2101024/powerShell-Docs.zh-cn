---
title: FormatString 元素 WideControl （格式） 的 WideItem |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860933"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="e2dc0-102">FormatString Element for WideItem for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="e2dc0-102">FormatString Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="e2dc0-103">指定格式模式，它定义如何在视图中显示的属性或脚本的值。</span><span class="sxs-lookup"><span data-stu-id="e2dc0-103">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

<span data-ttu-id="e2dc0-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） WideEntries 元素 （格式） WideEntry 元素的元素 WideControl （格式） WideItem WideControl （格式） FormatString 元素有关 WideItem 为 WideControl （格式）</span><span class="sxs-lookup"><span data-stu-id="e2dc0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element for WideControl (Format) WideItem Element for WideControl (Format) FormatString Element for WideItem for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e2dc0-105">语法</span><span class="sxs-lookup"><span data-stu-id="e2dc0-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e2dc0-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="e2dc0-106">Attributes and Elements</span></span>

<span data-ttu-id="e2dc0-107">以下各节描述了特性、 子元素和父元素的`FormatString`元素。</span><span class="sxs-lookup"><span data-stu-id="e2dc0-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e2dc0-108">特性</span><span class="sxs-lookup"><span data-stu-id="e2dc0-108">Attributes</span></span>

<span data-ttu-id="e2dc0-109">无。</span><span class="sxs-lookup"><span data-stu-id="e2dc0-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e2dc0-110">子元素</span><span class="sxs-lookup"><span data-stu-id="e2dc0-110">Child Elements</span></span>

<span data-ttu-id="e2dc0-111">无。</span><span class="sxs-lookup"><span data-stu-id="e2dc0-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e2dc0-112">父元素</span><span class="sxs-lookup"><span data-stu-id="e2dc0-112">Parent Elements</span></span>

|<span data-ttu-id="e2dc0-113">元素</span><span class="sxs-lookup"><span data-stu-id="e2dc0-113">Element</span></span>|<span data-ttu-id="e2dc0-114">描述</span><span class="sxs-lookup"><span data-stu-id="e2dc0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e2dc0-115">WideControl （格式） 的 WideItem 元素</span><span class="sxs-lookup"><span data-stu-id="e2dc0-115">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="e2dc0-116">定义属性或其值显示在列表视图的行中的脚本。</span><span class="sxs-lookup"><span data-stu-id="e2dc0-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e2dc0-117">文本值</span><span class="sxs-lookup"><span data-stu-id="e2dc0-117">Text Value</span></span>

<span data-ttu-id="e2dc0-118">指定用于设置数据格式的模式。</span><span class="sxs-lookup"><span data-stu-id="e2dc0-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="e2dc0-119">例如，可以使用此模式的类型的任何属性的值进行格式[System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {{0:hh}: {0:mm}。</span><span class="sxs-lookup"><span data-stu-id="e2dc0-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="e2dc0-120">备注</span><span class="sxs-lookup"><span data-stu-id="e2dc0-120">Remarks</span></span>

<span data-ttu-id="e2dc0-121">创建表视图、 列表视图、 宽视图或自定义视图时，可以使用格式字符串。</span><span class="sxs-lookup"><span data-stu-id="e2dc0-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="e2dc0-122">有关格式设置显示在视图中的一个值的详细信息，请参阅[格式显示数据](./formatting-displayed-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e2dc0-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="e2dc0-123">有关宽视图中使用格式字符串的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="e2dc0-123">For more information about using format strings in wide views, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e2dc0-124">示例</span><span class="sxs-lookup"><span data-stu-id="e2dc0-124">Example</span></span>

<span data-ttu-id="e2dc0-125">下面的示例演示如何定义的值的格式设置字符串`StartTime`属性。</span><span class="sxs-lookup"><span data-stu-id="e2dc0-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="e2dc0-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e2dc0-126">See Also</span></span>

[<span data-ttu-id="e2dc0-127">创建较宽的视图</span><span class="sxs-lookup"><span data-stu-id="e2dc0-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e2dc0-128">WideControl （格式） 的 WideItem 元素</span><span class="sxs-lookup"><span data-stu-id="e2dc0-128">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="e2dc0-129">编写 Windows PowerShell 格式设置和文件类型</span><span class="sxs-lookup"><span data-stu-id="e2dc0-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
