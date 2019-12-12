---
title: ListControl 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362776"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="d213d-102">ListControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="d213d-102">ListControl Element (Format)</span></span>

<span data-ttu-id="d213d-103">定义视图的列表格式。</span><span class="sxs-lookup"><span data-stu-id="d213d-103">Defines a list format for the view.</span></span>

<span data-ttu-id="d213d-104">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="d213d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d213d-105">语法</span><span class="sxs-lookup"><span data-stu-id="d213d-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="d213d-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="d213d-106">Attributes and Elements</span></span>

<span data-ttu-id="d213d-107">以下各节介绍了 `ListControl` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d213d-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="d213d-108">此元素必须只包含一个子元素。</span><span class="sxs-lookup"><span data-stu-id="d213d-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d213d-109">属性</span><span class="sxs-lookup"><span data-stu-id="d213d-109">Attributes</span></span>

<span data-ttu-id="d213d-110">无。</span><span class="sxs-lookup"><span data-stu-id="d213d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d213d-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d213d-111">Child Elements</span></span>

|<span data-ttu-id="d213d-112">元素</span><span class="sxs-lookup"><span data-stu-id="d213d-112">Element</span></span>|<span data-ttu-id="d213d-113">描述</span><span class="sxs-lookup"><span data-stu-id="d213d-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d213d-114">ListEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d213d-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="d213d-115">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="d213d-115">Required element.</span></span><br /><br /> <span data-ttu-id="d213d-116">提供列表视图的定义。</span><span class="sxs-lookup"><span data-stu-id="d213d-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d213d-117">父元素</span><span class="sxs-lookup"><span data-stu-id="d213d-117">Parent Elements</span></span>

|<span data-ttu-id="d213d-118">元素</span><span class="sxs-lookup"><span data-stu-id="d213d-118">Element</span></span>|<span data-ttu-id="d213d-119">描述</span><span class="sxs-lookup"><span data-stu-id="d213d-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d213d-120">View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d213d-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="d213d-121">定义一个视图，该视图用于显示一个或多个对象的成员。</span><span class="sxs-lookup"><span data-stu-id="d213d-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d213d-122">备注</span><span class="sxs-lookup"><span data-stu-id="d213d-122">Remarks</span></span>

<span data-ttu-id="d213d-123">有关创建列表视图的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d213d-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d213d-124">示例</span><span class="sxs-lookup"><span data-stu-id="d213d-124">Example</span></span>

<span data-ttu-id="d213d-125">此示例显示了[system.serviceprocess. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象的列表视图。</span><span class="sxs-lookup"><span data-stu-id="d213d-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d213d-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d213d-126">See Also</span></span>

[<span data-ttu-id="d213d-127">View 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d213d-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="d213d-128">ListEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="d213d-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="d213d-129">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="d213d-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d213d-130">编写 Windows PowerShell 格式设置和类型文件</span><span class="sxs-lookup"><span data-stu-id="d213d-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
