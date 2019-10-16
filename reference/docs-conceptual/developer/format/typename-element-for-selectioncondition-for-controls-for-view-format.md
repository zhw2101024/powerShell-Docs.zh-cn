---
title: 用于视图（格式）的控件的 SelectionCondition 的 TypeName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7141aefc-6656-4c52-8a9c-c2bfc9c87be9
caps.latest.revision: 6
ms.openlocfilehash: 7a697c286ec9efe750930739cdfa2580003365dd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361596"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-view-format"></a><span data-ttu-id="95e72-102">TypeName Element for SelectionCondition for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="95e72-102">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>

<span data-ttu-id="95e72-103">指定触发条件的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="95e72-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="95e72-104">定义可由视图使用的控件时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="95e72-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="95e72-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） Controls 元素（format） Control 元素 for View （format） CustomControl 元素的控件元素，用于控件的 View （format） CustomEntries 元素CustomControl for view （format） CustomEntry 元素 for view （format）元素 for CustomEntries for view （format） EntrySelectedBy 元素 for view （format）元素 for CustomEntry for view （format） SelectionCondition 元素 for view （Format） View 的 SelectionCondition 的 TypeName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="95e72-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format) TypeName Element for SelectionCondition for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="95e72-106">语法</span><span class="sxs-lookup"><span data-stu-id="95e72-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="95e72-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="95e72-107">Attributes and Elements</span></span>

<span data-ttu-id="95e72-108">以下各节介绍了 `TypeName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="95e72-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="95e72-109">属性</span><span class="sxs-lookup"><span data-stu-id="95e72-109">Attributes</span></span>

<span data-ttu-id="95e72-110">无。</span><span class="sxs-lookup"><span data-stu-id="95e72-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="95e72-111">子元素</span><span class="sxs-lookup"><span data-stu-id="95e72-111">Child Elements</span></span>

<span data-ttu-id="95e72-112">无。</span><span class="sxs-lookup"><span data-stu-id="95e72-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="95e72-113">父元素</span><span class="sxs-lookup"><span data-stu-id="95e72-113">Parent Elements</span></span>

|<span data-ttu-id="95e72-114">元素</span><span class="sxs-lookup"><span data-stu-id="95e72-114">Element</span></span>|<span data-ttu-id="95e72-115">描述</span><span class="sxs-lookup"><span data-stu-id="95e72-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="95e72-116">用于视图的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="95e72-116">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)|<span data-ttu-id="95e72-117">定义要使用的控件定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="95e72-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="95e72-118">文本值</span><span class="sxs-lookup"><span data-stu-id="95e72-118">Text Value</span></span>

<span data-ttu-id="95e72-119">指定 .NET 类型的完全限定名，如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="95e72-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="95e72-120">备注</span><span class="sxs-lookup"><span data-stu-id="95e72-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="95e72-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="95e72-121">See Also</span></span>

[<span data-ttu-id="95e72-122">用于视图的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="95e72-122">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

[<span data-ttu-id="95e72-123">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="95e72-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
