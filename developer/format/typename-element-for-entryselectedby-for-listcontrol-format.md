---
title: TypeName 元素 ListControl （格式） 的 EntrySelectedBy |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 0f7216d4dcc0380bceb47ea7c15b3d4a7e5ceeb2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084022"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="665f3-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="665f3-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="665f3-103">指定使用此项的列表视图中的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="665f3-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="665f3-104">可以指定列表项的类型的数量没有限制。</span><span class="sxs-lookup"><span data-stu-id="665f3-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="665f3-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 （格式） ListEntry 元素 （格式） EntrySelectedBy 元素 ListEntry （格式） TypeName 元素EntrySelectedBy 的 ListControl （格式）</span><span class="sxs-lookup"><span data-stu-id="665f3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="665f3-106">语法</span><span class="sxs-lookup"><span data-stu-id="665f3-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="665f3-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="665f3-107">Attributes and Elements</span></span>

<span data-ttu-id="665f3-108">以下各节描述了特性、 子元素和父元素的`TypeName`元素。</span><span class="sxs-lookup"><span data-stu-id="665f3-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="665f3-109">属性</span><span class="sxs-lookup"><span data-stu-id="665f3-109">Attributes</span></span>

<span data-ttu-id="665f3-110">无。</span><span class="sxs-lookup"><span data-stu-id="665f3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="665f3-111">子元素</span><span class="sxs-lookup"><span data-stu-id="665f3-111">Child Elements</span></span>

<span data-ttu-id="665f3-112">无。</span><span class="sxs-lookup"><span data-stu-id="665f3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="665f3-113">父元素</span><span class="sxs-lookup"><span data-stu-id="665f3-113">Parent Elements</span></span>

|<span data-ttu-id="665f3-114">元素</span><span class="sxs-lookup"><span data-stu-id="665f3-114">Element</span></span>|<span data-ttu-id="665f3-115">说明</span><span class="sxs-lookup"><span data-stu-id="665f3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="665f3-116">ListEntry （格式） 的 EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="665f3-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="665f3-117">定义使用此列表项或要使用此项必须存在的条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="665f3-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="665f3-118">文本值</span><span class="sxs-lookup"><span data-stu-id="665f3-118">Text Value</span></span>

<span data-ttu-id="665f3-119">指定.NET 类型的完全限定名称，例如`System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="665f3-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="665f3-120">备注</span><span class="sxs-lookup"><span data-stu-id="665f3-120">Remarks</span></span>

<span data-ttu-id="665f3-121">每个列表项必须具有至少一个类型名称、 选择集或定义的选择条件。</span><span class="sxs-lookup"><span data-stu-id="665f3-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="665f3-122">有关如何在列表视图中使用此元素的详细信息，请参阅[列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="665f3-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="665f3-123">示例</span><span class="sxs-lookup"><span data-stu-id="665f3-123">Example</span></span>

<span data-ttu-id="665f3-124">下面的示例演示如何以指定的选项集列表视图的条目。</span><span class="sxs-lookup"><span data-stu-id="665f3-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="665f3-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="665f3-125">See Also</span></span>

[<span data-ttu-id="665f3-126">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="665f3-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="665f3-127">ListEntry （格式） 的 EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="665f3-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="665f3-128">ListEntry （格式） 的 EntrySelectedBy SelectionSetName 元素</span><span class="sxs-lookup"><span data-stu-id="665f3-128">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="665f3-129">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="665f3-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
