---
title: 脚本块元素 WideControl （格式） 的 WideItem |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858023"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="ab222-102">ScriptBlock Element for WideItem for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ab222-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="ab222-103">指定其值宽视图中显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="ab222-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="ab222-104">元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） WideEntries 元素 （格式） WideEntry 元素 （格式） WideItem 元素 （格式） 脚本块的配置元素 WideItem （格式）</span><span class="sxs-lookup"><span data-stu-id="ab222-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ab222-105">语法</span><span class="sxs-lookup"><span data-stu-id="ab222-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ab222-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="ab222-106">Attributes and Elements</span></span>

<span data-ttu-id="ab222-107">以下各节描述的特性、 子元素和父元素的`ScriptBlock`元素。</span><span class="sxs-lookup"><span data-stu-id="ab222-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ab222-108">属性</span><span class="sxs-lookup"><span data-stu-id="ab222-108">Attributes</span></span>

<span data-ttu-id="ab222-109">无。</span><span class="sxs-lookup"><span data-stu-id="ab222-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ab222-110">子元素</span><span class="sxs-lookup"><span data-stu-id="ab222-110">Child Elements</span></span>

<span data-ttu-id="ab222-111">无。</span><span class="sxs-lookup"><span data-stu-id="ab222-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ab222-112">父元素</span><span class="sxs-lookup"><span data-stu-id="ab222-112">Parent Elements</span></span>

|<span data-ttu-id="ab222-113">元素</span><span class="sxs-lookup"><span data-stu-id="ab222-113">Element</span></span>|<span data-ttu-id="ab222-114">说明</span><span class="sxs-lookup"><span data-stu-id="ab222-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab222-115">WideItem 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="ab222-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="ab222-116">定义宽视图中显示其值的属性或脚本块。</span><span class="sxs-lookup"><span data-stu-id="ab222-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ab222-117">文本值</span><span class="sxs-lookup"><span data-stu-id="ab222-117">Text Value</span></span>

<span data-ttu-id="ab222-118">指定显示其值的脚本。</span><span class="sxs-lookup"><span data-stu-id="ab222-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="ab222-119">备注</span><span class="sxs-lookup"><span data-stu-id="ab222-119">Remarks</span></span>

<span data-ttu-id="ab222-120">有关较宽的视图的组件的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="ab222-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ab222-121">示例</span><span class="sxs-lookup"><span data-stu-id="ab222-121">Example</span></span>

<span data-ttu-id="ab222-122">此示例显示了`WideItem`元素，用于定义其值显示在视图中的脚本。</span><span class="sxs-lookup"><span data-stu-id="ab222-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="ab222-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab222-123">See Also</span></span>

[<span data-ttu-id="ab222-124">WideItem 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="ab222-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="ab222-125">创建较宽的视图</span><span class="sxs-lookup"><span data-stu-id="ab222-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ab222-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="ab222-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
