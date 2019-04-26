---
title: TableControl （格式） 的 TableColumnHeader 的 width 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083614"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="10336-102">Width Element for TableColumnHeader for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="10336-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="10336-103">定义列的宽度 （以字符为单位）。</span><span class="sxs-lookup"><span data-stu-id="10336-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="10336-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableHeaders 元素 TableControl （格式） TableColumnHeader 元素 TableHeaders TableControl （格式） 的宽度元素TableControl （格式） 的 TableColumnHeader</span><span class="sxs-lookup"><span data-stu-id="10336-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="10336-105">语法</span><span class="sxs-lookup"><span data-stu-id="10336-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="10336-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="10336-106">Attributes and Elements</span></span>

<span data-ttu-id="10336-107">以下各节描述的特性、 子元素和父元素的`Width`定义列标题时使用的元素。</span><span class="sxs-lookup"><span data-stu-id="10336-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="10336-108">属性</span><span class="sxs-lookup"><span data-stu-id="10336-108">Attributes</span></span>

<span data-ttu-id="10336-109">无。</span><span class="sxs-lookup"><span data-stu-id="10336-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="10336-110">子元素</span><span class="sxs-lookup"><span data-stu-id="10336-110">Child Elements</span></span>

<span data-ttu-id="10336-111">无。</span><span class="sxs-lookup"><span data-stu-id="10336-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="10336-112">父元素</span><span class="sxs-lookup"><span data-stu-id="10336-112">Parent Elements</span></span>

|<span data-ttu-id="10336-113">元素</span><span class="sxs-lookup"><span data-stu-id="10336-113">Element</span></span>|<span data-ttu-id="10336-114">说明</span><span class="sxs-lookup"><span data-stu-id="10336-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="10336-115">TableControl （格式） 的 TableHeaders TableColumnHeader 元素</span><span class="sxs-lookup"><span data-stu-id="10336-115">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="10336-116">定义标签、 宽度和对齐方式的表的列的数据。</span><span class="sxs-lookup"><span data-stu-id="10336-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="10336-117">文本值</span><span class="sxs-lookup"><span data-stu-id="10336-117">Text Value</span></span>

<span data-ttu-id="10336-118">在所有可能的当指定的显示的属性值的长度大于宽度 （以字符为单位）。</span><span class="sxs-lookup"><span data-stu-id="10336-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="10336-119">备注</span><span class="sxs-lookup"><span data-stu-id="10336-119">Remarks</span></span>

<span data-ttu-id="10336-120">表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="10336-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="10336-121">示例</span><span class="sxs-lookup"><span data-stu-id="10336-121">Example</span></span>

<span data-ttu-id="10336-122">下面的示例演示`TableColumnHeader`元素，其宽度为 16 个字符。</span><span class="sxs-lookup"><span data-stu-id="10336-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="10336-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="10336-123">See Also</span></span>

[<span data-ttu-id="10336-124">创建表视图</span><span class="sxs-lookup"><span data-stu-id="10336-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="10336-125">TableControl （格式） 的 TableHeader TableColumnHeader 元素</span><span class="sxs-lookup"><span data-stu-id="10336-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="10336-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="10336-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
