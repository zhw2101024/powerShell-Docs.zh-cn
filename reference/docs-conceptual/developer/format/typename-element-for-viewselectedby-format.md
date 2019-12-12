---
title: ViewSelectedBy 的 TypeName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361436"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="aae38-102">TypeName Element for ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="aae38-102">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="aae38-103">指定视图显示的 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="aae38-103">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="aae38-104">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） ViewSelectedBy 元素（format） ViewSelectedBy 的 TypeName 元素（format）</span><span class="sxs-lookup"><span data-stu-id="aae38-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="aae38-105">语法</span><span class="sxs-lookup"><span data-stu-id="aae38-105">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aae38-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="aae38-106">Attributes and Elements</span></span>

<span data-ttu-id="aae38-107">以下各节介绍了 `TypeName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="aae38-107">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="aae38-108">属性</span><span class="sxs-lookup"><span data-stu-id="aae38-108">Attributes</span></span>

<span data-ttu-id="aae38-109">无。</span><span class="sxs-lookup"><span data-stu-id="aae38-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aae38-110">子元素</span><span class="sxs-lookup"><span data-stu-id="aae38-110">Child Elements</span></span>

<span data-ttu-id="aae38-111">无。</span><span class="sxs-lookup"><span data-stu-id="aae38-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="aae38-112">父元素</span><span class="sxs-lookup"><span data-stu-id="aae38-112">Parent Elements</span></span>

|<span data-ttu-id="aae38-113">元素</span><span class="sxs-lookup"><span data-stu-id="aae38-113">Element</span></span>|<span data-ttu-id="aae38-114">描述</span><span class="sxs-lookup"><span data-stu-id="aae38-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aae38-115">ViewSelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="aae38-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="aae38-116">定义视图显示的 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="aae38-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="aae38-117">文本值</span><span class="sxs-lookup"><span data-stu-id="aae38-117">Text Value</span></span>

<span data-ttu-id="aae38-118">指定 .NET 类型的完全限定名，如 `System.IO.DirectoryInfo`。</span><span class="sxs-lookup"><span data-stu-id="aae38-118">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="aae38-119">备注</span><span class="sxs-lookup"><span data-stu-id="aae38-119">Remarks</span></span>

<span data-ttu-id="aae38-120">有关此元素在不同视图中的使用方式的详细信息，请参阅[创建表视图](./creating-a-table-view.md)、[创建列表视图](./creating-a-list-view.md)、[创建宽视图](./creating-a-wide-view.md)和[自定义视图组件](./creating-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="aae38-120">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="aae38-121">示例</span><span class="sxs-lookup"><span data-stu-id="aae38-121">Example</span></span>

<span data-ttu-id="aae38-122">下面的示例演示如何为列表视图指定[Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象。</span><span class="sxs-lookup"><span data-stu-id="aae38-122">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="aae38-123">表、宽视图和自定义视图使用相同的架构。</span><span class="sxs-lookup"><span data-stu-id="aae38-123">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="aae38-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aae38-124">See Also</span></span>

[<span data-ttu-id="aae38-125">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="aae38-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="aae38-126">创建表视图</span><span class="sxs-lookup"><span data-stu-id="aae38-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="aae38-127">创建宽视图</span><span class="sxs-lookup"><span data-stu-id="aae38-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="aae38-128">创建自定义控件</span><span class="sxs-lookup"><span data-stu-id="aae38-128">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="aae38-129">ViewSelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="aae38-129">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="aae38-130">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="aae38-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
