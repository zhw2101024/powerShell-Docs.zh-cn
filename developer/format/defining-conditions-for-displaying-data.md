---
title: 定义用于显示数据的条件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066322"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="af1d7-102">定义用于显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="af1d7-102">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="af1d7-103">在定义的视图或控件显示的数据时，可以指定要显示的数据必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="af1d7-103">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="af1d7-104">由特定的属性，或脚本时，可触发条件或属性值的计算结果为`true`。</span><span class="sxs-lookup"><span data-stu-id="af1d7-104">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="af1d7-105">当满足选择条件，则将使用视图或控件的定义。</span><span class="sxs-lookup"><span data-stu-id="af1d7-105">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="af1d7-106">指定选择条件的定义</span><span class="sxs-lookup"><span data-stu-id="af1d7-106">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="af1d7-107">创建视图或控件的定义时`EntrySelectedBy`元素用于指定哪些对象将使用的定义或定义要使用哪种条件必须存在。</span><span class="sxs-lookup"><span data-stu-id="af1d7-107">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="af1d7-108">通过指定的条件`SelectionCondition`元素。</span><span class="sxs-lookup"><span data-stu-id="af1d7-108">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="af1d7-109">在以下示例中，选择条件指定的表视图的定义。</span><span class="sxs-lookup"><span data-stu-id="af1d7-109">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="af1d7-110">定义用于在此示例中，仅当指定的脚本的计算结果为`true`。</span><span class="sxs-lookup"><span data-stu-id="af1d7-110">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <SelectionCondition>
      <ScriptBlock>ScriptToEvaluate</ScriptBlock>
    </SelectionCondition>
  </EntrySelectedBy>
  <TableColumnItems>
  </TableColumnItems>
</TableRowEntry>

```

<span data-ttu-id="af1d7-111">可以为视图或控件的定义指定的选择条件数目没有限制。</span><span class="sxs-lookup"><span data-stu-id="af1d7-111">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="af1d7-112">唯一的要求如下所示：</span><span class="sxs-lookup"><span data-stu-id="af1d7-112">The only requirements are the following:</span></span>

- <span data-ttu-id="af1d7-113">选择条件必须指定一个属性名称或脚本来触发条件，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="af1d7-113">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="af1d7-114">选择条件可以指定任意数量的.NET 类型，或者选择设置，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="af1d7-114">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="af1d7-115">指定项的选择条件</span><span class="sxs-lookup"><span data-stu-id="af1d7-115">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="af1d7-116">此外可以指定当由列表视图或控件的项包括`ItemSelectionCondition`项定义中的元素。</span><span class="sxs-lookup"><span data-stu-id="af1d7-116">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="af1d7-117">在以下示例中，列表视图的项被指定选择条件。</span><span class="sxs-lookup"><span data-stu-id="af1d7-117">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="af1d7-118">在此示例中，仅当该脚本的计算结果为时使用了项`true`。</span><span class="sxs-lookup"><span data-stu-id="af1d7-118">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="af1d7-119">可以指定只有一个选择条件的项。</span><span class="sxs-lookup"><span data-stu-id="af1d7-119">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="af1d7-120">和条件必须指定一个属性名称或脚本来触发条件，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="af1d7-120">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="af1d7-121">XML 元素</span><span class="sxs-lookup"><span data-stu-id="af1d7-121">XML Elements</span></span>

 <span data-ttu-id="af1d7-122">以下 XML 元素用于创建所选内容的条件。</span><span class="sxs-lookup"><span data-stu-id="af1d7-122">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="af1d7-123">以下元素指定视图定义的选择条件：</span><span class="sxs-lookup"><span data-stu-id="af1d7-123">The following elements specify selection conditions for view definitions:</span></span>

    - [<span data-ttu-id="af1d7-124">TableControl （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="af1d7-124">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="af1d7-125">ListControl （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="af1d7-125">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="af1d7-126">WideControl （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="af1d7-126">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="af1d7-127">CustomControl （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="af1d7-127">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="af1d7-128">以下元素指定选择条件的常见和视图控件定义：</span><span class="sxs-lookup"><span data-stu-id="af1d7-128">The following elements specify selection conditions for common and view control definitions:</span></span>

    - [<span data-ttu-id="af1d7-129">配置 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="af1d7-129">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="af1d7-130">视图 （格式） 的控件的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="af1d7-130">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="af1d7-131">下面的元素指定扩展的集合对象的选择条件：</span><span class="sxs-lookup"><span data-stu-id="af1d7-131">The following element specifies the selection condition for expanding collection objects:</span></span>

    - [<span data-ttu-id="af1d7-132">EnumerableExpansion （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="af1d7-132">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="af1d7-133">下面的元素指定用于显示数据的新组选择条件：</span><span class="sxs-lookup"><span data-stu-id="af1d7-133">The following element specifies the selection condition for displaying a new group of data:</span></span>

    - [<span data-ttu-id="af1d7-134">GroupBy （格式） 的 EntrySelectedBy SelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="af1d7-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="af1d7-135">下面的元素指定列表视图项选择条件：</span><span class="sxs-lookup"><span data-stu-id="af1d7-135">The following element specifies an item selection condition for a list view:</span></span>

    - [<span data-ttu-id="af1d7-136">ItemSelectionCondition ListControl （格式） 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="af1d7-136">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="af1d7-137">以下元素指定控件的项选择条件：</span><span class="sxs-lookup"><span data-stu-id="af1d7-137">The following elements specify an item selection condition for controls:</span></span>

    - [<span data-ttu-id="af1d7-138">配置 （格式） 的控件的 ExpressionBinding 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="af1d7-138">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="af1d7-139">ExpressionBinding 的 Controls 的视图 （格式） 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="af1d7-139">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [<span data-ttu-id="af1d7-140">CustomControl （格式） 的 ExpressionBinding 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="af1d7-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="af1d7-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="af1d7-141">See Also</span></span>

[<span data-ttu-id="af1d7-142">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="af1d7-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
