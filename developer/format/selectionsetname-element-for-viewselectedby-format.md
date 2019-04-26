---
title: ViewSelectedBy （格式） 的 SelectionSetName 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ab0f033-df09-4435-a8bd-76ec2d01f13b
caps.latest.revision: 13
ms.openlocfilehash: d1de2b30860bac80bf17508f40eec33c2794c4b2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076219"
---
# <a name="selectionsetname-element-for-viewselectedby-format"></a><span data-ttu-id="86293-102">SelectionSetName Element for ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="86293-102">SelectionSetName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="86293-103">指定一组.NET 对象所显示的视图。</span><span class="sxs-lookup"><span data-stu-id="86293-103">Specifies a set of .NET objects that are displayed by the view.</span></span>

<span data-ttu-id="86293-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ViewSelectedBy 元素 （格式） SelectionSetName 元素 ViewSelectedBy （格式）</span><span class="sxs-lookup"><span data-stu-id="86293-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) SelectionSetName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="86293-105">语法</span><span class="sxs-lookup"><span data-stu-id="86293-105">Syntax</span></span>

```xml
<SelectionSetName>Name of selection set<SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="86293-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="86293-106">Attributes and Elements</span></span>

<span data-ttu-id="86293-107">以下各节描述了特性、 子元素和父元素的`SelectionSetName`元素。</span><span class="sxs-lookup"><span data-stu-id="86293-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="86293-108">属性</span><span class="sxs-lookup"><span data-stu-id="86293-108">Attributes</span></span>

<span data-ttu-id="86293-109">无。</span><span class="sxs-lookup"><span data-stu-id="86293-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="86293-110">子元素</span><span class="sxs-lookup"><span data-stu-id="86293-110">Child Elements</span></span>

<span data-ttu-id="86293-111">无。</span><span class="sxs-lookup"><span data-stu-id="86293-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="86293-112">父元素</span><span class="sxs-lookup"><span data-stu-id="86293-112">Parent Elements</span></span>

|<span data-ttu-id="86293-113">元素</span><span class="sxs-lookup"><span data-stu-id="86293-113">Element</span></span>|<span data-ttu-id="86293-114">说明</span><span class="sxs-lookup"><span data-stu-id="86293-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86293-115">ViewSelectedBy 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="86293-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="86293-116">定义视图所显示的.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="86293-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="86293-117">文本值</span><span class="sxs-lookup"><span data-stu-id="86293-117">Text Value</span></span>

<span data-ttu-id="86293-118">指定由定义的选项集的名称`Name`选项集的元素。</span><span class="sxs-lookup"><span data-stu-id="86293-118">Specify the name of the selection set that is defined by the `Name` element for the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="86293-119">备注</span><span class="sxs-lookup"><span data-stu-id="86293-119">Remarks</span></span>

<span data-ttu-id="86293-120">当有一组你想要使用单一名称，例如一组通过继承相关的对象引用的相关对象时，你可以使用所选内容集。</span><span class="sxs-lookup"><span data-stu-id="86293-120">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="86293-121">有关定义和引用所选内容集的详细信息，请参阅[定义设置的对象](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="86293-121">For more information about defining and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="86293-122">示例</span><span class="sxs-lookup"><span data-stu-id="86293-122">Example</span></span>

<span data-ttu-id="86293-123">下面的示例演示如何指定设置列表视图的选择。</span><span class="sxs-lookup"><span data-stu-id="86293-123">The following example shows how to specify a selection set for a list view.</span></span> <span data-ttu-id="86293-124">相同的架构用于表中，宽，和自定义视图。</span><span class="sxs-lookup"><span data-stu-id="86293-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>Name of View</Name>
  <ViewSelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="86293-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="86293-125">See Also</span></span>

[<span data-ttu-id="86293-126">定义的选项集</span><span class="sxs-lookup"><span data-stu-id="86293-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="86293-127">ViewSelectedBy 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="86293-127">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="86293-128">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="86293-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
