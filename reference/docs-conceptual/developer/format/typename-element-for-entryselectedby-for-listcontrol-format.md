---
title: ListControl 的 EntrySelectedBy 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33c7345c-b808-4c1e-bd54-cb870b407432
caps.latest.revision: 14
ms.openlocfilehash: 0f7216d4dcc0380bceb47ea7c15b3d4a7e5ceeb2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361656"
---
# <a name="typename-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="c20dc-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c20dc-102">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="c20dc-103">指定使用此列表视图项的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="c20dc-103">Specifies a .NET type that uses this entry of the list view.</span></span> <span data-ttu-id="c20dc-104">对于列表项可以指定的类型数量没有限制。</span><span class="sxs-lookup"><span data-stu-id="c20dc-104">There is no limit to the number of types that can be specified for a list entry.</span></span>

<span data-ttu-id="c20dc-105">配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） ListControl 元素（格式） ListEntries 元素（格式） ListEntry 元素（format） EntrySelectedBy 元素 for ListEntry （Format） TypeName 元素 forEntrySelectedBy for ListControl （Format）</span><span class="sxs-lookup"><span data-stu-id="c20dc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c20dc-106">语法</span><span class="sxs-lookup"><span data-stu-id="c20dc-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c20dc-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="c20dc-107">Attributes and Elements</span></span>

<span data-ttu-id="c20dc-108">以下各节介绍了 `TypeName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c20dc-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c20dc-109">属性</span><span class="sxs-lookup"><span data-stu-id="c20dc-109">Attributes</span></span>

<span data-ttu-id="c20dc-110">无。</span><span class="sxs-lookup"><span data-stu-id="c20dc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c20dc-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c20dc-111">Child Elements</span></span>

<span data-ttu-id="c20dc-112">无。</span><span class="sxs-lookup"><span data-stu-id="c20dc-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c20dc-113">父元素</span><span class="sxs-lookup"><span data-stu-id="c20dc-113">Parent Elements</span></span>

|<span data-ttu-id="c20dc-114">元素</span><span class="sxs-lookup"><span data-stu-id="c20dc-114">Element</span></span>|<span data-ttu-id="c20dc-115">描述</span><span class="sxs-lookup"><span data-stu-id="c20dc-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c20dc-116">ListEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c20dc-116">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="c20dc-117">定义使用此列表项的 .NET 类型或此项要使用的条件。</span><span class="sxs-lookup"><span data-stu-id="c20dc-117">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c20dc-118">文本值</span><span class="sxs-lookup"><span data-stu-id="c20dc-118">Text Value</span></span>

<span data-ttu-id="c20dc-119">指定 .NET 类型的完全限定名称，如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="c20dc-119">Specify the fully-qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="c20dc-120">备注</span><span class="sxs-lookup"><span data-stu-id="c20dc-120">Remarks</span></span>

<span data-ttu-id="c20dc-121">每个列表项必须至少定义一个类型名称、选择集或选择条件。</span><span class="sxs-lookup"><span data-stu-id="c20dc-121">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="c20dc-122">有关如何在列表视图中使用此元素的详细信息，请参阅[列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="c20dc-122">For more information about how this element is used in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c20dc-123">示例</span><span class="sxs-lookup"><span data-stu-id="c20dc-123">Example</span></span>

<span data-ttu-id="c20dc-124">下面的示例演示如何为列表视图的条目指定选择集。</span><span class="sxs-lookup"><span data-stu-id="c20dc-124">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>Nameof.NetType</TypeName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="c20dc-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c20dc-125">See Also</span></span>

[<span data-ttu-id="c20dc-126">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="c20dc-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c20dc-127">ListEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c20dc-127">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="c20dc-128">ListEntry 的 EntrySelectedBy 的 SelectionSetName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="c20dc-128">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="c20dc-129">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="c20dc-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
