---
title: TableControl 的 TableColumnItem 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362246"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="c8535-102">PropertyName Element for TableColumnItem for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c8535-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="c8535-103">指定其值显示在行的列中的属性。</span><span class="sxs-lookup"><span data-stu-id="c8535-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="c8535-104">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（格式） TableColumnItems 元素（格式） TableColumnItem 元素（格式）TableColumnItem 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="c8535-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c8535-105">语法</span><span class="sxs-lookup"><span data-stu-id="c8535-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c8535-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="c8535-106">Attributes and Elements</span></span>

<span data-ttu-id="c8535-107">以下各节介绍 `PropertyName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c8535-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c8535-108">属性</span><span class="sxs-lookup"><span data-stu-id="c8535-108">Attributes</span></span>

<span data-ttu-id="c8535-109">无。</span><span class="sxs-lookup"><span data-stu-id="c8535-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c8535-110">子元素</span><span class="sxs-lookup"><span data-stu-id="c8535-110">Child Elements</span></span>

<span data-ttu-id="c8535-111">无。</span><span class="sxs-lookup"><span data-stu-id="c8535-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c8535-112">父元素</span><span class="sxs-lookup"><span data-stu-id="c8535-112">Parent Elements</span></span>

|<span data-ttu-id="c8535-113">元素</span><span class="sxs-lookup"><span data-stu-id="c8535-113">Element</span></span>|<span data-ttu-id="c8535-114">描述</span><span class="sxs-lookup"><span data-stu-id="c8535-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c8535-115">TableColumnItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c8535-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="c8535-116">定义其值显示在行的列中的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="c8535-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c8535-117">文本值</span><span class="sxs-lookup"><span data-stu-id="c8535-117">Text Value</span></span>

<span data-ttu-id="c8535-118">指定显示其值的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="c8535-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="c8535-119">备注</span><span class="sxs-lookup"><span data-stu-id="c8535-119">Remarks</span></span>

<span data-ttu-id="c8535-120">有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="c8535-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c8535-121">示例</span><span class="sxs-lookup"><span data-stu-id="c8535-121">Example</span></span>

<span data-ttu-id="c8535-122">此示例演示一个 @no__t 0 元素，该元素指定了[system.exception 对象的](/dotnet/api/System.Diagnostics.Process)@no__t 属性。</span><span class="sxs-lookup"><span data-stu-id="c8535-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="c8535-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c8535-123">See Also</span></span>

[<span data-ttu-id="c8535-124">创建表视图</span><span class="sxs-lookup"><span data-stu-id="c8535-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c8535-125">TableColumnItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c8535-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="c8535-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="c8535-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
