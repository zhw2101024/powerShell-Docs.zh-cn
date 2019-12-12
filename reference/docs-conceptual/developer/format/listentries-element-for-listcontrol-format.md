---
title: ListControl 的 ListEntries 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362756"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="3ea5f-102">ListEntries Element for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3ea5f-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="3ea5f-103">提供列表视图的定义。</span><span class="sxs-lookup"><span data-stu-id="3ea5f-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="3ea5f-104">列表视图必须指定一个或多个定义。</span><span class="sxs-lookup"><span data-stu-id="3ea5f-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="3ea5f-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） ListControl 元素（format） ListEntries 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="3ea5f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3ea5f-106">语法</span><span class="sxs-lookup"><span data-stu-id="3ea5f-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3ea5f-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="3ea5f-107">Attributes and Elements</span></span>

<span data-ttu-id="3ea5f-108">以下各节介绍了 `ListEntries` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3ea5f-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="3ea5f-109">必须至少指定一个子元素。</span><span class="sxs-lookup"><span data-stu-id="3ea5f-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="3ea5f-110">属性</span><span class="sxs-lookup"><span data-stu-id="3ea5f-110">Attributes</span></span>

<span data-ttu-id="3ea5f-111">无。</span><span class="sxs-lookup"><span data-stu-id="3ea5f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3ea5f-112">子元素</span><span class="sxs-lookup"><span data-stu-id="3ea5f-112">Child Elements</span></span>

|<span data-ttu-id="3ea5f-113">元素</span><span class="sxs-lookup"><span data-stu-id="3ea5f-113">Element</span></span>|<span data-ttu-id="3ea5f-114">描述</span><span class="sxs-lookup"><span data-stu-id="3ea5f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ea5f-115">ListEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3ea5f-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="3ea5f-116">提供列表视图的定义。</span><span class="sxs-lookup"><span data-stu-id="3ea5f-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3ea5f-117">父元素</span><span class="sxs-lookup"><span data-stu-id="3ea5f-117">Parent Elements</span></span>

|<span data-ttu-id="3ea5f-118">元素</span><span class="sxs-lookup"><span data-stu-id="3ea5f-118">Element</span></span>|<span data-ttu-id="3ea5f-119">描述</span><span class="sxs-lookup"><span data-stu-id="3ea5f-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3ea5f-120">ListControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3ea5f-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="3ea5f-121">定义视图的列表格式。</span><span class="sxs-lookup"><span data-stu-id="3ea5f-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3ea5f-122">备注</span><span class="sxs-lookup"><span data-stu-id="3ea5f-122">Remarks</span></span>

<span data-ttu-id="3ea5f-123">有关列表视图的详细信息，请参阅[列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="3ea5f-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="3ea5f-124">示例</span><span class="sxs-lookup"><span data-stu-id="3ea5f-124">Example</span></span>

<span data-ttu-id="3ea5f-125">此示例显示了为[system.serviceprocess. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象定义列表视图的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="3ea5f-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3ea5f-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ea5f-126">See Also</span></span>

[<span data-ttu-id="3ea5f-127">ListControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3ea5f-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="3ea5f-128">ListEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="3ea5f-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="3ea5f-129">列表视图</span><span class="sxs-lookup"><span data-stu-id="3ea5f-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="3ea5f-130">编写 Windows PowerShell 格式设置和类型文件</span><span class="sxs-lookup"><span data-stu-id="3ea5f-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
