---
title: 对于 GroupBy，为 EntrySelectedBy 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361666"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="5b745-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5b745-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="5b745-103">指定使用自定义控件的此定义的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="5b745-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="5b745-104">此元素在定义如何显示新的对象组时使用。</span><span class="sxs-lookup"><span data-stu-id="5b745-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="5b745-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）用于 CustomEntry for groupby （format） TypeName 元素的 CustomControl for groupby （format） EntrySelectedBy 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="5b745-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5b745-106">语法</span><span class="sxs-lookup"><span data-stu-id="5b745-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5b745-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="5b745-107">Attributes and Elements</span></span>

<span data-ttu-id="5b745-108">以下各节介绍了 `TypeName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5b745-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5b745-109">属性</span><span class="sxs-lookup"><span data-stu-id="5b745-109">Attributes</span></span>

<span data-ttu-id="5b745-110">无。</span><span class="sxs-lookup"><span data-stu-id="5b745-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5b745-111">子元素</span><span class="sxs-lookup"><span data-stu-id="5b745-111">Child Elements</span></span>

<span data-ttu-id="5b745-112">无。</span><span class="sxs-lookup"><span data-stu-id="5b745-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5b745-113">父元素</span><span class="sxs-lookup"><span data-stu-id="5b745-113">Parent Elements</span></span>

|<span data-ttu-id="5b745-114">元素</span><span class="sxs-lookup"><span data-stu-id="5b745-114">Element</span></span>|<span data-ttu-id="5b745-115">描述</span><span class="sxs-lookup"><span data-stu-id="5b745-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5b745-116">GroupBy 的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5b745-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="5b745-117">定义使用此控件定义的 .NET 类型或要使用此定义时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="5b745-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5b745-118">文本值</span><span class="sxs-lookup"><span data-stu-id="5b745-118">Text Value</span></span>

<span data-ttu-id="5b745-119">指定 .NET 类型的完全限定名，如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="5b745-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="5b745-120">备注</span><span class="sxs-lookup"><span data-stu-id="5b745-120">Remarks</span></span>

<span data-ttu-id="5b745-121">每个控件定义都必须定义至少一个类型名称、选择集或选择条件。</span><span class="sxs-lookup"><span data-stu-id="5b745-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="5b745-122">有关自定义控件视图组件的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="5b745-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5b745-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b745-123">See Also</span></span>

[<span data-ttu-id="5b745-124">创建自定义控件</span><span class="sxs-lookup"><span data-stu-id="5b745-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="5b745-125">GroupBy 的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5b745-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="5b745-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="5b745-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
