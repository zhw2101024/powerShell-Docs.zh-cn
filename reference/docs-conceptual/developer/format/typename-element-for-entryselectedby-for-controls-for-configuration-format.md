---
title: 用于配置（格式）的控件的 EntrySelectedBy 的 TypeName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30bb1382-8c6b-4371-82e6-baf427fa0781
caps.latest.revision: 6
ms.openlocfilehash: cec8c5d76bded321ec1d6a1cd0409d7c88863c03
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368076"
---
# <a name="typename-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="a6b5f-102">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="a6b5f-102">TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="a6b5f-103">指定使用控件的此定义的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="a6b5f-103">Specifies a .NET type that uses this definition of the control.</span></span> <span data-ttu-id="a6b5f-104">此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。</span><span class="sxs-lookup"><span data-stu-id="a6b5f-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="a6b5f-105">Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format） CustomEntry 的 CustomControl 的元素，用于配置（format）的控件的 EntrySelectedBy 元素 for CustomEntry 的元素，用于配置的控件的的元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6b5f-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) TypeName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a6b5f-106">语法</span><span class="sxs-lookup"><span data-stu-id="a6b5f-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="a6b5f-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="a6b5f-107">Attributes and Elements</span></span>

<span data-ttu-id="a6b5f-108">以下各节介绍了 `TypeName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a6b5f-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a6b5f-109">属性</span><span class="sxs-lookup"><span data-stu-id="a6b5f-109">Attributes</span></span>

<span data-ttu-id="a6b5f-110">无。</span><span class="sxs-lookup"><span data-stu-id="a6b5f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a6b5f-111">子元素</span><span class="sxs-lookup"><span data-stu-id="a6b5f-111">Child Elements</span></span>

<span data-ttu-id="a6b5f-112">无。</span><span class="sxs-lookup"><span data-stu-id="a6b5f-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a6b5f-113">父元素</span><span class="sxs-lookup"><span data-stu-id="a6b5f-113">Parent Elements</span></span>

|<span data-ttu-id="a6b5f-114">元素</span><span class="sxs-lookup"><span data-stu-id="a6b5f-114">Element</span></span>|<span data-ttu-id="a6b5f-115">描述</span><span class="sxs-lookup"><span data-stu-id="a6b5f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a6b5f-116">用于配置的控件的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6b5f-116">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="a6b5f-117">定义使用此控件定义的 .NET 类型或要使用此定义时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="a6b5f-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a6b5f-118">文本值</span><span class="sxs-lookup"><span data-stu-id="a6b5f-118">Text Value</span></span>

<span data-ttu-id="a6b5f-119">指定 .NET 类型的完全限定名，如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="a6b5f-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="a6b5f-120">备注</span><span class="sxs-lookup"><span data-stu-id="a6b5f-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="a6b5f-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a6b5f-121">See Also</span></span>

[<span data-ttu-id="a6b5f-122">用于配置的控件的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6b5f-122">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="a6b5f-123">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="a6b5f-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
