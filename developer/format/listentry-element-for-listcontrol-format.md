---
title: ListControl （格式） 的 ListEntry 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065217"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="b976a-102">ListEntry Element for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b976a-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="b976a-103">提供列表视图中的定义。</span><span class="sxs-lookup"><span data-stu-id="b976a-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="b976a-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 （格式） ListEntry 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b976a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b976a-105">语法</span><span class="sxs-lookup"><span data-stu-id="b976a-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b976a-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b976a-106">Attributes and Elements</span></span>

<span data-ttu-id="b976a-107">以下各节描述了特性、 子元素和父元素的`ListEntry`元素。</span><span class="sxs-lookup"><span data-stu-id="b976a-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b976a-108">属性</span><span class="sxs-lookup"><span data-stu-id="b976a-108">Attributes</span></span>

<span data-ttu-id="b976a-109">无。</span><span class="sxs-lookup"><span data-stu-id="b976a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b976a-110">子元素</span><span class="sxs-lookup"><span data-stu-id="b976a-110">Child Elements</span></span>

|<span data-ttu-id="b976a-111">元素</span><span class="sxs-lookup"><span data-stu-id="b976a-111">Element</span></span>|<span data-ttu-id="b976a-112">说明</span><span class="sxs-lookup"><span data-stu-id="b976a-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b976a-113">ListEntry （格式） 的 EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="b976a-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="b976a-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="b976a-114">Optional element.</span></span><br /><br /> <span data-ttu-id="b976a-115">定义使用此列表视图定义或要使用此定义中必须存在的条件的.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="b976a-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="b976a-116">Listitem 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b976a-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="b976a-117">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="b976a-117">Required element.</span></span><br /><br /> <span data-ttu-id="b976a-118">定义属性和其值将由列表视图的脚本。</span><span class="sxs-lookup"><span data-stu-id="b976a-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b976a-119">父元素</span><span class="sxs-lookup"><span data-stu-id="b976a-119">Parent Elements</span></span>

|<span data-ttu-id="b976a-120">元素</span><span class="sxs-lookup"><span data-stu-id="b976a-120">Element</span></span>|<span data-ttu-id="b976a-121">说明</span><span class="sxs-lookup"><span data-stu-id="b976a-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b976a-122">ListEntries 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b976a-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="b976a-123">提供了列表视图的定义。</span><span class="sxs-lookup"><span data-stu-id="b976a-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b976a-124">备注</span><span class="sxs-lookup"><span data-stu-id="b976a-124">Remarks</span></span>

<span data-ttu-id="b976a-125">列表视图是以列表格式显示属性值或为每个对象的脚本值。</span><span class="sxs-lookup"><span data-stu-id="b976a-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="b976a-126">有关列表视图的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="b976a-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b976a-127">示例</span><span class="sxs-lookup"><span data-stu-id="b976a-127">Example</span></span>

<span data-ttu-id="b976a-128">此示例显示了定义的列表视图的 XML 元素[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象。</span><span class="sxs-lookup"><span data-stu-id="b976a-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b976a-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b976a-129">See Also</span></span>

[<span data-ttu-id="b976a-130">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="b976a-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="b976a-131">ListEntry （格式） 的 EntrySelectedBy 元素</span><span class="sxs-lookup"><span data-stu-id="b976a-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="b976a-132">ListEntries 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b976a-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="b976a-133">Listitem 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b976a-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="b976a-134">编写 Windows PowerShell 格式设置和文件类型</span><span class="sxs-lookup"><span data-stu-id="b976a-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
