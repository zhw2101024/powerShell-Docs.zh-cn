---
title: TableControl （格式） 的 EntrySelectedBy 的 TypeName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd872ada-d476-4c4d-a788-ccac3f983070
caps.latest.revision: 10
ms.openlocfilehash: 7bbb47268a23fcb37a34e2287a6ce949313a13bb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083954"
---
# <a name="typename-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="bbe51-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="bbe51-102">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="bbe51-103">指定使用此项的表视图的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="bbe51-103">Specifies a .NET type that uses this entry of the table view.</span></span> <span data-ttu-id="bbe51-104">可以为表条目指定的类型的数量没有限制。</span><span class="sxs-lookup"><span data-stu-id="bbe51-104">There is no limit to the number of types that can be specified for a table entry.</span></span>

<span data-ttu-id="bbe51-105">元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） TableControl 元素 （格式） TableRowEntries 元素 （格式） TableRowEntry 元素 （格式） EntrySelectedBy 元素 （格式） 类型名称的配置元素 EntrySelectedBy有关 TableRowEntry （格式）</span><span class="sxs-lookup"><span data-stu-id="bbe51-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) TypeName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bbe51-106">语法</span><span class="sxs-lookup"><span data-stu-id="bbe51-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bbe51-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="bbe51-107">Attributes and Elements</span></span>

<span data-ttu-id="bbe51-108">以下各节描述了特性、 子元素和父元素的`TypeName`元素。</span><span class="sxs-lookup"><span data-stu-id="bbe51-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="bbe51-109">属性</span><span class="sxs-lookup"><span data-stu-id="bbe51-109">Attributes</span></span>

<span data-ttu-id="bbe51-110">无。</span><span class="sxs-lookup"><span data-stu-id="bbe51-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bbe51-111">子元素</span><span class="sxs-lookup"><span data-stu-id="bbe51-111">Child Elements</span></span>

<span data-ttu-id="bbe51-112">无。</span><span class="sxs-lookup"><span data-stu-id="bbe51-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bbe51-113">父元素</span><span class="sxs-lookup"><span data-stu-id="bbe51-113">Parent Elements</span></span>

|<span data-ttu-id="bbe51-114">元素</span><span class="sxs-lookup"><span data-stu-id="bbe51-114">Element</span></span>|<span data-ttu-id="bbe51-115">说明</span><span class="sxs-lookup"><span data-stu-id="bbe51-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bbe51-116">EntrySelectedBy 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="bbe51-116">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="bbe51-117">定义使用此项或要使用此项必须存在的条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="bbe51-117">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="bbe51-118">文本值</span><span class="sxs-lookup"><span data-stu-id="bbe51-118">Text Value</span></span>

<span data-ttu-id="bbe51-119">指定.NET 类型的名称。</span><span class="sxs-lookup"><span data-stu-id="bbe51-119">Specify the name of the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="bbe51-120">备注</span><span class="sxs-lookup"><span data-stu-id="bbe51-120">Remarks</span></span>

<span data-ttu-id="bbe51-121">每个列表项必须具有至少一个类型名称、 选择集或定义的选择条件。</span><span class="sxs-lookup"><span data-stu-id="bbe51-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="bbe51-122">表视图的组件的详细信息，请参阅[创建表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="bbe51-122">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bbe51-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bbe51-123">See Also</span></span>

[<span data-ttu-id="bbe51-124">创建表视图</span><span class="sxs-lookup"><span data-stu-id="bbe51-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="bbe51-125">EntrySelectedBy 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="bbe51-125">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="bbe51-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="bbe51-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
