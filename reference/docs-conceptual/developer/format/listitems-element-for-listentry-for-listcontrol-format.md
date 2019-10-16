---
title: ListControl （Format）的 ListEntry 的 ListItems 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362736"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="f74a2-102">ListItems Element for ListEntry for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f74a2-102">ListItems Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="f74a2-103">定义其值显示在列表视图的行中的属性和脚本。</span><span class="sxs-lookup"><span data-stu-id="f74a2-103">Defines the properties and scripts whose values are displayed in the rows of the list view.</span></span>

<span data-ttu-id="f74a2-104">用于 ListControl 的 ListItems （format） ListEntry 元素的配置元素（格式） ViewDefinitions 元素（格式） ListControl 元素（格式） ListEntries 元素（格式）元素</span><span class="sxs-lookup"><span data-stu-id="f74a2-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for List Control (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f74a2-105">语法</span><span class="sxs-lookup"><span data-stu-id="f74a2-105">Syntax</span></span>

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f74a2-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="f74a2-106">Attributes and Elements</span></span>

<span data-ttu-id="f74a2-107">以下各节介绍 `ListItems` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f74a2-107">The following sections describe the attributes, child elements, and parent element of the `ListItems` element.</span></span> <span data-ttu-id="f74a2-108">对于可以指定的子元素数没有限制。</span><span class="sxs-lookup"><span data-stu-id="f74a2-108">There is no limit to the number of child elements that can be specified.</span></span> <span data-ttu-id="f74a2-109">子元素的顺序定义值在列表视图中的显示顺序。</span><span class="sxs-lookup"><span data-stu-id="f74a2-109">The order of the child elements defines the order that values are displayed in the list view.</span></span>

### <a name="attributes"></a><span data-ttu-id="f74a2-110">属性</span><span class="sxs-lookup"><span data-stu-id="f74a2-110">Attributes</span></span>

<span data-ttu-id="f74a2-111">无。</span><span class="sxs-lookup"><span data-stu-id="f74a2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f74a2-112">子元素</span><span class="sxs-lookup"><span data-stu-id="f74a2-112">Child Elements</span></span>

|<span data-ttu-id="f74a2-113">元素</span><span class="sxs-lookup"><span data-stu-id="f74a2-113">Element</span></span>|<span data-ttu-id="f74a2-114">描述</span><span class="sxs-lookup"><span data-stu-id="f74a2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f74a2-115">ListControl 的元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f74a2-115">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="f74a2-116">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="f74a2-116">Required element.</span></span><br /><br /> <span data-ttu-id="f74a2-117">定义其值由列表视图显示的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="f74a2-117">Defines the property or script whose value is displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f74a2-118">父元素</span><span class="sxs-lookup"><span data-stu-id="f74a2-118">Parent Elements</span></span>

|<span data-ttu-id="f74a2-119">元素</span><span class="sxs-lookup"><span data-stu-id="f74a2-119">Element</span></span>|<span data-ttu-id="f74a2-120">描述</span><span class="sxs-lookup"><span data-stu-id="f74a2-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f74a2-121">ListControl 的 ListEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f74a2-121">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="f74a2-122">提供列表视图的定义。</span><span class="sxs-lookup"><span data-stu-id="f74a2-122">Provides a definition of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f74a2-123">备注</span><span class="sxs-lookup"><span data-stu-id="f74a2-123">Remarks</span></span>

<span data-ttu-id="f74a2-124">有关此类视图的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="f74a2-124">For more information about this type of view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f74a2-125">示例</span><span class="sxs-lookup"><span data-stu-id="f74a2-125">Example</span></span>

<span data-ttu-id="f74a2-126">此示例显示了用于定义列表视图的三行的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="f74a2-126">This example shows the XML elements that define three rows of the list view.</span></span>

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="f74a2-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f74a2-127">See Also</span></span>

[<span data-ttu-id="f74a2-128">ListControl 的 ListEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f74a2-128">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="f74a2-129">ListControl 的元素（格式）</span><span class="sxs-lookup"><span data-stu-id="f74a2-129">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="f74a2-130">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="f74a2-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f74a2-131">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="f74a2-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
