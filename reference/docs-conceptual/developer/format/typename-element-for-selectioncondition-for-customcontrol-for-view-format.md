---
title: CustomControl 的 SelectionCondition 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c65171-4d4c-46a9-a545-591df058acd1
caps.latest.revision: 7
ms.openlocfilehash: 00e9ae0916dd6d22602b99b201c9c4b7e549dc48
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361586"
---
# <a name="typename-element-for-selectioncondition-for-customcontrol-for-view--format"></a><span data-ttu-id="ae1a3-102">TypeName Element for SelectionCondition for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="ae1a3-102">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>

<span data-ttu-id="ae1a3-103">指定触发条件的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="ae1a3-103">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="ae1a3-104">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="ae1a3-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="ae1a3-105">Configuration Element （Format） ViewDefinitions 元素（格式） View 元素（format） CustomControl 元素 for View （format） CustomEntries 元素 for CustomControl for CustomEntry for CustomEntries for View （Format） CustomControl 元素 for view （Format） CustomItem 元素 for CustomEntry for CustomControl for EntrySelectedBy for CustomControl for SelectionCondition for CustomControl for for for view （Format）</span><span class="sxs-lookup"><span data-stu-id="ae1a3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format) TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ae1a3-106">语法</span><span class="sxs-lookup"><span data-stu-id="ae1a3-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="ae1a3-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="ae1a3-107">Attributes and Elements</span></span>

<span data-ttu-id="ae1a3-108">以下各节介绍了 `TypeName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ae1a3-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ae1a3-109">属性</span><span class="sxs-lookup"><span data-stu-id="ae1a3-109">Attributes</span></span>

<span data-ttu-id="ae1a3-110">无。</span><span class="sxs-lookup"><span data-stu-id="ae1a3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ae1a3-111">子元素</span><span class="sxs-lookup"><span data-stu-id="ae1a3-111">Child Elements</span></span>

<span data-ttu-id="ae1a3-112">无。</span><span class="sxs-lookup"><span data-stu-id="ae1a3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ae1a3-113">父元素</span><span class="sxs-lookup"><span data-stu-id="ae1a3-113">Parent Elements</span></span>

|<span data-ttu-id="ae1a3-114">元素</span><span class="sxs-lookup"><span data-stu-id="ae1a3-114">Element</span></span>|<span data-ttu-id="ae1a3-115">描述</span><span class="sxs-lookup"><span data-stu-id="ae1a3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ae1a3-116">用于 View 的 CustomControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ae1a3-116">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)|<span data-ttu-id="ae1a3-117">定义要使用的控件定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="ae1a3-117">Defines a condition that must exist for the control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ae1a3-118">文本值</span><span class="sxs-lookup"><span data-stu-id="ae1a3-118">Text Value</span></span>

<span data-ttu-id="ae1a3-119">指定 .NET 类型的完全限定名，如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="ae1a3-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="ae1a3-120">备注</span><span class="sxs-lookup"><span data-stu-id="ae1a3-120">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="ae1a3-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ae1a3-121">See Also</span></span>

[<span data-ttu-id="ae1a3-122">用于 View 的 CustomControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ae1a3-122">SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

[<span data-ttu-id="ae1a3-123">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="ae1a3-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
