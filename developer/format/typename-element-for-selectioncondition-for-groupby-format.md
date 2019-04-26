---
title: GroupBy （格式） 的 SelectionCondition 的 TypeName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083767"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="10bc5-102">TypeName Element for SelectionCondition for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="10bc5-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="10bc5-103">指定触发条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="10bc5-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="10bc5-104">定义如何显示一组新对象时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="10bc5-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="10bc5-105">GroupBy （格式） 的 GroupBy （格式） CustomEntry 元素 CustomControl CustomEntries 元素的视图 （格式） CustomControl 元素的配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） GroupBy 元素CustomControl SelectionCondition 为 GroupBy （格式） 的 GroupBy （格式） TypeName 元素 EntrySelectedBy GroupBy （格式） SelectionCondition 元素 CustomEntry GroupBy （格式） EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="10bc5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="10bc5-106">语法</span><span class="sxs-lookup"><span data-stu-id="10bc5-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="10bc5-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="10bc5-107">Attributes and Elements</span></span>

<span data-ttu-id="10bc5-108">以下各节描述了特性、 子元素和父元素的`TypeName`元素。</span><span class="sxs-lookup"><span data-stu-id="10bc5-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="10bc5-109">属性</span><span class="sxs-lookup"><span data-stu-id="10bc5-109">Attributes</span></span>

<span data-ttu-id="10bc5-110">无。</span><span class="sxs-lookup"><span data-stu-id="10bc5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="10bc5-111">子元素</span><span class="sxs-lookup"><span data-stu-id="10bc5-111">Child Elements</span></span>

<span data-ttu-id="10bc5-112">无。</span><span class="sxs-lookup"><span data-stu-id="10bc5-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="10bc5-113">父元素</span><span class="sxs-lookup"><span data-stu-id="10bc5-113">Parent Elements</span></span>

|<span data-ttu-id="10bc5-114">元素</span><span class="sxs-lookup"><span data-stu-id="10bc5-114">Element</span></span>|<span data-ttu-id="10bc5-115">说明</span><span class="sxs-lookup"><span data-stu-id="10bc5-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="10bc5-116">GroupBy （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="10bc5-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="10bc5-117">定义必须存在要使用的控件定义的条件。</span><span class="sxs-lookup"><span data-stu-id="10bc5-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="10bc5-118">文本值</span><span class="sxs-lookup"><span data-stu-id="10bc5-118">Text Value</span></span>

<span data-ttu-id="10bc5-119">指定.NET 类型的完全限定的名称，例如`System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="10bc5-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="10bc5-120">备注</span><span class="sxs-lookup"><span data-stu-id="10bc5-120">Remarks</span></span>

<span data-ttu-id="10bc5-121">当指定此元素时，不能指定`SelectionSetName`元素。</span><span class="sxs-lookup"><span data-stu-id="10bc5-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="10bc5-122">有关定义选择条件的详细信息，请参阅[定义显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="10bc5-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="10bc5-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="10bc5-123">See Also</span></span>

[<span data-ttu-id="10bc5-124">GroupBy （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="10bc5-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="10bc5-125">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="10bc5-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
