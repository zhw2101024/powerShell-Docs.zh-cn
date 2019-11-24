---
title: TableControl 的 TableColumnHeader 的 Width 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: 4a25c9d81df670dc10955065bfb66766cdb1bd33
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367866"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="f21e7-102">Width Element for TableColumnHeader for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f21e7-102">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="f21e7-103">定义列的宽度（以字符为字符）。</span><span class="sxs-lookup"><span data-stu-id="f21e7-103">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="f21e7-104">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（format） TableHeaders 元素 for TableControl （format） TableColumnHeader 元素 TableHeaders for TableControl （Format） Width 元素TableColumnHeader for TableControl （Format）</span><span class="sxs-lookup"><span data-stu-id="f21e7-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f21e7-105">语法</span><span class="sxs-lookup"><span data-stu-id="f21e7-105">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f21e7-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="f21e7-106">Attributes and Elements</span></span>

<span data-ttu-id="f21e7-107">以下各节描述定义列标题时使用的 `Width` 元素的特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f21e7-107">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="f21e7-108">特性</span><span class="sxs-lookup"><span data-stu-id="f21e7-108">Attributes</span></span>

<span data-ttu-id="f21e7-109">无。</span><span class="sxs-lookup"><span data-stu-id="f21e7-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f21e7-110">子元素</span><span class="sxs-lookup"><span data-stu-id="f21e7-110">Child Elements</span></span>

<span data-ttu-id="f21e7-111">无。</span><span class="sxs-lookup"><span data-stu-id="f21e7-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f21e7-112">父元素</span><span class="sxs-lookup"><span data-stu-id="f21e7-112">Parent Elements</span></span>

|<span data-ttu-id="f21e7-113">元素</span><span class="sxs-lookup"><span data-stu-id="f21e7-113">Element</span></span>|<span data-ttu-id="f21e7-114">描述</span><span class="sxs-lookup"><span data-stu-id="f21e7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f21e7-115">TableControl 的 TableHeaders 的 TableColumnHeader 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f21e7-115">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="f21e7-116">定义表的列的数据的标签、宽度和对齐方式。</span><span class="sxs-lookup"><span data-stu-id="f21e7-116">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f21e7-117">文本值</span><span class="sxs-lookup"><span data-stu-id="f21e7-117">Text Value</span></span>

<span data-ttu-id="f21e7-118">如果可能，请指定大于所显示属性值长度的宽度（字符数）。</span><span class="sxs-lookup"><span data-stu-id="f21e7-118">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="f21e7-119">备注</span><span class="sxs-lookup"><span data-stu-id="f21e7-119">Remarks</span></span>

<span data-ttu-id="f21e7-120">有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="f21e7-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f21e7-121">示例</span><span class="sxs-lookup"><span data-stu-id="f21e7-121">Example</span></span>

<span data-ttu-id="f21e7-122">下面的示例演示一个宽度为16个字符的 `TableColumnHeader` 元素。</span><span class="sxs-lookup"><span data-stu-id="f21e7-122">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="f21e7-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f21e7-123">See Also</span></span>

[<span data-ttu-id="f21e7-124">创建表视图</span><span class="sxs-lookup"><span data-stu-id="f21e7-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f21e7-125">TableControl 的 TableHeader 的 TableColumnHeader 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f21e7-125">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="f21e7-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="f21e7-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
