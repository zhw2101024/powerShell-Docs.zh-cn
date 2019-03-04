---
title: 自定义格式设置文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860603"
---
# <a name="custom-formatting-files"></a><span data-ttu-id="abe4a-102">自定义格式设置文件</span><span class="sxs-lookup"><span data-stu-id="abe4a-102">Custom Formatting Files</span></span>

<span data-ttu-id="abe4a-103">使用格式设置文件 （format.ps1xml 文件） 进行定义的 cmdlet、 函数和脚本返回的对象的显示格式。</span><span class="sxs-lookup"><span data-stu-id="abe4a-103">The display format for the objects returned by cmdlets, functions, and scripts are defined using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="abe4a-104">多个这些文件提供了 Windows PowerShell，若要定义由 Windows PowerShell cmdlet 返回这些对象的默认显示格式。</span><span class="sxs-lookup"><span data-stu-id="abe4a-104">Several of these files are provided by Windows PowerShell to define the default display format for those objects returned by Windows PowerShell cmdlets.</span></span> <span data-ttu-id="abe4a-105">但是，您还可以创建自己的自定义格式设置文件以覆盖默认显示格式，或若要定义自己的命令返回的对象的显示。</span><span class="sxs-lookup"><span data-stu-id="abe4a-105">However, you can also create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

<span data-ttu-id="abe4a-106">Windows PowerShell 将使用这些格式设置文件中的数据来确定显示的内容和设置数据的格式。</span><span class="sxs-lookup"><span data-stu-id="abe4a-106">Windows PowerShell uses the data in these formatting files to determine what is displayed and how the data is formatted.</span></span> <span data-ttu-id="abe4a-107">在显示的数据可以包括对象的属性或脚本块的值。</span><span class="sxs-lookup"><span data-stu-id="abe4a-107">The displayed data can include the properties of an object or the value of a script block.</span></span>  <span data-ttu-id="abe4a-108">如果你想要显示某些值不是可直接从对象的属性，则使用脚本块。</span><span class="sxs-lookup"><span data-stu-id="abe4a-108">Script blocks are used if you want to display some value that is not available directly from the properties of an object.</span></span> <span data-ttu-id="abe4a-109">例如，你可能想要添加两个对象的属性的值并显示为一个单独的数据的总和。</span><span class="sxs-lookup"><span data-stu-id="abe4a-109">For example, you may want to add the value of two properties of an object and display the sum as a separate piece of data.</span></span> <span data-ttu-id="abe4a-110">在编写您自己的格式文件时，你将需要定义*视图*你想要显示的对象。</span><span class="sxs-lookup"><span data-stu-id="abe4a-110">When you write your own formatting file, you will need to define *views* for the objects that you want to display.</span></span> <span data-ttu-id="abe4a-111">可以定义每个对象的单个视图，可以定义多个对象的单一视图也可以定义相同的对象的多个视图。</span><span class="sxs-lookup"><span data-stu-id="abe4a-111">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="abe4a-112">可以定义的视图数目没有限制。</span><span class="sxs-lookup"><span data-stu-id="abe4a-112">There is no limit to the number of views that you can define.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="abe4a-113">格式设置文件不用于确定返回到管道对象的元素。</span><span class="sxs-lookup"><span data-stu-id="abe4a-113">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="abe4a-114">当对象返回到管道时，该对象的所有成员都都可用。</span><span class="sxs-lookup"><span data-stu-id="abe4a-114">When an object is returned to the pipeline, all members of that object are available.</span></span>

## <a name="format-views"></a><span data-ttu-id="abe4a-115">设置视图的格式</span><span class="sxs-lookup"><span data-stu-id="abe4a-115">Format Views</span></span>

<span data-ttu-id="abe4a-116">格式设置的视图可以显示在表格格式、 以列表格式、 宽格式和自定义格式的对象。</span><span class="sxs-lookup"><span data-stu-id="abe4a-116">Formatting views can display objects in a table format, a list format, a wide format, and a custom format.</span></span> <span data-ttu-id="abe4a-117">大多数情况下，由一组描述视图的 XML 标记描述每个格式设置的定义。</span><span class="sxs-lookup"><span data-stu-id="abe4a-117">For the most part, each formatting definition is described by a set of XML tags that describe a view.</span></span> <span data-ttu-id="abe4a-118">每个视图包含视图的名称使用视图和视图，如表视图的列和行信息的元素的对象。</span><span class="sxs-lookup"><span data-stu-id="abe4a-118">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="abe4a-119">提供了以下视图。</span><span class="sxs-lookup"><span data-stu-id="abe4a-119">The following views are available.</span></span>

<span data-ttu-id="abe4a-120">表视图列出了对象或一个或多个列中的脚本块值的属性。</span><span class="sxs-lookup"><span data-stu-id="abe4a-120">Table view Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="abe4a-121">每个列表示的对象或脚本块值的属性。</span><span class="sxs-lookup"><span data-stu-id="abe4a-121">Each column represents a property of the object or a script block value.</span></span> <span data-ttu-id="abe4a-122">可以定义显示的对象的对象或属性和脚本块值的组合的属性子集的所有属性的表视图。</span><span class="sxs-lookup"><span data-stu-id="abe4a-122">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script block values.</span></span> <span data-ttu-id="abe4a-123">表的每一行表示一个返回的对象。</span><span class="sxs-lookup"><span data-stu-id="abe4a-123">Each row of the table represents a returned object.</span></span> <span data-ttu-id="abe4a-124">有关此视图的详细信息，请参阅[表视图](../format/creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="abe4a-124">For more information about this view, see [Table View](../format/creating-a-table-view.md).</span></span>

<span data-ttu-id="abe4a-125">列表视图列出了对象或单个列中的脚本块值的属性。</span><span class="sxs-lookup"><span data-stu-id="abe4a-125">List view Lists the properties of an object or a script block value in a single column.</span></span> <span data-ttu-id="abe4a-126">列表的每行显示的可选标签或跟属性或脚本块的值的属性名称。</span><span class="sxs-lookup"><span data-stu-id="abe4a-126">Each row of the list displays an optional label or the property name followed by the value of the property or script block.</span></span> <span data-ttu-id="abe4a-127">有关此视图的详细信息，请参阅[列表视图](../format/creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="abe4a-127">For more information about this view, see [List View](../format/creating-a-list-view.md).</span></span>

<span data-ttu-id="abe4a-128">宽视图列出了对象或一个或多个列中的脚本块值的单个属性。</span><span class="sxs-lookup"><span data-stu-id="abe4a-128">Wide view Lists a single property of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="abe4a-129">没有标签或此视图的标头。</span><span class="sxs-lookup"><span data-stu-id="abe4a-129">There is no label or header for this view.</span></span> <span data-ttu-id="abe4a-130">有关此视图的详细信息，请参阅[宽视图](../format/creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="abe4a-130">For more information about this view, see [Wide View](../format/creating-a-wide-view.md).</span></span>

<span data-ttu-id="abe4a-131">自定义视图显示不符合的表视图、 列表视图或宽视图刚性结构的可自定义视图的对象属性或脚本块值。</span><span class="sxs-lookup"><span data-stu-id="abe4a-131">Custom view Displays a customizable view of object properties or script block values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="abe4a-132">可以定义独立的自定义视图，也可以定义由另一个视图，如表视图或列表视图的自定义视图。</span><span class="sxs-lookup"><span data-stu-id="abe4a-132">You can define a standalone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="abe4a-133">有关此视图的详细信息，请参阅[的自定义视图](../format/creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="abe4a-133">For more information about this view, see [Custom View](../format/creating-custom-controls.md).</span></span>

## <a name="view-xml-elements"></a><span data-ttu-id="abe4a-134">查看 XML 元素</span><span class="sxs-lookup"><span data-stu-id="abe4a-134">View XML Elements</span></span>

<span data-ttu-id="abe4a-135">下面的示例演示用于定义包含两个列的表视图的 XML 标记。</span><span class="sxs-lookup"><span data-stu-id="abe4a-135">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="abe4a-136">[ViewDefinitions](../format/viewdefinitions-element-format.md)元素是格式设置文件中定义的所有视图的容器元素。</span><span class="sxs-lookup"><span data-stu-id="abe4a-136">The [ViewDefinitions](../format/viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="abe4a-137">[视图](../format/view-element-format.md)元素定义特定的表、 列表、 宽，或自定义视图。</span><span class="sxs-lookup"><span data-stu-id="abe4a-137">The [View](../format/view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="abe4a-138">在每个视图中，[名称](../format/name-element-for-view-format.md)元素指定的视图名称[ViewSelectedBy](../format/viewselectedby-element-format.md)元素定义使用的视图和不同的控件元素的对象 (如`TableControl`元素） 定义的视图格式。</span><span class="sxs-lookup"><span data-stu-id="abe4a-138">Within each view, the [Name](../format/name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](../format/viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element) define the format of the view.</span></span>

```xml
ViewDefinitions
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="abe4a-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="abe4a-139">See Also</span></span>

[<span data-ttu-id="abe4a-140">表视图</span><span class="sxs-lookup"><span data-stu-id="abe4a-140">Table View</span></span>](../format/creating-a-table-view.md)

[<span data-ttu-id="abe4a-141">列表视图</span><span class="sxs-lookup"><span data-stu-id="abe4a-141">List View</span></span>](../format/creating-a-list-view.md)

[<span data-ttu-id="abe4a-142">宽的视图</span><span class="sxs-lookup"><span data-stu-id="abe4a-142">Wide View</span></span>](../format/creating-a-wide-view.md)

[<span data-ttu-id="abe4a-143">自定义视图</span><span class="sxs-lookup"><span data-stu-id="abe4a-143">Custom View</span></span>](../format/creating-custom-controls.md)

[<span data-ttu-id="abe4a-144">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="abe4a-144">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
