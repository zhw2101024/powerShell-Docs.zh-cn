---
title: 用于视图（格式）的控件的 EntrySelectedBy 的 TypeName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 52003450-07ca-41e5-b075-8b6b03fc6e88
caps.latest.revision: 6
ms.openlocfilehash: 30215734ef832d778b08d3d7be224ff8d88b0579
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361776"
---
# <a name="typename-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="a8333-102">TypeName Element for EntrySelectedBy for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="a8333-102">TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="a8333-103">指定使用控件的此定义的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="a8333-103">Specifies a .NET type that uses this definition of the control.</span></span> <span data-ttu-id="a8333-104">定义可由视图使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="a8333-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="a8333-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 元素（format） Control 元素 for View （format） CustomControl 元素的控件元素，用于控件的 View （format） CustomEntries 元素View （format） CustomEntry 元素的 CustomControl for view （format）元素 for CustomEntries for view （format）</span><span class="sxs-lookup"><span data-stu-id="a8333-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) TypeName Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a8333-106">语法</span><span class="sxs-lookup"><span data-stu-id="a8333-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="a8333-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="a8333-107">Attributes and Elements</span></span>

<span data-ttu-id="a8333-108">以下各节介绍了 `TypeName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a8333-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a8333-109">属性</span><span class="sxs-lookup"><span data-stu-id="a8333-109">Attributes</span></span>

<span data-ttu-id="a8333-110">无。</span><span class="sxs-lookup"><span data-stu-id="a8333-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a8333-111">子元素</span><span class="sxs-lookup"><span data-stu-id="a8333-111">Child Elements</span></span>

<span data-ttu-id="a8333-112">无。</span><span class="sxs-lookup"><span data-stu-id="a8333-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a8333-113">父元素</span><span class="sxs-lookup"><span data-stu-id="a8333-113">Parent Elements</span></span>

|<span data-ttu-id="a8333-114">元素</span><span class="sxs-lookup"><span data-stu-id="a8333-114">Element</span></span>|<span data-ttu-id="a8333-115">描述</span><span class="sxs-lookup"><span data-stu-id="a8333-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a8333-116">用于视图的控件的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a8333-116">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="a8333-117">定义使用此控件定义的 .NET 类型或要使用此定义时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="a8333-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a8333-118">文本值</span><span class="sxs-lookup"><span data-stu-id="a8333-118">Text Value</span></span>

<span data-ttu-id="a8333-119">指定 .NET 类型的完全限定名，如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="a8333-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="a8333-120">备注</span><span class="sxs-lookup"><span data-stu-id="a8333-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="a8333-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a8333-121">See Also</span></span>

[<span data-ttu-id="a8333-122">用于视图的控件的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a8333-122">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="a8333-123">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="a8333-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
