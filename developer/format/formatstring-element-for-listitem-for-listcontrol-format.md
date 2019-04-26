---
title: ListControl （格式） 的列表项的 FormatString 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd2cac66-88bb-449f-9d47-bd2cd4fe1801
caps.latest.revision: 13
ms.openlocfilehash: e6024ec4f7fc490c92408047c8c15c775e45bf9d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065608"
---
# <a name="formatstring-element-for-listitem-for-listcontrol--format"></a><span data-ttu-id="16dbf-102">FormatString Element for ListItem for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="16dbf-102">FormatString Element for ListItem for ListControl  (Format)</span></span>

<span data-ttu-id="16dbf-103">指定格式模式，它定义如何显示的属性或脚本的值。</span><span class="sxs-lookup"><span data-stu-id="16dbf-103">Specifies a format pattern that defines how the property or script value is displayed.</span></span>

<span data-ttu-id="16dbf-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素的元素 ListControl （格式） ListEntry ListControl （格式） 的 ListControl （格式） Listitem 元素ListControl （格式） 格式说明符 ListControl （格式） 的 ListItem 元素的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="16dbf-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem Element for ListControl (Format) FormatString Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="16dbf-105">语法</span><span class="sxs-lookup"><span data-stu-id="16dbf-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="16dbf-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="16dbf-106">Attributes and Elements</span></span>

<span data-ttu-id="16dbf-107">以下各节描述了特性、 子元素和父元素的`FormatString`元素。</span><span class="sxs-lookup"><span data-stu-id="16dbf-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="16dbf-108">属性</span><span class="sxs-lookup"><span data-stu-id="16dbf-108">Attributes</span></span>

<span data-ttu-id="16dbf-109">无。</span><span class="sxs-lookup"><span data-stu-id="16dbf-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="16dbf-110">子元素</span><span class="sxs-lookup"><span data-stu-id="16dbf-110">Child Elements</span></span>

<span data-ttu-id="16dbf-111">无。</span><span class="sxs-lookup"><span data-stu-id="16dbf-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="16dbf-112">父元素</span><span class="sxs-lookup"><span data-stu-id="16dbf-112">Parent Elements</span></span>

|<span data-ttu-id="16dbf-113">元素</span><span class="sxs-lookup"><span data-stu-id="16dbf-113">Element</span></span>|<span data-ttu-id="16dbf-114">说明</span><span class="sxs-lookup"><span data-stu-id="16dbf-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="16dbf-115">ListItem 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="16dbf-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="16dbf-116">定义属性或其值显示在列表视图的行中的脚本。</span><span class="sxs-lookup"><span data-stu-id="16dbf-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="16dbf-117">文本值</span><span class="sxs-lookup"><span data-stu-id="16dbf-117">Text Value</span></span>

<span data-ttu-id="16dbf-118">指定用于设置数据格式的模式。</span><span class="sxs-lookup"><span data-stu-id="16dbf-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="16dbf-119">例如，可以使用此模式的类型的任何属性的值进行格式[System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {{0:hh}: {0:mm}。</span><span class="sxs-lookup"><span data-stu-id="16dbf-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="16dbf-120">备注</span><span class="sxs-lookup"><span data-stu-id="16dbf-120">Remarks</span></span>

<span data-ttu-id="16dbf-121">创建表视图、 列表视图、 宽视图或自定义视图时，可以使用格式字符串。</span><span class="sxs-lookup"><span data-stu-id="16dbf-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="16dbf-122">有关格式设置显示在视图中的一个值的详细信息，请参阅[格式显示数据](./formatting-displayed-data.md)。</span><span class="sxs-lookup"><span data-stu-id="16dbf-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="16dbf-123">在列表视图中使用格式字符串的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="16dbf-123">For more information about using format strings in list views, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="16dbf-124">示例</span><span class="sxs-lookup"><span data-stu-id="16dbf-124">Example</span></span>

<span data-ttu-id="16dbf-125">下面的示例演示如何定义的值的格式设置字符串`StartTime`属性。</span><span class="sxs-lookup"><span data-stu-id="16dbf-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

## <a name="see-also"></a><span data-ttu-id="16dbf-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="16dbf-126">See Also</span></span>

[<span data-ttu-id="16dbf-127">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="16dbf-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="16dbf-128">ListItem 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="16dbf-128">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="16dbf-129">编写 Windows PowerShell 格式设置和文件类型</span><span class="sxs-lookup"><span data-stu-id="16dbf-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
