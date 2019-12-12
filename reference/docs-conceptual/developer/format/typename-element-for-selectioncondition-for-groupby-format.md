---
title: 对于 GroupBy，为 SelectionCondition 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 290d38e3-b9bd-4382-9671-2e28b32b7260
caps.latest.revision: 6
ms.openlocfilehash: a4036b1e9de85da7e0029e02cca9e0eaed462f70
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361476"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a><span data-ttu-id="1d21a-102">TypeName Element for SelectionCondition for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="1d21a-102">TypeName Element for SelectionCondition for GroupBy (Format)</span></span>

<span data-ttu-id="1d21a-103">指定触发条件的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="1d21a-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="1d21a-104">此元素在定义如何显示新的对象组时使用。</span><span class="sxs-lookup"><span data-stu-id="1d21a-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="1d21a-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）CustomControl for groupby （format） EntrySelectedBy 元素 for CustomEntry for groupby （format） SelectionCondition 元素 for EntrySelectedBy for groupby （format） TypeName 元素 for groupby （Format）</span><span class="sxs-lookup"><span data-stu-id="1d21a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format) TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1d21a-106">语法</span><span class="sxs-lookup"><span data-stu-id="1d21a-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="1d21a-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="1d21a-107">Attributes and Elements</span></span>

<span data-ttu-id="1d21a-108">以下各节介绍了 `TypeName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1d21a-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1d21a-109">属性</span><span class="sxs-lookup"><span data-stu-id="1d21a-109">Attributes</span></span>

<span data-ttu-id="1d21a-110">无。</span><span class="sxs-lookup"><span data-stu-id="1d21a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1d21a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="1d21a-111">Child Elements</span></span>

<span data-ttu-id="1d21a-112">无。</span><span class="sxs-lookup"><span data-stu-id="1d21a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1d21a-113">父元素</span><span class="sxs-lookup"><span data-stu-id="1d21a-113">Parent Elements</span></span>

|<span data-ttu-id="1d21a-114">元素</span><span class="sxs-lookup"><span data-stu-id="1d21a-114">Element</span></span>|<span data-ttu-id="1d21a-115">描述</span><span class="sxs-lookup"><span data-stu-id="1d21a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1d21a-116">GroupBy 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1d21a-116">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="1d21a-117">定义要使用的控件定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="1d21a-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1d21a-118">文本值</span><span class="sxs-lookup"><span data-stu-id="1d21a-118">Text Value</span></span>

<span data-ttu-id="1d21a-119">指定 .NET 类型的完全限定名，如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="1d21a-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="1d21a-120">备注</span><span class="sxs-lookup"><span data-stu-id="1d21a-120">Remarks</span></span>

<span data-ttu-id="1d21a-121">如果指定此元素，则不能指定 `SelectionSetName` 元素。</span><span class="sxs-lookup"><span data-stu-id="1d21a-121">When this element is specified, you cannot specify the `SelectionSetName` element.</span></span> <span data-ttu-id="1d21a-122">有关定义选择条件的详细信息，请参阅[定义用于显示数据的条件](./defining-conditions-for-displaying-data.md)。</span><span class="sxs-lookup"><span data-stu-id="1d21a-122">For more information about defining selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d21a-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d21a-123">See Also</span></span>

[<span data-ttu-id="1d21a-124">GroupBy 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="1d21a-124">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="1d21a-125">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="1d21a-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
