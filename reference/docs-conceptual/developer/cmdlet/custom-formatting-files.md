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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369826"
---
# <a name="custom-formatting-files"></a><span data-ttu-id="d13e2-102">自定义格式设置文件</span><span class="sxs-lookup"><span data-stu-id="d13e2-102">Custom Formatting Files</span></span>

<span data-ttu-id="d13e2-103">Cmdlet、函数和脚本返回的对象的显示格式是使用格式设置文件（types.ps1xml 文件）定义的。</span><span class="sxs-lookup"><span data-stu-id="d13e2-103">The display format for the objects returned by cmdlets, functions, and scripts are defined using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="d13e2-104">Windows PowerShell 会提供其中几个文件来定义 Windows PowerShell cmdlet 返回的这些对象的默认显示格式。</span><span class="sxs-lookup"><span data-stu-id="d13e2-104">Several of these files are provided by Windows PowerShell to define the default display format for those objects returned by Windows PowerShell cmdlets.</span></span> <span data-ttu-id="d13e2-105">但是，您还可以创建自己的自定义格式设置文件来覆盖默认显示格式，或定义您自己的命令返回的对象的显示。</span><span class="sxs-lookup"><span data-stu-id="d13e2-105">However, you can also create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

<span data-ttu-id="d13e2-106">Windows PowerShell 使用这些格式设置文件中的数据来确定显示的内容以及如何设置数据的格式。</span><span class="sxs-lookup"><span data-stu-id="d13e2-106">Windows PowerShell uses the data in these formatting files to determine what is displayed and how the data is formatted.</span></span> <span data-ttu-id="d13e2-107">显示的数据可以包括对象的属性或脚本块的值。</span><span class="sxs-lookup"><span data-stu-id="d13e2-107">The displayed data can include the properties of an object or the value of a script block.</span></span>  <span data-ttu-id="d13e2-108">如果希望显示某个不能直接从对象的属性中使用的值，则使用脚本块。</span><span class="sxs-lookup"><span data-stu-id="d13e2-108">Script blocks are used if you want to display some value that is not available directly from the properties of an object.</span></span> <span data-ttu-id="d13e2-109">例如，你可能想要添加一个对象的两个属性的值，并将 sum 显示为单独的数据片段。</span><span class="sxs-lookup"><span data-stu-id="d13e2-109">For example, you may want to add the value of two properties of an object and display the sum as a separate piece of data.</span></span> <span data-ttu-id="d13e2-110">编写您自己的格式化文件时，需要为要显示的对象定义*视图*。</span><span class="sxs-lookup"><span data-stu-id="d13e2-110">When you write your own formatting file, you will need to define *views* for the objects that you want to display.</span></span> <span data-ttu-id="d13e2-111">您可以为每个对象定义一个视图，可以为多个对象定义一个视图，也可以为同一对象定义多个视图。</span><span class="sxs-lookup"><span data-stu-id="d13e2-111">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="d13e2-112">您可以定义的视图数没有限制。</span><span class="sxs-lookup"><span data-stu-id="d13e2-112">There is no limit to the number of views that you can define.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d13e2-113">格式化文件不确定返回到管道的对象的元素。</span><span class="sxs-lookup"><span data-stu-id="d13e2-113">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="d13e2-114">当对象返回到管道时，该对象的所有成员都可用。</span><span class="sxs-lookup"><span data-stu-id="d13e2-114">When an object is returned to the pipeline, all members of that object are available.</span></span>

## <a name="format-views"></a><span data-ttu-id="d13e2-115">格式视图</span><span class="sxs-lookup"><span data-stu-id="d13e2-115">Format Views</span></span>

<span data-ttu-id="d13e2-116">格式视图可按表格式显示对象、列表格式、宽格式和自定义格式。</span><span class="sxs-lookup"><span data-stu-id="d13e2-116">Formatting views can display objects in a table format, a list format, a wide format, and a custom format.</span></span> <span data-ttu-id="d13e2-117">大多数情况下，每个格式设置定义由一组描述视图的 XML 标记来描述。</span><span class="sxs-lookup"><span data-stu-id="d13e2-117">For the most part, each formatting definition is described by a set of XML tags that describe a view.</span></span> <span data-ttu-id="d13e2-118">每个视图都包含视图的名称、使用该视图的对象和视图的元素，例如表视图的列和行信息。</span><span class="sxs-lookup"><span data-stu-id="d13e2-118">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="d13e2-119">以下视图可用。</span><span class="sxs-lookup"><span data-stu-id="d13e2-119">The following views are available.</span></span>

<span data-ttu-id="d13e2-120">表视图在一个或多个列中列出对象或脚本块值的属性。</span><span class="sxs-lookup"><span data-stu-id="d13e2-120">Table view Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="d13e2-121">每个列表示对象的一个属性或一个脚本块值。</span><span class="sxs-lookup"><span data-stu-id="d13e2-121">Each column represents a property of the object or a script block value.</span></span> <span data-ttu-id="d13e2-122">您可以定义显示对象的所有属性的表视图、对象属性的子集或属性和脚本块值的组合。</span><span class="sxs-lookup"><span data-stu-id="d13e2-122">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script block values.</span></span> <span data-ttu-id="d13e2-123">表中的每一行都表示一个返回的对象。</span><span class="sxs-lookup"><span data-stu-id="d13e2-123">Each row of the table represents a returned object.</span></span> <span data-ttu-id="d13e2-124">有关此视图的详细信息，请参阅[表视图](../format/creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d13e2-124">For more information about this view, see [Table View](../format/creating-a-table-view.md).</span></span>

<span data-ttu-id="d13e2-125">列表视图在单个列中列出对象或脚本块值的属性。</span><span class="sxs-lookup"><span data-stu-id="d13e2-125">List view Lists the properties of an object or a script block value in a single column.</span></span> <span data-ttu-id="d13e2-126">列表中的每一行都显示一个可选标签或属性名称，后跟属性或脚本块的值。</span><span class="sxs-lookup"><span data-stu-id="d13e2-126">Each row of the list displays an optional label or the property name followed by the value of the property or script block.</span></span> <span data-ttu-id="d13e2-127">有关此视图的详细信息，请参阅[列表视图](../format/creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d13e2-127">For more information about this view, see [List View](../format/creating-a-list-view.md).</span></span>

<span data-ttu-id="d13e2-128">宽视图列出对象的单个属性或一个或多个列中的脚本块值。</span><span class="sxs-lookup"><span data-stu-id="d13e2-128">Wide view Lists a single property of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="d13e2-129">此视图没有标签或标题。</span><span class="sxs-lookup"><span data-stu-id="d13e2-129">There is no label or header for this view.</span></span> <span data-ttu-id="d13e2-130">有关此视图的详细信息，请参阅[宽视图](../format/creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d13e2-130">For more information about this view, see [Wide View](../format/creating-a-wide-view.md).</span></span>

<span data-ttu-id="d13e2-131">自定义视图显示对象属性或脚本块值的可自定义视图，这些视图不遵守严格的表视图、列表视图或宽视图结构。</span><span class="sxs-lookup"><span data-stu-id="d13e2-131">Custom view Displays a customizable view of object properties or script block values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="d13e2-132">您可以定义一个独立的自定义视图，也可以定义另一个视图使用的自定义视图，如表视图或列表视图。</span><span class="sxs-lookup"><span data-stu-id="d13e2-132">You can define a standalone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="d13e2-133">有关此视图的详细信息，请参阅[自定义视图](../format/creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="d13e2-133">For more information about this view, see [Custom View](../format/creating-custom-controls.md).</span></span>

## <a name="view-xml-elements"></a><span data-ttu-id="d13e2-134">查看 XML 元素</span><span class="sxs-lookup"><span data-stu-id="d13e2-134">View XML Elements</span></span>

<span data-ttu-id="d13e2-135">下面的示例显示用于定义包含两个列的表视图的 XML 标记。</span><span class="sxs-lookup"><span data-stu-id="d13e2-135">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="d13e2-136">[ViewDefinitions](../format/viewdefinitions-element-format.md)元素是在格式设置文件中定义的所有视图的容器元素。</span><span class="sxs-lookup"><span data-stu-id="d13e2-136">The [ViewDefinitions](../format/viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="d13e2-137">[View](../format/view-element-format.md)元素定义特定的表、列表、宽视图或自定义视图。</span><span class="sxs-lookup"><span data-stu-id="d13e2-137">The [View](../format/view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="d13e2-138">在每个视图中， [name](../format/name-element-for-view-format.md)元素指定视图的名称， [ViewSelectedBy](../format/viewselectedby-element-format.md)元素定义使用视图的对象，不同的控件元素（如 `TableControl` 元素）定义视图的格式。</span><span class="sxs-lookup"><span data-stu-id="d13e2-138">Within each view, the [Name](../format/name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](../format/viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element) define the format of the view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d13e2-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d13e2-139">See Also</span></span>

[<span data-ttu-id="d13e2-140">表视图</span><span class="sxs-lookup"><span data-stu-id="d13e2-140">Table View</span></span>](../format/creating-a-table-view.md)

[<span data-ttu-id="d13e2-141">列表视图</span><span class="sxs-lookup"><span data-stu-id="d13e2-141">List View</span></span>](../format/creating-a-list-view.md)

[<span data-ttu-id="d13e2-142">宽视图</span><span class="sxs-lookup"><span data-stu-id="d13e2-142">Wide View</span></span>](../format/creating-a-wide-view.md)

[<span data-ttu-id="d13e2-143">自定义视图</span><span class="sxs-lookup"><span data-stu-id="d13e2-143">Custom View</span></span>](../format/creating-custom-controls.md)

[<span data-ttu-id="d13e2-144">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d13e2-144">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
