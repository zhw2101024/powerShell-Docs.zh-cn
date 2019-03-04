---
title: 配置 （格式） 的控件的 SelectionCondition 的 TypeName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 477c8711-fffc-4f92-af45-6d4f80990474
caps.latest.revision: 7
ms.openlocfilehash: 60f02f3240c5574e1b1f9027b060bd9af89a11d2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853593"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="72f18-102">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="72f18-102">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="72f18-103">指定触发条件的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="72f18-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="72f18-104">定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。</span><span class="sxs-lookup"><span data-stu-id="72f18-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="72f18-105">配置 （格式） 的配置 （格式） 的 Controls 的 CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素配置 （格式） 的 Controls 的配置 （格式） 的 Controls 的配置 （格式） SelectionCondition 元素，用于为 CustomEntry 的 EntrySelectedBy CustomEntry EntrySelectedBy 元素 CustomControl CustomEntry 元素SelectionCondition 的 Controls 的配置 （格式） 的配置 （格式） TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="72f18-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format) TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="72f18-106">语法</span><span class="sxs-lookup"><span data-stu-id="72f18-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="72f18-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="72f18-107">Attributes and Elements</span></span>

<span data-ttu-id="72f18-108">以下各节描述了特性、 子元素和父元素的`TypeName`元素。</span><span class="sxs-lookup"><span data-stu-id="72f18-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="72f18-109">特性</span><span class="sxs-lookup"><span data-stu-id="72f18-109">Attributes</span></span>

<span data-ttu-id="72f18-110">无。</span><span class="sxs-lookup"><span data-stu-id="72f18-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="72f18-111">子元素</span><span class="sxs-lookup"><span data-stu-id="72f18-111">Child Elements</span></span>

<span data-ttu-id="72f18-112">无。</span><span class="sxs-lookup"><span data-stu-id="72f18-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="72f18-113">父元素</span><span class="sxs-lookup"><span data-stu-id="72f18-113">Parent Elements</span></span>

|<span data-ttu-id="72f18-114">元素</span><span class="sxs-lookup"><span data-stu-id="72f18-114">Element</span></span>|<span data-ttu-id="72f18-115">描述</span><span class="sxs-lookup"><span data-stu-id="72f18-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="72f18-116">为配置 （格式） 的 CustomEntry EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="72f18-116">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="72f18-117">定义必须存在要使用的控件定义的条件。</span><span class="sxs-lookup"><span data-stu-id="72f18-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="72f18-118">文本值</span><span class="sxs-lookup"><span data-stu-id="72f18-118">Text Value</span></span>

<span data-ttu-id="72f18-119">指定.NET 类型的完全限定的名称，例如`System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="72f18-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="72f18-120">备注</span><span class="sxs-lookup"><span data-stu-id="72f18-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="72f18-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="72f18-121">See Also</span></span>

[<span data-ttu-id="72f18-122">为配置 （格式） 的 CustomEntry EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="72f18-122">SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="72f18-123">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="72f18-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
