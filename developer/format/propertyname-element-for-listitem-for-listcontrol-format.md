---
title: PropertyName ListControl （格式） 的 ListItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064886"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="0a127-102">PropertyName Element for ListItem for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0a127-102">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="0a127-103">指定其值显示在列表中的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="0a127-103">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="0a127-104">元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 （格式） ListEntry 元素 （格式） Listitem 元素 （格式） ListItem 元素 （格式） 属性名称的配置元素ListItem （格式）</span><span class="sxs-lookup"><span data-stu-id="0a127-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0a127-105">语法</span><span class="sxs-lookup"><span data-stu-id="0a127-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0a127-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="0a127-106">Attributes and Elements</span></span>

<span data-ttu-id="0a127-107">以下各节描述了特性、 子元素和父元素的`PropertyName`元素。</span><span class="sxs-lookup"><span data-stu-id="0a127-107">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0a127-108">属性</span><span class="sxs-lookup"><span data-stu-id="0a127-108">Attributes</span></span>

<span data-ttu-id="0a127-109">无。</span><span class="sxs-lookup"><span data-stu-id="0a127-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0a127-110">子元素</span><span class="sxs-lookup"><span data-stu-id="0a127-110">Child Elements</span></span>

<span data-ttu-id="0a127-111">无。</span><span class="sxs-lookup"><span data-stu-id="0a127-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0a127-112">父元素</span><span class="sxs-lookup"><span data-stu-id="0a127-112">Parent Elements</span></span>

|<span data-ttu-id="0a127-113">元素</span><span class="sxs-lookup"><span data-stu-id="0a127-113">Element</span></span>|<span data-ttu-id="0a127-114">说明</span><span class="sxs-lookup"><span data-stu-id="0a127-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0a127-115">ListItem 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="0a127-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="0a127-116">定义属性或其值显示在列表视图的行中的脚本。</span><span class="sxs-lookup"><span data-stu-id="0a127-116">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0a127-117">文本值</span><span class="sxs-lookup"><span data-stu-id="0a127-117">Text Value</span></span>

<span data-ttu-id="0a127-118">指定显示其值的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="0a127-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="0a127-119">备注</span><span class="sxs-lookup"><span data-stu-id="0a127-119">Remarks</span></span>

<span data-ttu-id="0a127-120">当指定此元素时，不能指定[ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="0a127-120">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="0a127-121">除了显示的属性值，还可以指定的值或可用于更改值的显示格式字符串的标签。</span><span class="sxs-lookup"><span data-stu-id="0a127-121">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="0a127-122">在列表视图中指定数据的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="0a127-122">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0a127-123">示例</span><span class="sxs-lookup"><span data-stu-id="0a127-123">Example</span></span>

<span data-ttu-id="0a127-124">下面的示例演示如何以指定的标签和其值显示的属性。</span><span class="sxs-lookup"><span data-stu-id="0a127-124">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="0a127-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0a127-125">See Also</span></span>

[<span data-ttu-id="0a127-126">ListControl （格式） 的列表项的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="0a127-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="0a127-127">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="0a127-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="0a127-128">ListControl(Format) 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="0a127-128">ListItem Element for ListControl(Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="0a127-129">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="0a127-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
