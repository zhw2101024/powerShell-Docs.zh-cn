---
title: TypeName 元素的视图 （格式） 的 CustomEntry EntrySelectedBy |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76548af7-05bd-4d12-bf71-6fb69c434ef2
caps.latest.revision: 10
ms.openlocfilehash: c3dd761cd9b6c468d4833ea35b897ba5d425f598
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858833"
---
# <a name="typename-element-for-entryselectedby-for-customentry-for-view-format"></a><span data-ttu-id="33bde-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span><span class="sxs-lookup"><span data-stu-id="33bde-102">TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

<span data-ttu-id="33bde-103">指定将使用此定义的自定义控件视图的.NET 类型。</span><span class="sxs-lookup"><span data-stu-id="33bde-103">Specifies a .NET type that uses this definition of the custom control view.</span></span> <span data-ttu-id="33bde-104">可以为定义指定的类型的数量没有限制。</span><span class="sxs-lookup"><span data-stu-id="33bde-104">There is no limit to the number of types that can be specified for a definition.</span></span>

<span data-ttu-id="33bde-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl 视图 （格式） 的视图 （格式） EntrySelectedBy CustomEntries CustomEntry 元素CustomEntry 视图 （格式） 的视图 （格式） 的 CustomEntry EntrySelectedBy TypeName 元素的元素</span><span class="sxs-lookup"><span data-stu-id="33bde-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) TypeName Element for EntrySelectedBy for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="33bde-106">语法</span><span class="sxs-lookup"><span data-stu-id="33bde-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="33bde-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="33bde-107">Attributes and Elements</span></span>

<span data-ttu-id="33bde-108">以下各节描述了特性、 子元素和父元素的`TypeName`元素。</span><span class="sxs-lookup"><span data-stu-id="33bde-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="33bde-109">特性</span><span class="sxs-lookup"><span data-stu-id="33bde-109">Attributes</span></span>

<span data-ttu-id="33bde-110">无。</span><span class="sxs-lookup"><span data-stu-id="33bde-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="33bde-111">子元素</span><span class="sxs-lookup"><span data-stu-id="33bde-111">Child Elements</span></span>

<span data-ttu-id="33bde-112">无。</span><span class="sxs-lookup"><span data-stu-id="33bde-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="33bde-113">父元素</span><span class="sxs-lookup"><span data-stu-id="33bde-113">Parent Elements</span></span>

|<span data-ttu-id="33bde-114">元素</span><span class="sxs-lookup"><span data-stu-id="33bde-114">Element</span></span>|<span data-ttu-id="33bde-115">描述</span><span class="sxs-lookup"><span data-stu-id="33bde-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="33bde-116">视图 （格式） 的 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="33bde-116">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="33bde-117">定义使用此自定义控件的视图定义的.NET 类型或要使用此定义中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="33bde-117">Defines the .NET types that use this custom control view definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="33bde-118">文本值</span><span class="sxs-lookup"><span data-stu-id="33bde-118">Text Value</span></span>

<span data-ttu-id="33bde-119">指定.NET 类型的完全限定的名称，例如`System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="33bde-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="33bde-120">备注</span><span class="sxs-lookup"><span data-stu-id="33bde-120">Remarks</span></span>

<span data-ttu-id="33bde-121">每个自定义控件的视图定义必须至少一个类型名称、 选择集或定义的选择条件。</span><span class="sxs-lookup"><span data-stu-id="33bde-121">Each custom control view definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="33bde-122">有关组件的自定义控件视图的详细信息，请参阅[创建自定义控件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="33bde-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="33bde-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="33bde-123">See Also</span></span>

[<span data-ttu-id="33bde-124">创建自定义控件</span><span class="sxs-lookup"><span data-stu-id="33bde-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="33bde-125">视图 （格式） 的 CustomEntry EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="33bde-125">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="33bde-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="33bde-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
