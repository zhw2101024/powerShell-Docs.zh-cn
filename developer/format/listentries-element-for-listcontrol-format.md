---
title: ListControl （格式） 的 ListEntries 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856783"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="b1289-102">ListEntries Element for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b1289-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="b1289-103">提供了列表视图的定义。</span><span class="sxs-lookup"><span data-stu-id="b1289-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="b1289-104">列表视图中必须指定一个或多个定义。</span><span class="sxs-lookup"><span data-stu-id="b1289-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="b1289-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b1289-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b1289-106">语法</span><span class="sxs-lookup"><span data-stu-id="b1289-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b1289-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="b1289-107">Attributes and Elements</span></span>

<span data-ttu-id="b1289-108">以下各节描述了特性、 子元素和父元素的`ListEntries`元素。</span><span class="sxs-lookup"><span data-stu-id="b1289-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="b1289-109">必须指定至少一个子元素。</span><span class="sxs-lookup"><span data-stu-id="b1289-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="b1289-110">特性</span><span class="sxs-lookup"><span data-stu-id="b1289-110">Attributes</span></span>

<span data-ttu-id="b1289-111">无。</span><span class="sxs-lookup"><span data-stu-id="b1289-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b1289-112">子元素</span><span class="sxs-lookup"><span data-stu-id="b1289-112">Child Elements</span></span>

|<span data-ttu-id="b1289-113">元素</span><span class="sxs-lookup"><span data-stu-id="b1289-113">Element</span></span>|<span data-ttu-id="b1289-114">描述</span><span class="sxs-lookup"><span data-stu-id="b1289-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b1289-115">ListEntry 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b1289-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="b1289-116">提供列表视图中的定义。</span><span class="sxs-lookup"><span data-stu-id="b1289-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b1289-117">父元素</span><span class="sxs-lookup"><span data-stu-id="b1289-117">Parent Elements</span></span>

|<span data-ttu-id="b1289-118">元素</span><span class="sxs-lookup"><span data-stu-id="b1289-118">Element</span></span>|<span data-ttu-id="b1289-119">描述</span><span class="sxs-lookup"><span data-stu-id="b1289-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b1289-120">ListControl 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b1289-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="b1289-121">定义视图以列表格式。</span><span class="sxs-lookup"><span data-stu-id="b1289-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b1289-122">备注</span><span class="sxs-lookup"><span data-stu-id="b1289-122">Remarks</span></span>

<span data-ttu-id="b1289-123">有关列表视图的详细信息，请参阅[列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="b1289-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b1289-124">示例</span><span class="sxs-lookup"><span data-stu-id="b1289-124">Example</span></span>

<span data-ttu-id="b1289-125">此示例显示了定义的列表视图的 XML 元素[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象。</span><span class="sxs-lookup"><span data-stu-id="b1289-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b1289-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b1289-126">See Also</span></span>

[<span data-ttu-id="b1289-127">ListControl 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b1289-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="b1289-128">ListEntry 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="b1289-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="b1289-129">列表视图</span><span class="sxs-lookup"><span data-stu-id="b1289-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="b1289-130">编写 Windows PowerShell 格式设置和文件类型</span><span class="sxs-lookup"><span data-stu-id="b1289-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
