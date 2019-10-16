---
title: 用于配置（格式）的控件的 SelectionCondition 的 TypeName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 477c8711-fffc-4f92-af45-6d4f80990474
caps.latest.revision: 7
ms.openlocfilehash: 60f02f3240c5574e1b1f9027b060bd9af89a11d2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361606"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="927cd-102">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="927cd-102">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="927cd-103">指定触发条件的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="927cd-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="927cd-104">此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。</span><span class="sxs-lookup"><span data-stu-id="927cd-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="927cd-105">Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，用于控件的配置（format） CustomEntries 元素，用于 CustomControl 的控件配置（format） CustomEntry 元素 for CustomControl for EntrySelectedBy 元素 for CustomEntry for 元素 for for SelectionCondition for EntrySelectedBy 的 CustomEntry 元素配置（格式）用于配置的控件的 SelectionCondition 的 TypeName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="927cd-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="927cd-106">语法</span><span class="sxs-lookup"><span data-stu-id="927cd-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="927cd-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="927cd-107">Attributes and Elements</span></span>

<span data-ttu-id="927cd-108">以下各节介绍了 `TypeName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="927cd-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="927cd-109">属性</span><span class="sxs-lookup"><span data-stu-id="927cd-109">Attributes</span></span>

<span data-ttu-id="927cd-110">无。</span><span class="sxs-lookup"><span data-stu-id="927cd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="927cd-111">子元素</span><span class="sxs-lookup"><span data-stu-id="927cd-111">Child Elements</span></span>

<span data-ttu-id="927cd-112">无。</span><span class="sxs-lookup"><span data-stu-id="927cd-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="927cd-113">父元素</span><span class="sxs-lookup"><span data-stu-id="927cd-113">Parent Elements</span></span>

|<span data-ttu-id="927cd-114">元素</span><span class="sxs-lookup"><span data-stu-id="927cd-114">Element</span></span>|<span data-ttu-id="927cd-115">描述</span><span class="sxs-lookup"><span data-stu-id="927cd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="927cd-116">用于配置的 CustomEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="927cd-116">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="927cd-117">定义要使用的控件定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="927cd-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="927cd-118">文本值</span><span class="sxs-lookup"><span data-stu-id="927cd-118">Text Value</span></span>

<span data-ttu-id="927cd-119">指定 .NET 类型的完全限定名，如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="927cd-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="927cd-120">备注</span><span class="sxs-lookup"><span data-stu-id="927cd-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="927cd-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="927cd-121">See Also</span></span>

[<span data-ttu-id="927cd-122">用于配置的 CustomEntry 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="927cd-122">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="927cd-123">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="927cd-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
