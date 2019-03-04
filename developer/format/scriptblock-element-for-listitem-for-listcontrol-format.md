---
title: ListControl （格式） 的列表项的脚本块元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855553"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="0f96f-102">ScriptBlock Element for ListItem for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0f96f-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="0f96f-103">指定其值显示的行中的脚本。</span><span class="sxs-lookup"><span data-stu-id="0f96f-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="0f96f-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） ListControl 元素 （格式） ListEntries 元素 ListEntries ListEntry ListControl （格式） Listitem 元素的 ListControl （格式） ListEntry 元素ListControl （格式） ScriptBlock ListControl （格式） 的 ListItem 元素 ListItems ListControl （格式） ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="0f96f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0f96f-105">语法</span><span class="sxs-lookup"><span data-stu-id="0f96f-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0f96f-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="0f96f-106">Attributes and Elements</span></span>

<span data-ttu-id="0f96f-107">以下各节描述了特性、 子元素和父元素的`ScriptBlock`元素。</span><span class="sxs-lookup"><span data-stu-id="0f96f-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0f96f-108">特性</span><span class="sxs-lookup"><span data-stu-id="0f96f-108">Attributes</span></span>

<span data-ttu-id="0f96f-109">无。</span><span class="sxs-lookup"><span data-stu-id="0f96f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0f96f-110">子元素</span><span class="sxs-lookup"><span data-stu-id="0f96f-110">Child Elements</span></span>

<span data-ttu-id="0f96f-111">无。</span><span class="sxs-lookup"><span data-stu-id="0f96f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0f96f-112">父元素</span><span class="sxs-lookup"><span data-stu-id="0f96f-112">Parent Elements</span></span>

|<span data-ttu-id="0f96f-113">元素</span><span class="sxs-lookup"><span data-stu-id="0f96f-113">Element</span></span>|<span data-ttu-id="0f96f-114">描述</span><span class="sxs-lookup"><span data-stu-id="0f96f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0f96f-115">ListItem 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="0f96f-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="0f96f-116">定义属性或其值显示在列表视图的行中的脚本。</span><span class="sxs-lookup"><span data-stu-id="0f96f-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0f96f-117">文本值</span><span class="sxs-lookup"><span data-stu-id="0f96f-117">Text Value</span></span>

<span data-ttu-id="0f96f-118">指定其值显示的行中的脚本。</span><span class="sxs-lookup"><span data-stu-id="0f96f-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="0f96f-119">备注</span><span class="sxs-lookup"><span data-stu-id="0f96f-119">Remarks</span></span>

<span data-ttu-id="0f96f-120">当指定此元素时，不能指定[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="0f96f-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="0f96f-121">在列表视图中指定脚本的详细信息，请参阅[列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="0f96f-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0f96f-122">示例</span><span class="sxs-lookup"><span data-stu-id="0f96f-122">Example</span></span>

<span data-ttu-id="0f96f-123">下面的示例演示如何指定其值显示的属性。</span><span class="sxs-lookup"><span data-stu-id="0f96f-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="0f96f-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0f96f-124">See Also</span></span>

[<span data-ttu-id="0f96f-125">PropertyName ListControl （格式） 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="0f96f-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="0f96f-126">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="0f96f-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="0f96f-127">ListItems 的 ListControl （格式） 的 ListItem 元素</span><span class="sxs-lookup"><span data-stu-id="0f96f-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="0f96f-128">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="0f96f-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
