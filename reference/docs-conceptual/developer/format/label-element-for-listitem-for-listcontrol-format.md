---
title: ListControl 的标记元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362886"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="6ba61-102">Label Element for ListItem for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6ba61-102">Label Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="6ba61-103">指定在行的属性或脚本值左侧显示的标签。</span><span class="sxs-lookup"><span data-stu-id="6ba61-103">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>

<span data-ttu-id="6ba61-104">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（format） ListEntries 元素 for ListControl （format） ListEntry 元素 for ListControl for ListItems 元素（Format） ListControl 的 ListItems for ListControl （Format） Label 元素的元素</span><span class="sxs-lookup"><span data-stu-id="6ba61-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems for ListEntry for ListControl Element (Format) ListItem Element for ListItems for ListControl (Format) Label Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6ba61-105">语法</span><span class="sxs-lookup"><span data-stu-id="6ba61-105">Syntax</span></span>

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6ba61-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="6ba61-106">Attributes and Elements</span></span>

<span data-ttu-id="6ba61-107">以下各节介绍了 `Label` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6ba61-107">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6ba61-108">属性</span><span class="sxs-lookup"><span data-stu-id="6ba61-108">Attributes</span></span>

<span data-ttu-id="6ba61-109">无。</span><span class="sxs-lookup"><span data-stu-id="6ba61-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6ba61-110">子元素</span><span class="sxs-lookup"><span data-stu-id="6ba61-110">Child Elements</span></span>

<span data-ttu-id="6ba61-111">无。</span><span class="sxs-lookup"><span data-stu-id="6ba61-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6ba61-112">父元素</span><span class="sxs-lookup"><span data-stu-id="6ba61-112">Parent Elements</span></span>

|<span data-ttu-id="6ba61-113">元素</span><span class="sxs-lookup"><span data-stu-id="6ba61-113">Element</span></span>|<span data-ttu-id="6ba61-114">描述</span><span class="sxs-lookup"><span data-stu-id="6ba61-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6ba61-115">ListControl 的 ListItems 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6ba61-115">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="6ba61-116">定义其值显示在列表视图的行中的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="6ba61-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="6ba61-117">文本值</span><span class="sxs-lookup"><span data-stu-id="6ba61-117">Text Value</span></span>

<span data-ttu-id="6ba61-118">指定要在属性或脚本值左侧显示的标签。</span><span class="sxs-lookup"><span data-stu-id="6ba61-118">Specify the label to be display to the left of the property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="6ba61-119">备注</span><span class="sxs-lookup"><span data-stu-id="6ba61-119">Remarks</span></span>

<span data-ttu-id="6ba61-120">如果未指定标签，则显示属性或脚本的名称。</span><span class="sxs-lookup"><span data-stu-id="6ba61-120">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="6ba61-121">有关在列表视图中使用标签的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="6ba61-121">For more information about using labels in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6ba61-122">示例</span><span class="sxs-lookup"><span data-stu-id="6ba61-122">Example</span></span>

<span data-ttu-id="6ba61-123">下面的示例演示如何向行中添加标签。</span><span class="sxs-lookup"><span data-stu-id="6ba61-123">The following example shows how to add a label to a row.</span></span>

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="6ba61-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6ba61-124">See Also</span></span>

[<span data-ttu-id="6ba61-125">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="6ba61-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="6ba61-126">元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6ba61-126">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="6ba61-127">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="6ba61-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
