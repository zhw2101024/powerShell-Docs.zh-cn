---
title: ListControl 的 ListItems 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365126"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="0b9b4-102">ListItem Element for ListItems for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0b9b4-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="0b9b4-103">定义其值显示在列表视图的行中的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="0b9b4-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="0b9b4-104">ListEntry 的 ListControl （format） ListControl 元素的配置元素（格式） ViewDefinitions 元素（格式） ListControl 元素（format） ListEntries 元素（format）ListControl 元素的输入（格式）</span><span class="sxs-lookup"><span data-stu-id="0b9b4-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0b9b4-105">语法</span><span class="sxs-lookup"><span data-stu-id="0b9b4-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0b9b4-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="0b9b4-106">Attributes and Elements</span></span>

<span data-ttu-id="0b9b4-107">以下各节介绍 `ListItem` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0b9b4-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="0b9b4-108">只能指定一个属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="0b9b4-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="0b9b4-109">属性</span><span class="sxs-lookup"><span data-stu-id="0b9b4-109">Attributes</span></span>

<span data-ttu-id="0b9b4-110">无</span><span class="sxs-lookup"><span data-stu-id="0b9b4-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="0b9b4-111">子元素</span><span class="sxs-lookup"><span data-stu-id="0b9b4-111">Child Elements</span></span>

|<span data-ttu-id="0b9b4-112">元素</span><span class="sxs-lookup"><span data-stu-id="0b9b4-112">Element</span></span>|<span data-ttu-id="0b9b4-113">描述</span><span class="sxs-lookup"><span data-stu-id="0b9b4-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0b9b4-114">ListControl 的的格式字符串元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0b9b4-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="0b9b4-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="0b9b4-115">Optional element.</span></span><br /><br /> <span data-ttu-id="0b9b4-116">指定定义属性或脚本值显示方式的格式字符串。</span><span class="sxs-lookup"><span data-stu-id="0b9b4-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="0b9b4-117">ListControl 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0b9b4-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="0b9b4-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="0b9b4-118">Optional element.</span></span><br /><br /> <span data-ttu-id="0b9b4-119">定义要使用此列表项必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="0b9b4-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="0b9b4-120">ListControl 的标记元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0b9b4-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="0b9b4-121">可选元素</span><span class="sxs-lookup"><span data-stu-id="0b9b4-121">Optional element</span></span><br /><br /> <span data-ttu-id="0b9b4-122">指定在行的属性或脚本值左侧显示的标签。</span><span class="sxs-lookup"><span data-stu-id="0b9b4-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="0b9b4-123">ListControl 的名称名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0b9b4-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="0b9b4-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="0b9b4-124">Optional element.</span></span><br /><br /> <span data-ttu-id="0b9b4-125">指定其值显示在行中的 .NET 属性。</span><span class="sxs-lookup"><span data-stu-id="0b9b4-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="0b9b4-126">ListControl 的的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0b9b4-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="0b9b4-127">可选元素。</span><span class="sxs-lookup"><span data-stu-id="0b9b4-127">Optional element.</span></span><br /><br /> <span data-ttu-id="0b9b4-128">指定其值在行中显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="0b9b4-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0b9b4-129">父元素</span><span class="sxs-lookup"><span data-stu-id="0b9b4-129">Parent Elements</span></span>

|<span data-ttu-id="0b9b4-130">元素</span><span class="sxs-lookup"><span data-stu-id="0b9b4-130">Element</span></span>|<span data-ttu-id="0b9b4-131">描述</span><span class="sxs-lookup"><span data-stu-id="0b9b4-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0b9b4-132">List 控件的 ListItems 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="0b9b4-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="0b9b4-133">定义其值在列表视图中显示的属性和脚本。</span><span class="sxs-lookup"><span data-stu-id="0b9b4-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0b9b4-134">备注</span><span class="sxs-lookup"><span data-stu-id="0b9b4-134">Remarks</span></span>

<span data-ttu-id="0b9b4-135">有关列表视图组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="0b9b4-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0b9b4-136">示例</span><span class="sxs-lookup"><span data-stu-id="0b9b4-136">Example</span></span>

<span data-ttu-id="0b9b4-137">此示例显示了用于定义列表视图的三行的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="0b9b4-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="0b9b4-138">前两行显示 .NET 属性的值，最后一行显示脚本生成的值。</span><span class="sxs-lookup"><span data-stu-id="0b9b4-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0b9b4-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0b9b4-139">See Also</span></span>

[<span data-ttu-id="0b9b4-140">ListItems 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0b9b4-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="0b9b4-141">输入字符串的格式字符串元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0b9b4-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="0b9b4-142">元素的 Label 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0b9b4-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="0b9b4-143">元素名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0b9b4-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="0b9b4-144">脚本块元素（格式）</span><span class="sxs-lookup"><span data-stu-id="0b9b4-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="0b9b4-145">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="0b9b4-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="0b9b4-146">编写 Windows PowerShell 格式设置和类型文件</span><span class="sxs-lookup"><span data-stu-id="0b9b4-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
