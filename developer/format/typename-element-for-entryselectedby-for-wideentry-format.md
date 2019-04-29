---
title: TypeName 元素 WideEntry （格式） 的 EntrySelectedBy |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083920"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="f4adf-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f4adf-102">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="f4adf-103">指定定义的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="f4adf-103">Specifies a .NET type for the definition.</span></span> <span data-ttu-id="f4adf-104">定义用于显示此对象时。</span><span class="sxs-lookup"><span data-stu-id="f4adf-104">The definition is used whenever this object is displayed.</span></span>

<span data-ttu-id="f4adf-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） WideEntries 元素 （格式） WideEntry 元素 （格式） EntrySelectedBy 元素 WideEntry （WideEntry （格式） TypeName 元素格式）</span><span class="sxs-lookup"><span data-stu-id="f4adf-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) TypeName Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f4adf-106">语法</span><span class="sxs-lookup"><span data-stu-id="f4adf-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f4adf-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f4adf-107">Attributes and Elements</span></span>

<span data-ttu-id="f4adf-108">以下各节描述了特性、 子元素和父元素的`TypeName`元素。</span><span class="sxs-lookup"><span data-stu-id="f4adf-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f4adf-109">属性</span><span class="sxs-lookup"><span data-stu-id="f4adf-109">Attributes</span></span>

<span data-ttu-id="f4adf-110">无。</span><span class="sxs-lookup"><span data-stu-id="f4adf-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f4adf-111">子元素</span><span class="sxs-lookup"><span data-stu-id="f4adf-111">Child Elements</span></span>

<span data-ttu-id="f4adf-112">无。</span><span class="sxs-lookup"><span data-stu-id="f4adf-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f4adf-113">父元素</span><span class="sxs-lookup"><span data-stu-id="f4adf-113">Parent Elements</span></span>

|<span data-ttu-id="f4adf-114">元素</span><span class="sxs-lookup"><span data-stu-id="f4adf-114">Element</span></span>|<span data-ttu-id="f4adf-115">说明</span><span class="sxs-lookup"><span data-stu-id="f4adf-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f4adf-116">WideEntry （格式） 的 EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="f4adf-116">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="f4adf-117">定义使用此宽的项或要使用此项必须存在的条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="f4adf-117">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f4adf-118">文本值</span><span class="sxs-lookup"><span data-stu-id="f4adf-118">Text Value</span></span>

<span data-ttu-id="f4adf-119">指定.NET 类型的完全限定的名称，例如`System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="f4adf-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="f4adf-120">备注</span><span class="sxs-lookup"><span data-stu-id="f4adf-120">Remarks</span></span>

<span data-ttu-id="f4adf-121">每个宽的条目都必须指定一个或多个.NET 类型、 一个选择集或要使用的定义中必须存在的选择条件。</span><span class="sxs-lookup"><span data-stu-id="f4adf-121">Each wide entry must specify one or more .NET types, a selection set, or the selection condition that must exist for the definition to be used.</span></span>

<span data-ttu-id="f4adf-122">有关较宽的视图的其他组件的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="f4adf-122">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f4adf-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f4adf-123">See Also</span></span>

[<span data-ttu-id="f4adf-124">创建较宽的视图</span><span class="sxs-lookup"><span data-stu-id="f4adf-124">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="f4adf-125">WideEntry （格式） 的 EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="f4adf-125">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="f4adf-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="f4adf-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
