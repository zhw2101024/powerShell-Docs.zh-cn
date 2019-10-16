---
title: ViewSelectedBy 的 SelectionSetName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368256"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="4205c-102">SelectionSetName Element for ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="4205c-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="4205c-103">指定视图显示的一组 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="4205c-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="4205c-104">ViewSelectedBy 的 Configuration 元素（格式） ViewDefinitions 元素（格式） ViewSelectedBy 元素（format） SelectionSetName 元素（format）</span><span class="sxs-lookup"><span data-stu-id="4205c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4205c-105">语法</span><span class="sxs-lookup"><span data-stu-id="4205c-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4205c-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="4205c-106">Attributes and Elements</span></span>

<span data-ttu-id="4205c-107">以下各节介绍了 `SelectionSetName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4205c-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4205c-108">属性</span><span class="sxs-lookup"><span data-stu-id="4205c-108">Attributes</span></span>

<span data-ttu-id="4205c-109">无。</span><span class="sxs-lookup"><span data-stu-id="4205c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4205c-110">子元素</span><span class="sxs-lookup"><span data-stu-id="4205c-110">Child Elements</span></span>

<span data-ttu-id="4205c-111">无。</span><span class="sxs-lookup"><span data-stu-id="4205c-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4205c-112">父元素</span><span class="sxs-lookup"><span data-stu-id="4205c-112">Parent Elements</span></span>

|<span data-ttu-id="4205c-113">元素</span><span class="sxs-lookup"><span data-stu-id="4205c-113">Element</span></span>|<span data-ttu-id="4205c-114">描述</span><span class="sxs-lookup"><span data-stu-id="4205c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4205c-115">ViewSelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4205c-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="4205c-116">定义视图显示的 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="4205c-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4205c-117">文本值</span><span class="sxs-lookup"><span data-stu-id="4205c-117">Text Value</span></span>

<span data-ttu-id="4205c-118">为选择集指定由 `Name` 元素定义的选择集的名称。</span><span class="sxs-lookup"><span data-stu-id="4205c-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="4205c-119">备注</span><span class="sxs-lookup"><span data-stu-id="4205c-119">Remarks</span></span>

<span data-ttu-id="4205c-120">如果你有一组要通过使用单个名称引用的相关对象（例如通过继承相关的一组对象），则可以使用选择集。</span><span class="sxs-lookup"><span data-stu-id="4205c-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="4205c-121">有关定义和引用选项集的详细信息，请参阅[定义对象集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="4205c-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="4205c-122">示例</span><span class="sxs-lookup"><span data-stu-id="4205c-122">Example</span></span>

<span data-ttu-id="4205c-123">下面的示例演示如何为列表视图指定选择集。</span><span class="sxs-lookup"><span data-stu-id="4205c-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="4205c-124">表、宽视图和自定义视图使用相同的架构。</span><span class="sxs-lookup"><span data-stu-id="4205c-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="4205c-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4205c-125">See Also</span></span>

[<span data-ttu-id="4205c-126">定义选择集</span><span class="sxs-lookup"><span data-stu-id="4205c-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="4205c-127">ViewSelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4205c-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="4205c-128">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="4205c-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
