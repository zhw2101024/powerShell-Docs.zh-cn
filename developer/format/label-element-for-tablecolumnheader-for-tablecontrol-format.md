---
title: TableControl （格式） 的使用的 TableColumnHeader 标签元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054503"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="a938f-102">Label Element for TableColumnHeader for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="a938f-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="a938f-103">定义显示在某一列顶部的标签。</span><span class="sxs-lookup"><span data-stu-id="a938f-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="a938f-104">定义表视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="a938f-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="a938f-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableHeaders 元素 TableControl （格式） 标签元素 TableHeaders TableControl （格式） TableColumnHeader 元素TableControl （格式） 的 TableColumnHeader</span><span class="sxs-lookup"><span data-stu-id="a938f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a938f-106">语法</span><span class="sxs-lookup"><span data-stu-id="a938f-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="a938f-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="a938f-107">Attributes and Elements</span></span>

<span data-ttu-id="a938f-108">以下各节描述了特性、 子元素和父元素的`Label`元素。</span><span class="sxs-lookup"><span data-stu-id="a938f-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="a938f-109">每个列所允许只有一个标签。</span><span class="sxs-lookup"><span data-stu-id="a938f-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="a938f-110">属性</span><span class="sxs-lookup"><span data-stu-id="a938f-110">Attributes</span></span>

<span data-ttu-id="a938f-111">无。</span><span class="sxs-lookup"><span data-stu-id="a938f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a938f-112">子元素</span><span class="sxs-lookup"><span data-stu-id="a938f-112">Child Elements</span></span>

<span data-ttu-id="a938f-113">无。</span><span class="sxs-lookup"><span data-stu-id="a938f-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a938f-114">父元素</span><span class="sxs-lookup"><span data-stu-id="a938f-114">Parent Elements</span></span>

|<span data-ttu-id="a938f-115">元素</span><span class="sxs-lookup"><span data-stu-id="a938f-115">Element</span></span>|<span data-ttu-id="a938f-116">说明</span><span class="sxs-lookup"><span data-stu-id="a938f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a938f-117">TableControl （格式） 的 TableHeaders TableColumnHeader 元素</span><span class="sxs-lookup"><span data-stu-id="a938f-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="a938f-118">定义标签、 宽度和表的列的数据的对齐方式。</span><span class="sxs-lookup"><span data-stu-id="a938f-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a938f-119">文本值</span><span class="sxs-lookup"><span data-stu-id="a938f-119">Text Value</span></span>

<span data-ttu-id="a938f-120">指定的表的列的顶部显示的文本。</span><span class="sxs-lookup"><span data-stu-id="a938f-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="a938f-121">有无受限的字符的列标签。</span><span class="sxs-lookup"><span data-stu-id="a938f-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="a938f-122">备注</span><span class="sxs-lookup"><span data-stu-id="a938f-122">Remarks</span></span>

<span data-ttu-id="a938f-123">如果未不指定任何标签，则使用其值显示在行中的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="a938f-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="a938f-124">表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="a938f-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a938f-125">示例</span><span class="sxs-lookup"><span data-stu-id="a938f-125">Example</span></span>

<span data-ttu-id="a938f-126">此示例显示了`TableColumnHeader`其标签为"列 1"的元素。</span><span class="sxs-lookup"><span data-stu-id="a938f-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="a938f-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a938f-127">See Also</span></span>

[<span data-ttu-id="a938f-128">创建表视图</span><span class="sxs-lookup"><span data-stu-id="a938f-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a938f-129">TableColumnHeader 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="a938f-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="a938f-130">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="a938f-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
