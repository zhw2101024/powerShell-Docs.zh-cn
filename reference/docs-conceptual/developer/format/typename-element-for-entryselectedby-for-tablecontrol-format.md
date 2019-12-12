---
title: TableControl 的 EntrySelectedBy 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361626"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="047c7-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="047c7-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="047c7-103">指定使用此表视图项的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="047c7-103">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="047c7-104">对于可为表条目指定的类型数量没有限制。</span><span class="sxs-lookup"><span data-stu-id="047c7-104">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="047c7-105">用于 EntrySelectedBy 的配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） TableControl 元素（格式） TableRowEntries 元素（格式） TableRowEntry 元素（格式） EntrySelectedBy 元素（格式） TypeName 元素对于 TableRowEntry （格式）</span><span class="sxs-lookup"><span data-stu-id="047c7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="047c7-106">语法</span><span class="sxs-lookup"><span data-stu-id="047c7-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="047c7-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="047c7-107">Attributes and Elements</span></span>

<span data-ttu-id="047c7-108">以下各节介绍了 `TypeName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="047c7-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="047c7-109">属性</span><span class="sxs-lookup"><span data-stu-id="047c7-109">Attributes</span></span>

<span data-ttu-id="047c7-110">无。</span><span class="sxs-lookup"><span data-stu-id="047c7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="047c7-111">子元素</span><span class="sxs-lookup"><span data-stu-id="047c7-111">Child Elements</span></span>

<span data-ttu-id="047c7-112">无。</span><span class="sxs-lookup"><span data-stu-id="047c7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="047c7-113">父元素</span><span class="sxs-lookup"><span data-stu-id="047c7-113">Parent Elements</span></span>

|<span data-ttu-id="047c7-114">元素</span><span class="sxs-lookup"><span data-stu-id="047c7-114">Element</span></span>|<span data-ttu-id="047c7-115">描述</span><span class="sxs-lookup"><span data-stu-id="047c7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="047c7-116">EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="047c7-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="047c7-117">定义使用此项的 .NET 类型或此项要使用的条件。</span><span class="sxs-lookup"><span data-stu-id="047c7-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="047c7-118">文本值</span><span class="sxs-lookup"><span data-stu-id="047c7-118">Text Value</span></span>

<span data-ttu-id="047c7-119">指定 .NET 类型的名称。</span><span class="sxs-lookup"><span data-stu-id="047c7-119">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="047c7-120">备注</span><span class="sxs-lookup"><span data-stu-id="047c7-120">Remarks</span></span>

<span data-ttu-id="047c7-121">每个列表项必须至少定义一个类型名称、选择集或选择条件。</span><span class="sxs-lookup"><span data-stu-id="047c7-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="047c7-122">有关表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="047c7-122">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="047c7-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="047c7-123">See Also</span></span>

[<span data-ttu-id="047c7-124">创建表视图</span><span class="sxs-lookup"><span data-stu-id="047c7-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="047c7-125">EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="047c7-125">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="047c7-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="047c7-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
