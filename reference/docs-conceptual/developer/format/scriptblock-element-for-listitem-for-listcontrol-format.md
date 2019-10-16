---
title: ListControl 的的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364806"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="43f01-102">ScriptBlock Element for ListItem for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="43f01-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="43f01-103">指定其值在行中显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="43f01-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="43f01-104">用于 ListEntry 的 ListEntries for ListControl （Format） ListItems 元素的 ListControl （Format） ListEntry 元素的 Configuration Element （Format） ViewDefinitions 元素（格式） ListControl 元素（format） ListEntries 元素对于 ListControl （Format）的 ListControl （格式） ListItems 的 ListControl （格式） ScriptBlock 元素</span><span class="sxs-lookup"><span data-stu-id="43f01-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="43f01-105">语法</span><span class="sxs-lookup"><span data-stu-id="43f01-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="43f01-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="43f01-106">Attributes and Elements</span></span>

<span data-ttu-id="43f01-107">以下各节介绍了 `ScriptBlock` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="43f01-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="43f01-108">属性</span><span class="sxs-lookup"><span data-stu-id="43f01-108">Attributes</span></span>

<span data-ttu-id="43f01-109">无。</span><span class="sxs-lookup"><span data-stu-id="43f01-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="43f01-110">子元素</span><span class="sxs-lookup"><span data-stu-id="43f01-110">Child Elements</span></span>

<span data-ttu-id="43f01-111">无。</span><span class="sxs-lookup"><span data-stu-id="43f01-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="43f01-112">父元素</span><span class="sxs-lookup"><span data-stu-id="43f01-112">Parent Elements</span></span>

|<span data-ttu-id="43f01-113">元素</span><span class="sxs-lookup"><span data-stu-id="43f01-113">Element</span></span>|<span data-ttu-id="43f01-114">描述</span><span class="sxs-lookup"><span data-stu-id="43f01-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="43f01-115">元素（格式）</span><span class="sxs-lookup"><span data-stu-id="43f01-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="43f01-116">定义其值显示在列表视图的行中的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="43f01-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="43f01-117">文本值</span><span class="sxs-lookup"><span data-stu-id="43f01-117">Text Value</span></span>

<span data-ttu-id="43f01-118">指定其值在行中显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="43f01-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="43f01-119">备注</span><span class="sxs-lookup"><span data-stu-id="43f01-119">Remarks</span></span>

<span data-ttu-id="43f01-120">如果指定此元素，则不能指定[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="43f01-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="43f01-121">有关在列表视图中指定脚本的详细信息，请参阅[列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="43f01-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="43f01-122">示例</span><span class="sxs-lookup"><span data-stu-id="43f01-122">Example</span></span>

<span data-ttu-id="43f01-123">下面的示例演示如何指定显示其值的属性。</span><span class="sxs-lookup"><span data-stu-id="43f01-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="43f01-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="43f01-124">See Also</span></span>

[<span data-ttu-id="43f01-125">ListControl 的名称名称元素（格式）</span><span class="sxs-lookup"><span data-stu-id="43f01-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="43f01-126">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="43f01-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="43f01-127">ListControl 的 ListItems 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="43f01-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="43f01-128">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="43f01-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
