---
title: TableControl （格式） 的 TableColumnItem 的 FormatString 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065614"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="91ecc-102">FormatString Element for TableColumnItem for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="91ecc-102">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="91ecc-103">指定格式模式，它定义如何显示表的属性或脚本值。</span><span class="sxs-lookup"><span data-stu-id="91ecc-103">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="91ecc-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 （格式） TableRowEntry 元素 （格式） TableColumnItems 元素 （格式） TableColumnItem 元素 （格式）TableColumnItem （格式） 的 FormatString 元素</span><span class="sxs-lookup"><span data-stu-id="91ecc-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="91ecc-105">语法</span><span class="sxs-lookup"><span data-stu-id="91ecc-105">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="91ecc-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="91ecc-106">Attributes and Elements</span></span>

<span data-ttu-id="91ecc-107">以下各节描述了特性、 子元素和父元素的`FormatString`元素。</span><span class="sxs-lookup"><span data-stu-id="91ecc-107">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="91ecc-108">属性</span><span class="sxs-lookup"><span data-stu-id="91ecc-108">Attributes</span></span>

<span data-ttu-id="91ecc-109">无。</span><span class="sxs-lookup"><span data-stu-id="91ecc-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="91ecc-110">子元素</span><span class="sxs-lookup"><span data-stu-id="91ecc-110">Child Elements</span></span>

<span data-ttu-id="91ecc-111">无。</span><span class="sxs-lookup"><span data-stu-id="91ecc-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="91ecc-112">父元素</span><span class="sxs-lookup"><span data-stu-id="91ecc-112">Parent Elements</span></span>

|<span data-ttu-id="91ecc-113">元素</span><span class="sxs-lookup"><span data-stu-id="91ecc-113">Element</span></span>|<span data-ttu-id="91ecc-114">说明</span><span class="sxs-lookup"><span data-stu-id="91ecc-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="91ecc-115">TableColumnItem 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="91ecc-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="91ecc-116">定义属性或其值显示在一行的列中的脚本。</span><span class="sxs-lookup"><span data-stu-id="91ecc-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="91ecc-117">文本值</span><span class="sxs-lookup"><span data-stu-id="91ecc-117">Text Value</span></span>

<span data-ttu-id="91ecc-118">指定用于设置数据格式的模式。</span><span class="sxs-lookup"><span data-stu-id="91ecc-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="91ecc-119">例如，使用此模式的类型的任何属性的值进行格式[System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {{0:hh}: {0:mm}。</span><span class="sxs-lookup"><span data-stu-id="91ecc-119">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="91ecc-120">备注</span><span class="sxs-lookup"><span data-stu-id="91ecc-120">Remarks</span></span>

<span data-ttu-id="91ecc-121">创建表视图、 列表视图、 宽视图或自定义视图时，可以使用格式字符串。</span><span class="sxs-lookup"><span data-stu-id="91ecc-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="91ecc-122">有关格式设置显示在视图中的一个值的详细信息，请参阅[格式显示数据](./formatting-displayed-data.md)。</span><span class="sxs-lookup"><span data-stu-id="91ecc-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="91ecc-123">表视图的组件的详细信息，请参阅[表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="91ecc-123">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="91ecc-124">示例</span><span class="sxs-lookup"><span data-stu-id="91ecc-124">Example</span></span>

<span data-ttu-id="91ecc-125">下面的示例演示如何定义的值的格式设置字符串`StartTime`属性。</span><span class="sxs-lookup"><span data-stu-id="91ecc-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="91ecc-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="91ecc-126">See Also</span></span>

[<span data-ttu-id="91ecc-127">创建表视图</span><span class="sxs-lookup"><span data-stu-id="91ecc-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="91ecc-128">设置的格式显示数据</span><span class="sxs-lookup"><span data-stu-id="91ecc-128">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="91ecc-129">TableColumnItem 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="91ecc-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="91ecc-130">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="91ecc-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
