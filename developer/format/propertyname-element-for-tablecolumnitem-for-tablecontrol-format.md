---
title: TableControl （格式） 的 TableColumnItem PropertyName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064594"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="b579c-102">PropertyName Element for TableColumnItem for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b579c-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="b579c-103">指定其值显示在一行的列中的属性。</span><span class="sxs-lookup"><span data-stu-id="b579c-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="b579c-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 （格式） TableRowEntry 元素 （格式） TableColumnItems 元素 （格式） TableColumnItem 元素 （格式）TableColumnItem （格式） 的属性名称元素</span><span class="sxs-lookup"><span data-stu-id="b579c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b579c-105">语法</span><span class="sxs-lookup"><span data-stu-id="b579c-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b579c-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b579c-106">Attributes and Elements</span></span>

<span data-ttu-id="b579c-107">以下各节描述了特性、 子元素和父元素的`PropertyName`元素。</span><span class="sxs-lookup"><span data-stu-id="b579c-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b579c-108">属性</span><span class="sxs-lookup"><span data-stu-id="b579c-108">Attributes</span></span>

<span data-ttu-id="b579c-109">无。</span><span class="sxs-lookup"><span data-stu-id="b579c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b579c-110">子元素</span><span class="sxs-lookup"><span data-stu-id="b579c-110">Child Elements</span></span>

<span data-ttu-id="b579c-111">无。</span><span class="sxs-lookup"><span data-stu-id="b579c-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b579c-112">父元素</span><span class="sxs-lookup"><span data-stu-id="b579c-112">Parent Elements</span></span>

|<span data-ttu-id="b579c-113">元素</span><span class="sxs-lookup"><span data-stu-id="b579c-113">Element</span></span>|<span data-ttu-id="b579c-114">说明</span><span class="sxs-lookup"><span data-stu-id="b579c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b579c-115">TableColumnItem 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b579c-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="b579c-116">定义属性或其值显示在一行的列中的脚本。</span><span class="sxs-lookup"><span data-stu-id="b579c-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b579c-117">文本值</span><span class="sxs-lookup"><span data-stu-id="b579c-117">Text Value</span></span>

<span data-ttu-id="b579c-118">指定显示其值的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="b579c-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="b579c-119">备注</span><span class="sxs-lookup"><span data-stu-id="b579c-119">Remarks</span></span>

<span data-ttu-id="b579c-120">表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="b579c-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b579c-121">示例</span><span class="sxs-lookup"><span data-stu-id="b579c-121">Example</span></span>

<span data-ttu-id="b579c-122">此示例演示`TableColumnItem`指定的元素`Status`的属性[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象。</span><span class="sxs-lookup"><span data-stu-id="b579c-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="b579c-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b579c-123">See Also</span></span>

[<span data-ttu-id="b579c-124">创建表视图</span><span class="sxs-lookup"><span data-stu-id="b579c-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b579c-125">TableColumnItem 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b579c-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="b579c-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="b579c-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
