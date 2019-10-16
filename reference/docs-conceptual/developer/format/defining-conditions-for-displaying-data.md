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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363896"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="21fc8-102">定义用于显示数据的条件</span><span class="sxs-lookup"><span data-stu-id="21fc8-102">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="21fc8-103">定义视图或控件显示的数据时，您可以指定一个必须存在的条件，以便显示数据。</span><span class="sxs-lookup"><span data-stu-id="21fc8-103">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="21fc8-104">条件可由特定属性触发，或者在脚本或属性值的计算结果为 `true` 时触发。</span><span class="sxs-lookup"><span data-stu-id="21fc8-104">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="21fc8-105">如果满足选择条件，将使用视图或控件的定义。</span><span class="sxs-lookup"><span data-stu-id="21fc8-105">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="21fc8-106">为定义指定选择条件</span><span class="sxs-lookup"><span data-stu-id="21fc8-106">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="21fc8-107">创建视图或控件的定义时，@no__t 的元素用于指定将使用定义的对象或必须存在的条件才能使用定义。</span><span class="sxs-lookup"><span data-stu-id="21fc8-107">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="21fc8-108">条件由 `SelectionCondition` 元素指定。</span><span class="sxs-lookup"><span data-stu-id="21fc8-108">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="21fc8-109">在下面的示例中，将为表视图的定义指定选择条件。</span><span class="sxs-lookup"><span data-stu-id="21fc8-109">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="21fc8-110">在此示例中，仅当指定的脚本计算为 `true` 时，才使用定义。</span><span class="sxs-lookup"><span data-stu-id="21fc8-110">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

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

<span data-ttu-id="21fc8-111">对于您可以为视图或控件的定义指定的选择条件数没有限制。</span><span class="sxs-lookup"><span data-stu-id="21fc8-111">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="21fc8-112">唯一的要求如下：</span><span class="sxs-lookup"><span data-stu-id="21fc8-112">The only requirements are the following:</span></span>

- <span data-ttu-id="21fc8-113">选择条件必须指定一个属性名称或脚本来触发条件，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="21fc8-113">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="21fc8-114">选择条件可以指定任意数量的 .NET 类型或选择集，但是不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="21fc8-114">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="21fc8-115">指定项的选择条件</span><span class="sxs-lookup"><span data-stu-id="21fc8-115">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="21fc8-116">你还可以通过在项定义中包含 `ItemSelectionCondition` 元素来指定何时使用列表视图或控件的项。</span><span class="sxs-lookup"><span data-stu-id="21fc8-116">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="21fc8-117">在下面的示例中，为列表视图的项指定了选择条件。</span><span class="sxs-lookup"><span data-stu-id="21fc8-117">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="21fc8-118">在此示例中，仅当将脚本计算为 `true` 时才使用此项。</span><span class="sxs-lookup"><span data-stu-id="21fc8-118">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="21fc8-119">只能为项指定一个选择条件。</span><span class="sxs-lookup"><span data-stu-id="21fc8-119">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="21fc8-120">条件必须指定一个属性名称或脚本来触发条件，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="21fc8-120">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="21fc8-121">XML 元素</span><span class="sxs-lookup"><span data-stu-id="21fc8-121">XML Elements</span></span>

 <span data-ttu-id="21fc8-122">以下 XML 元素用于创建选择条件。</span><span class="sxs-lookup"><span data-stu-id="21fc8-122">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="21fc8-123">以下元素指定了视图定义的选择条件：</span><span class="sxs-lookup"><span data-stu-id="21fc8-123">The following elements specify selection conditions for view definitions:</span></span>

    - [<span data-ttu-id="21fc8-124">TableControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21fc8-124">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="21fc8-125">ListControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21fc8-125">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="21fc8-126">WideControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21fc8-126">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="21fc8-127">CustomControl 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21fc8-127">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="21fc8-128">以下元素指定常用和视图控件定义的选择条件：</span><span class="sxs-lookup"><span data-stu-id="21fc8-128">The following elements specify selection conditions for common and view control definitions:</span></span>

    - [<span data-ttu-id="21fc8-129">用于配置的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21fc8-129">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="21fc8-130">用于视图的控件的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21fc8-130">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="21fc8-131">以下元素指定展开集合对象的选择条件：</span><span class="sxs-lookup"><span data-stu-id="21fc8-131">The following element specifies the selection condition for expanding collection objects:</span></span>

    - [<span data-ttu-id="21fc8-132">EnumerableExpansion 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21fc8-132">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="21fc8-133">以下元素指定用于显示新数据组的选择条件：</span><span class="sxs-lookup"><span data-stu-id="21fc8-133">The following element specifies the selection condition for displaying a new group of data:</span></span>

    - [<span data-ttu-id="21fc8-134">GroupBy 的 EntrySelectedBy 的 SelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21fc8-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="21fc8-135">以下元素为列表视图指定项选择条件：</span><span class="sxs-lookup"><span data-stu-id="21fc8-135">The following element specifies an item selection condition for a list view:</span></span>

    - [<span data-ttu-id="21fc8-136">ListControl 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21fc8-136">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="21fc8-137">以下元素为控件指定项选择条件：</span><span class="sxs-lookup"><span data-stu-id="21fc8-137">The following elements specify an item selection condition for controls:</span></span>

    - [<span data-ttu-id="21fc8-138">用于配置的控件的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21fc8-138">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="21fc8-139">用于视图的控件的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21fc8-139">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [<span data-ttu-id="21fc8-140">CustomControl 的 ExpressionBinding 的 ItemSelectionCondition 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="21fc8-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="21fc8-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="21fc8-141">See Also</span></span>

[<span data-ttu-id="21fc8-142">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="21fc8-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
