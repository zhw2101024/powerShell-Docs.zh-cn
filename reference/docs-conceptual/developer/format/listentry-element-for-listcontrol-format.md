---
title: ListControl 的 ListEntry 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362746"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="7afed-102">ListEntry Element for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7afed-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="7afed-103">提供列表视图的定义。</span><span class="sxs-lookup"><span data-stu-id="7afed-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="7afed-104">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（format） ListEntries 元素（format） ListEntry 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="7afed-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7afed-105">语法</span><span class="sxs-lookup"><span data-stu-id="7afed-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7afed-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="7afed-106">Attributes and Elements</span></span>

<span data-ttu-id="7afed-107">以下各节介绍了 `ListEntry` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7afed-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7afed-108">属性</span><span class="sxs-lookup"><span data-stu-id="7afed-108">Attributes</span></span>

<span data-ttu-id="7afed-109">无。</span><span class="sxs-lookup"><span data-stu-id="7afed-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7afed-110">子元素</span><span class="sxs-lookup"><span data-stu-id="7afed-110">Child Elements</span></span>

|<span data-ttu-id="7afed-111">元素</span><span class="sxs-lookup"><span data-stu-id="7afed-111">Element</span></span>|<span data-ttu-id="7afed-112">描述</span><span class="sxs-lookup"><span data-stu-id="7afed-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7afed-113">ListEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7afed-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="7afed-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="7afed-114">Optional element.</span></span><br /><br /> <span data-ttu-id="7afed-115">定义使用此列表视图定义的 .NET 对象，或使用此定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="7afed-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="7afed-116">ListItems 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7afed-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="7afed-117">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="7afed-117">Required element.</span></span><br /><br /> <span data-ttu-id="7afed-118">定义其值由列表视图显示的属性和脚本。</span><span class="sxs-lookup"><span data-stu-id="7afed-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7afed-119">父元素</span><span class="sxs-lookup"><span data-stu-id="7afed-119">Parent Elements</span></span>

|<span data-ttu-id="7afed-120">元素</span><span class="sxs-lookup"><span data-stu-id="7afed-120">Element</span></span>|<span data-ttu-id="7afed-121">描述</span><span class="sxs-lookup"><span data-stu-id="7afed-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7afed-122">ListEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7afed-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="7afed-123">提供列表视图的定义。</span><span class="sxs-lookup"><span data-stu-id="7afed-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7afed-124">备注</span><span class="sxs-lookup"><span data-stu-id="7afed-124">Remarks</span></span>

<span data-ttu-id="7afed-125">列表视图是显示每个对象的属性值或脚本值的列表格式。</span><span class="sxs-lookup"><span data-stu-id="7afed-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="7afed-126">有关列表视图的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="7afed-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7afed-127">示例</span><span class="sxs-lookup"><span data-stu-id="7afed-127">Example</span></span>

<span data-ttu-id="7afed-128">此示例显示了为[system.serviceprocess. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象定义列表视图的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="7afed-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="7afed-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7afed-129">See Also</span></span>

[<span data-ttu-id="7afed-130">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="7afed-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="7afed-131">ListEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7afed-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="7afed-132">ListEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7afed-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="7afed-133">ListItems 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7afed-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="7afed-134">编写 Windows PowerShell 格式设置和类型文件</span><span class="sxs-lookup"><span data-stu-id="7afed-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
