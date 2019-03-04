---
title: ListControl （格式） 的 ListEntry 的 Listitem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858583"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="c104f-102">ListItems Element for ListEntry for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c104f-102">ListItems Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="c104f-103">定义属性和其值显示在列表视图的行中的脚本。</span><span class="sxs-lookup"><span data-stu-id="c104f-103">Defines the properties and scripts whose values are displayed in the rows of the list view.</span></span>

<span data-ttu-id="c104f-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素的元素列表控件 （格式） ListEntry ListControl （格式） 的 ListControl （格式） Listitem 元素</span><span class="sxs-lookup"><span data-stu-id="c104f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for List Control (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c104f-105">语法</span><span class="sxs-lookup"><span data-stu-id="c104f-105">Syntax</span></span>

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c104f-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="c104f-106">Attributes and Elements</span></span>

<span data-ttu-id="c104f-107">以下各节描述的特性、 子元素和父元素的`ListItems`元素。</span><span class="sxs-lookup"><span data-stu-id="c104f-107">The following sections describe the attributes, child elements, and parent element of the `ListItems` element.</span></span> <span data-ttu-id="c104f-108">可以指定的子元素的数目没有限制。</span><span class="sxs-lookup"><span data-stu-id="c104f-108">There is no limit to the number of child elements that can be specified.</span></span> <span data-ttu-id="c104f-109">子元素的顺序定义值显示在列表视图中的顺序。</span><span class="sxs-lookup"><span data-stu-id="c104f-109">The order of the child elements defines the order that values are displayed in the list view.</span></span>

### <a name="attributes"></a><span data-ttu-id="c104f-110">属性</span><span class="sxs-lookup"><span data-stu-id="c104f-110">Attributes</span></span>

<span data-ttu-id="c104f-111">无。</span><span class="sxs-lookup"><span data-stu-id="c104f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c104f-112">子元素</span><span class="sxs-lookup"><span data-stu-id="c104f-112">Child Elements</span></span>

|<span data-ttu-id="c104f-113">元素</span><span class="sxs-lookup"><span data-stu-id="c104f-113">Element</span></span>|<span data-ttu-id="c104f-114">说明</span><span class="sxs-lookup"><span data-stu-id="c104f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c104f-115">ListControl （格式） 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="c104f-115">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="c104f-116">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="c104f-116">Required element.</span></span><br /><br /> <span data-ttu-id="c104f-117">定义属性或其值显示的列表视图的脚本。</span><span class="sxs-lookup"><span data-stu-id="c104f-117">Defines the property or script whose value is displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c104f-118">父元素</span><span class="sxs-lookup"><span data-stu-id="c104f-118">Parent Elements</span></span>

|<span data-ttu-id="c104f-119">元素</span><span class="sxs-lookup"><span data-stu-id="c104f-119">Element</span></span>|<span data-ttu-id="c104f-120">说明</span><span class="sxs-lookup"><span data-stu-id="c104f-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c104f-121">ListControl （格式） 的 ListEntry 元素</span><span class="sxs-lookup"><span data-stu-id="c104f-121">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="c104f-122">提供列表视图中的定义。</span><span class="sxs-lookup"><span data-stu-id="c104f-122">Provides a definition of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c104f-123">备注</span><span class="sxs-lookup"><span data-stu-id="c104f-123">Remarks</span></span>

<span data-ttu-id="c104f-124">有关此类型的视图的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="c104f-124">For more information about this type of view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c104f-125">示例</span><span class="sxs-lookup"><span data-stu-id="c104f-125">Example</span></span>

<span data-ttu-id="c104f-126">此示例演示定义列表视图的三个行的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="c104f-126">This example shows the XML elements that define three rows of the list view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c104f-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c104f-127">See Also</span></span>

[<span data-ttu-id="c104f-128">ListControl （格式） 的 ListEntry 元素</span><span class="sxs-lookup"><span data-stu-id="c104f-128">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="c104f-129">ListControl （格式） 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="c104f-129">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="c104f-130">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="c104f-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c104f-131">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="c104f-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
