---
title: 使用 ListControl （格式） 的列表项的标签元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065421"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="0fbc7-102">Label Element for ListItem for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0fbc7-102">Label Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="0fbc7-103">指定属性或脚本值的行中的左侧显示的标签。</span><span class="sxs-lookup"><span data-stu-id="0fbc7-103">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>

<span data-ttu-id="0fbc7-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 ListControl （格式） 的 ListControl 元素 （ListEntry 的 ListControl （格式） ListItems ListEntry 元素ListItems ListControl （格式） 标签 ListControl （格式） 的 ListItem 元素的格式） ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="0fbc7-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems for ListEntry for ListControl Element (Format) ListItem Element for ListItems for ListControl (Format) Label Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0fbc7-105">语法</span><span class="sxs-lookup"><span data-stu-id="0fbc7-105">Syntax</span></span>

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0fbc7-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="0fbc7-106">Attributes and Elements</span></span>

<span data-ttu-id="0fbc7-107">以下各节描述了特性、 子元素和父元素的`Label`元素。</span><span class="sxs-lookup"><span data-stu-id="0fbc7-107">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0fbc7-108">属性</span><span class="sxs-lookup"><span data-stu-id="0fbc7-108">Attributes</span></span>

<span data-ttu-id="0fbc7-109">无。</span><span class="sxs-lookup"><span data-stu-id="0fbc7-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0fbc7-110">子元素</span><span class="sxs-lookup"><span data-stu-id="0fbc7-110">Child Elements</span></span>

<span data-ttu-id="0fbc7-111">无。</span><span class="sxs-lookup"><span data-stu-id="0fbc7-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0fbc7-112">父元素</span><span class="sxs-lookup"><span data-stu-id="0fbc7-112">Parent Elements</span></span>

|<span data-ttu-id="0fbc7-113">元素</span><span class="sxs-lookup"><span data-stu-id="0fbc7-113">Element</span></span>|<span data-ttu-id="0fbc7-114">说明</span><span class="sxs-lookup"><span data-stu-id="0fbc7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0fbc7-115">ListItems 的 ListControl （格式） 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="0fbc7-115">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="0fbc7-116">定义属性或其值显示在列表视图的行中的脚本。</span><span class="sxs-lookup"><span data-stu-id="0fbc7-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0fbc7-117">文本值</span><span class="sxs-lookup"><span data-stu-id="0fbc7-117">Text Value</span></span>

<span data-ttu-id="0fbc7-118">指定要向属性或脚本值的左侧显示的标签。</span><span class="sxs-lookup"><span data-stu-id="0fbc7-118">Specify the label to be display to the left of the property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="0fbc7-119">备注</span><span class="sxs-lookup"><span data-stu-id="0fbc7-119">Remarks</span></span>

<span data-ttu-id="0fbc7-120">如果未指定一个标签，显示属性或脚本的名称。</span><span class="sxs-lookup"><span data-stu-id="0fbc7-120">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="0fbc7-121">有关使用列表视图中的标签的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="0fbc7-121">For more information about using labels in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0fbc7-122">示例</span><span class="sxs-lookup"><span data-stu-id="0fbc7-122">Example</span></span>

<span data-ttu-id="0fbc7-123">下面的示例演示如何将标签添加到行。</span><span class="sxs-lookup"><span data-stu-id="0fbc7-123">The following example shows how to add a label to a row.</span></span>

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="0fbc7-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0fbc7-124">See Also</span></span>

[<span data-ttu-id="0fbc7-125">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="0fbc7-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="0fbc7-126">ListItem 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="0fbc7-126">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="0fbc7-127">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="0fbc7-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
