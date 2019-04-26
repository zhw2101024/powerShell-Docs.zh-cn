---
title: ListItems 的 ListControl （格式） 的 ListItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065761"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="668db-102">ListItem Element for ListItems for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="668db-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="668db-103">定义属性或其值显示在列表视图的行中的脚本。</span><span class="sxs-lookup"><span data-stu-id="668db-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="668db-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素的元素 ListControl （格式） ListEntry ListControl （格式） 的 ListControl （格式） Listitem 元素ListItem ListControl 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="668db-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="668db-105">语法</span><span class="sxs-lookup"><span data-stu-id="668db-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="668db-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="668db-106">Attributes and Elements</span></span>

<span data-ttu-id="668db-107">以下各节描述的特性、 子元素和父元素的`ListItem`元素。</span><span class="sxs-lookup"><span data-stu-id="668db-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="668db-108">可以指定只有一个属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="668db-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="668db-109">属性</span><span class="sxs-lookup"><span data-stu-id="668db-109">Attributes</span></span>

<span data-ttu-id="668db-110">无</span><span class="sxs-lookup"><span data-stu-id="668db-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="668db-111">子元素</span><span class="sxs-lookup"><span data-stu-id="668db-111">Child Elements</span></span>

|<span data-ttu-id="668db-112">元素</span><span class="sxs-lookup"><span data-stu-id="668db-112">Element</span></span>|<span data-ttu-id="668db-113">说明</span><span class="sxs-lookup"><span data-stu-id="668db-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="668db-114">ListControl （格式） 的列表项的 FormatString 元素</span><span class="sxs-lookup"><span data-stu-id="668db-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="668db-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="668db-115">Optional element.</span></span><br /><br /> <span data-ttu-id="668db-116">指定定义如何显示的属性或脚本的值的格式字符串。</span><span class="sxs-lookup"><span data-stu-id="668db-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="668db-117">ItemSelectionCondition ListControl （格式） 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="668db-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="668db-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="668db-118">Optional element.</span></span><br /><br /> <span data-ttu-id="668db-119">定义必须存在要使用此列表项的条件。</span><span class="sxs-lookup"><span data-stu-id="668db-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="668db-120">ListControl （格式） 的列表项的标签元素</span><span class="sxs-lookup"><span data-stu-id="668db-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="668db-121">可选元素</span><span class="sxs-lookup"><span data-stu-id="668db-121">Optional element</span></span><br /><br /> <span data-ttu-id="668db-122">指定属性或脚本值的行中的左侧显示的标签。</span><span class="sxs-lookup"><span data-stu-id="668db-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="668db-123">PropertyName ListControl （格式） 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="668db-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="668db-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="668db-124">Optional element.</span></span><br /><br /> <span data-ttu-id="668db-125">指定其值显示的行中的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="668db-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="668db-126">ListControl （格式） 的列表项的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="668db-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="668db-127">可选元素。</span><span class="sxs-lookup"><span data-stu-id="668db-127">Optional element.</span></span><br /><br /> <span data-ttu-id="668db-128">指定其值显示的行中的脚本。</span><span class="sxs-lookup"><span data-stu-id="668db-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="668db-129">父元素</span><span class="sxs-lookup"><span data-stu-id="668db-129">Parent Elements</span></span>

|<span data-ttu-id="668db-130">元素</span><span class="sxs-lookup"><span data-stu-id="668db-130">Element</span></span>|<span data-ttu-id="668db-131">说明</span><span class="sxs-lookup"><span data-stu-id="668db-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="668db-132">列表控件 （格式） 的 Listitem 元素</span><span class="sxs-lookup"><span data-stu-id="668db-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="668db-133">定义属性和其值显示在列表视图中的脚本。</span><span class="sxs-lookup"><span data-stu-id="668db-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="668db-134">备注</span><span class="sxs-lookup"><span data-stu-id="668db-134">Remarks</span></span>

<span data-ttu-id="668db-135">列表视图的组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="668db-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="668db-136">示例</span><span class="sxs-lookup"><span data-stu-id="668db-136">Example</span></span>

<span data-ttu-id="668db-137">此示例演示定义列表视图的三个行的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="668db-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="668db-138">前两行显示.NET 属性的值，最后一行显示由脚本生成的值。</span><span class="sxs-lookup"><span data-stu-id="668db-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a><span data-ttu-id="668db-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="668db-139">See Also</span></span>

[<span data-ttu-id="668db-140">Listitem 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="668db-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="668db-141">ListItem （格式） 的 FormatString 元素</span><span class="sxs-lookup"><span data-stu-id="668db-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="668db-142">ListItem （格式） 的标签元素</span><span class="sxs-lookup"><span data-stu-id="668db-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="668db-143">ListItem （格式） 的属性名称元素</span><span class="sxs-lookup"><span data-stu-id="668db-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="668db-144">ListItem （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="668db-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="668db-145">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="668db-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="668db-146">编写 Windows PowerShell 格式设置和文件类型</span><span class="sxs-lookup"><span data-stu-id="668db-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
