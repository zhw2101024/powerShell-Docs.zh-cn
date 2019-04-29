---
title: ListControl 元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065251"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="00689-102">ListControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="00689-102">ListControl Element (Format)</span></span>

<span data-ttu-id="00689-103">定义视图以列表格式。</span><span class="sxs-lookup"><span data-stu-id="00689-103">Defines a list format for the view.</span></span>

<span data-ttu-id="00689-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="00689-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="00689-105">语法</span><span class="sxs-lookup"><span data-stu-id="00689-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="00689-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="00689-106">Attributes and Elements</span></span>

<span data-ttu-id="00689-107">以下各节描述了特性、 子元素和父元素的`ListControl`元素。</span><span class="sxs-lookup"><span data-stu-id="00689-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="00689-108">此元素必须包含单个子元素。</span><span class="sxs-lookup"><span data-stu-id="00689-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="00689-109">属性</span><span class="sxs-lookup"><span data-stu-id="00689-109">Attributes</span></span>

<span data-ttu-id="00689-110">无。</span><span class="sxs-lookup"><span data-stu-id="00689-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="00689-111">子元素</span><span class="sxs-lookup"><span data-stu-id="00689-111">Child Elements</span></span>

|<span data-ttu-id="00689-112">元素</span><span class="sxs-lookup"><span data-stu-id="00689-112">Element</span></span>|<span data-ttu-id="00689-113">说明</span><span class="sxs-lookup"><span data-stu-id="00689-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="00689-114">ListEntries 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="00689-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="00689-115">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="00689-115">Required element.</span></span><br /><br /> <span data-ttu-id="00689-116">提供了列表视图的定义。</span><span class="sxs-lookup"><span data-stu-id="00689-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="00689-117">父元素</span><span class="sxs-lookup"><span data-stu-id="00689-117">Parent Elements</span></span>

|<span data-ttu-id="00689-118">元素</span><span class="sxs-lookup"><span data-stu-id="00689-118">Element</span></span>|<span data-ttu-id="00689-119">说明</span><span class="sxs-lookup"><span data-stu-id="00689-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="00689-120">视图元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="00689-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="00689-121">定义一个视图，它用于显示一个或多个对象的成员。</span><span class="sxs-lookup"><span data-stu-id="00689-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="00689-122">备注</span><span class="sxs-lookup"><span data-stu-id="00689-122">Remarks</span></span>

<span data-ttu-id="00689-123">有关创建列表视图的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="00689-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="00689-124">示例</span><span class="sxs-lookup"><span data-stu-id="00689-124">Example</span></span>

<span data-ttu-id="00689-125">此示例中显示的列表视图[System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象。</span><span class="sxs-lookup"><span data-stu-id="00689-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="00689-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="00689-126">See Also</span></span>

[<span data-ttu-id="00689-127">视图元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="00689-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="00689-128">ListEntries 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="00689-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="00689-129">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="00689-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="00689-130">编写 Windows PowerShell 格式设置和文件类型</span><span class="sxs-lookup"><span data-stu-id="00689-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
