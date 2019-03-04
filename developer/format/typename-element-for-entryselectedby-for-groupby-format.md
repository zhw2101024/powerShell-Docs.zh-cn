---
title: GroupBy （格式） 的 EntrySelectedBy 的 TypeName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861663"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="ddbf4-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ddbf4-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="ddbf4-103">指定将使用自定义控件的此定义的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="ddbf4-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="ddbf4-104">定义如何显示一组新对象时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="ddbf4-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="ddbf4-105">GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素CustomControl EntrySelectedBy 为 GroupBy （格式） 的 GroupBy （格式） TypeName 元素 CustomEntry GroupBy （格式） EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="ddbf4-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ddbf4-106">语法</span><span class="sxs-lookup"><span data-stu-id="ddbf4-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ddbf4-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="ddbf4-107">Attributes and Elements</span></span>

<span data-ttu-id="ddbf4-108">以下各节描述了特性、 子元素和父元素的`TypeName`元素。</span><span class="sxs-lookup"><span data-stu-id="ddbf4-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ddbf4-109">特性</span><span class="sxs-lookup"><span data-stu-id="ddbf4-109">Attributes</span></span>

<span data-ttu-id="ddbf4-110">无。</span><span class="sxs-lookup"><span data-stu-id="ddbf4-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ddbf4-111">子元素</span><span class="sxs-lookup"><span data-stu-id="ddbf4-111">Child Elements</span></span>

<span data-ttu-id="ddbf4-112">无。</span><span class="sxs-lookup"><span data-stu-id="ddbf4-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ddbf4-113">父元素</span><span class="sxs-lookup"><span data-stu-id="ddbf4-113">Parent Elements</span></span>

|<span data-ttu-id="ddbf4-114">元素</span><span class="sxs-lookup"><span data-stu-id="ddbf4-114">Element</span></span>|<span data-ttu-id="ddbf4-115">描述</span><span class="sxs-lookup"><span data-stu-id="ddbf4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ddbf4-116">GroupBy （格式） 的 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="ddbf4-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="ddbf4-117">定义使用此控件定义或要使用此定义中必须存在的条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="ddbf4-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ddbf4-118">文本值</span><span class="sxs-lookup"><span data-stu-id="ddbf4-118">Text Value</span></span>

<span data-ttu-id="ddbf4-119">指定.NET 类型的完全限定的名称，例如`System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="ddbf4-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="ddbf4-120">备注</span><span class="sxs-lookup"><span data-stu-id="ddbf4-120">Remarks</span></span>

<span data-ttu-id="ddbf4-121">每个控件定义必须至少一个类型名称、 选择集或定义的选择条件。</span><span class="sxs-lookup"><span data-stu-id="ddbf4-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="ddbf4-122">有关组件的自定义控件视图的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="ddbf4-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ddbf4-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ddbf4-123">See Also</span></span>

[<span data-ttu-id="ddbf4-124">创建自定义控件</span><span class="sxs-lookup"><span data-stu-id="ddbf4-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="ddbf4-125">GroupBy （格式） 的 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="ddbf4-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="ddbf4-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="ddbf4-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
