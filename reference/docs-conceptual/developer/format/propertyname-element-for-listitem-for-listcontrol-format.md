---
title: ListControl 的名称名称元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362376"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="5b9e6-102">PropertyName Element for ListItem for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="5b9e6-102">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="5b9e6-103">指定其值显示在列表中的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="5b9e6-103">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="5b9e6-104">配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） ListControl 元素（格式） ListEntries 元素（格式） ListEntry 元素（格式） ListItems 元素（格式）元素（格式） PropertyName 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5b9e6-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5b9e6-105">语法</span><span class="sxs-lookup"><span data-stu-id="5b9e6-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5b9e6-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="5b9e6-106">Attributes and Elements</span></span>

<span data-ttu-id="5b9e6-107">以下各节介绍了 `PropertyName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5b9e6-107">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5b9e6-108">属性</span><span class="sxs-lookup"><span data-stu-id="5b9e6-108">Attributes</span></span>

<span data-ttu-id="5b9e6-109">无。</span><span class="sxs-lookup"><span data-stu-id="5b9e6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5b9e6-110">子元素</span><span class="sxs-lookup"><span data-stu-id="5b9e6-110">Child Elements</span></span>

<span data-ttu-id="5b9e6-111">无。</span><span class="sxs-lookup"><span data-stu-id="5b9e6-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5b9e6-112">父元素</span><span class="sxs-lookup"><span data-stu-id="5b9e6-112">Parent Elements</span></span>

|<span data-ttu-id="5b9e6-113">元素</span><span class="sxs-lookup"><span data-stu-id="5b9e6-113">Element</span></span>|<span data-ttu-id="5b9e6-114">描述</span><span class="sxs-lookup"><span data-stu-id="5b9e6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5b9e6-115">元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5b9e6-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="5b9e6-116">定义其值显示在列表视图的行中的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="5b9e6-116">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5b9e6-117">文本值</span><span class="sxs-lookup"><span data-stu-id="5b9e6-117">Text Value</span></span>

<span data-ttu-id="5b9e6-118">指定显示其值的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="5b9e6-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="5b9e6-119">备注</span><span class="sxs-lookup"><span data-stu-id="5b9e6-119">Remarks</span></span>

<span data-ttu-id="5b9e6-120">如果指定此元素，则不能指定[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="5b9e6-120">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="5b9e6-121">除了显示属性值以外，还可以指定值的标签或可用于更改值显示的格式字符串。</span><span class="sxs-lookup"><span data-stu-id="5b9e6-121">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="5b9e6-122">有关在列表视图中指定数据的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="5b9e6-122">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="5b9e6-123">示例</span><span class="sxs-lookup"><span data-stu-id="5b9e6-123">Example</span></span>

<span data-ttu-id="5b9e6-124">下面的示例演示如何指定显示其值的标签和属性。</span><span class="sxs-lookup"><span data-stu-id="5b9e6-124">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="5b9e6-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b9e6-125">See Also</span></span>

[<span data-ttu-id="5b9e6-126">ListControl 的的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5b9e6-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="5b9e6-127">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="5b9e6-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="5b9e6-128">ListControl 的元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5b9e6-128">ListItem Element for ListControl(Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="5b9e6-129">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="5b9e6-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
