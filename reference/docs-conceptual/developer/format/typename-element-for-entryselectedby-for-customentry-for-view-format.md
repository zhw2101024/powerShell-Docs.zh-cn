---
title: CustomEntry 的 EntrySelectedBy 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368066"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="fb3bb-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span><span class="sxs-lookup"><span data-stu-id="fb3bb-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="fb3bb-103">指定使用自定义控件视图的此定义的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="fb3bb-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="fb3bb-104">对于可以为定义指定的类型数量没有限制。</span><span class="sxs-lookup"><span data-stu-id="fb3bb-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="fb3bb-105">用于 CustomEntry 的 CustomControl for view （format） CustomEntries 元素的配置元素（格式） ViewDefinitions 元素（格式） CustomControl 元素（format） CustomEntries 元素 EntrySelectedBy用于 CustomEntry for View （Format）的 EntrySelectedBy 的 CustomEntry for View （Format） TypeName 元素的元素</span><span class="sxs-lookup"><span data-stu-id="fb3bb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fb3bb-106">语法</span><span class="sxs-lookup"><span data-stu-id="fb3bb-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fb3bb-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="fb3bb-107">Attributes and Elements</span></span>

<span data-ttu-id="fb3bb-108">以下各节介绍了 `TypeName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fb3bb-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fb3bb-109">属性</span><span class="sxs-lookup"><span data-stu-id="fb3bb-109">Attributes</span></span>

<span data-ttu-id="fb3bb-110">无。</span><span class="sxs-lookup"><span data-stu-id="fb3bb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fb3bb-111">子元素</span><span class="sxs-lookup"><span data-stu-id="fb3bb-111">Child Elements</span></span>

<span data-ttu-id="fb3bb-112">无。</span><span class="sxs-lookup"><span data-stu-id="fb3bb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fb3bb-113">父元素</span><span class="sxs-lookup"><span data-stu-id="fb3bb-113">Parent Elements</span></span>

|<span data-ttu-id="fb3bb-114">元素</span><span class="sxs-lookup"><span data-stu-id="fb3bb-114">Element</span></span>|<span data-ttu-id="fb3bb-115">描述</span><span class="sxs-lookup"><span data-stu-id="fb3bb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fb3bb-116">用于视图的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fb3bb-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="fb3bb-117">定义使用此自定义控件视图定义或要使用此定义必须存在的条件的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="fb3bb-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="fb3bb-118">文本值</span><span class="sxs-lookup"><span data-stu-id="fb3bb-118">Text Value</span></span>

<span data-ttu-id="fb3bb-119">指定 .NET 类型的完全限定名，如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="fb3bb-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="fb3bb-120">备注</span><span class="sxs-lookup"><span data-stu-id="fb3bb-120">Remarks</span></span>

<span data-ttu-id="fb3bb-121">每个自定义控件视图定义都必须定义至少一个类型名称、选择集或选择条件。</span><span class="sxs-lookup"><span data-stu-id="fb3bb-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="fb3bb-122">有关自定义控件视图组件的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="fb3bb-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fb3bb-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fb3bb-123">See Also</span></span>

[<span data-ttu-id="fb3bb-124">创建自定义控件</span><span class="sxs-lookup"><span data-stu-id="fb3bb-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="fb3bb-125">用于视图的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fb3bb-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="fb3bb-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="fb3bb-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
