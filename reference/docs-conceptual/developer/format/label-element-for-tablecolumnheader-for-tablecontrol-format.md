---
title: TableControl 的 TableColumnHeader 的 Label 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365166"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="450ee-102">Label Element for TableColumnHeader for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="450ee-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="450ee-103">定义在列顶部显示的标签。</span><span class="sxs-lookup"><span data-stu-id="450ee-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="450ee-104">定义表视图时使用此元素。</span><span class="sxs-lookup"><span data-stu-id="450ee-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="450ee-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（format） TableHeaders 元素 for TableControl （Format） TableColumnHeader 元素 for TableHeaders for TableControl （Format） Label 元素 forTableColumnHeader for TableControl （Format）</span><span class="sxs-lookup"><span data-stu-id="450ee-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="450ee-106">语法</span><span class="sxs-lookup"><span data-stu-id="450ee-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="450ee-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="450ee-107">Attributes and Elements</span></span>

<span data-ttu-id="450ee-108">以下各节介绍了 `Label` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="450ee-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="450ee-109">每个列只允许有一个标签。</span><span class="sxs-lookup"><span data-stu-id="450ee-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="450ee-110">特性</span><span class="sxs-lookup"><span data-stu-id="450ee-110">Attributes</span></span>

<span data-ttu-id="450ee-111">无。</span><span class="sxs-lookup"><span data-stu-id="450ee-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="450ee-112">子元素</span><span class="sxs-lookup"><span data-stu-id="450ee-112">Child Elements</span></span>

<span data-ttu-id="450ee-113">无。</span><span class="sxs-lookup"><span data-stu-id="450ee-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="450ee-114">父元素</span><span class="sxs-lookup"><span data-stu-id="450ee-114">Parent Elements</span></span>

|<span data-ttu-id="450ee-115">元素</span><span class="sxs-lookup"><span data-stu-id="450ee-115">Element</span></span>|<span data-ttu-id="450ee-116">描述</span><span class="sxs-lookup"><span data-stu-id="450ee-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="450ee-117">TableControl 的 TableHeaders 的 TableColumnHeader 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="450ee-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="450ee-118">定义表中某一列的数据的标签、宽度和对齐方式。</span><span class="sxs-lookup"><span data-stu-id="450ee-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="450ee-119">文本值</span><span class="sxs-lookup"><span data-stu-id="450ee-119">Text Value</span></span>

<span data-ttu-id="450ee-120">指定在表的列顶部显示的文本。</span><span class="sxs-lookup"><span data-stu-id="450ee-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="450ee-121">列标签没有受限制的字符。</span><span class="sxs-lookup"><span data-stu-id="450ee-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="450ee-122">备注</span><span class="sxs-lookup"><span data-stu-id="450ee-122">Remarks</span></span>

<span data-ttu-id="450ee-123">如果未指定标签，则使用在行中显示其值的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="450ee-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="450ee-124">有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="450ee-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="450ee-125">示例</span><span class="sxs-lookup"><span data-stu-id="450ee-125">Example</span></span>

<span data-ttu-id="450ee-126">此示例演示一个标签为 "Column 1" 的 `TableColumnHeader` 元素。</span><span class="sxs-lookup"><span data-stu-id="450ee-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="450ee-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="450ee-127">See Also</span></span>

[<span data-ttu-id="450ee-128">创建表视图</span><span class="sxs-lookup"><span data-stu-id="450ee-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="450ee-129">TableColumnHeader 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="450ee-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="450ee-130">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="450ee-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
