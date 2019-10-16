---
title: WideControl 的 WideItem 的 ScriptBlock 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362026"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="ea778-102">ScriptBlock Element for WideItem for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ea778-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="ea778-103">指定其值在宽视图中显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="ea778-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="ea778-104">用于 WideItem 的配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） WideControl 元素（格式） WideEntries 元素（格式）元素（格式） ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ea778-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ea778-105">语法</span><span class="sxs-lookup"><span data-stu-id="ea778-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ea778-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="ea778-106">Attributes and Elements</span></span>

<span data-ttu-id="ea778-107">以下各节介绍 `ScriptBlock` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ea778-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ea778-108">属性</span><span class="sxs-lookup"><span data-stu-id="ea778-108">Attributes</span></span>

<span data-ttu-id="ea778-109">无。</span><span class="sxs-lookup"><span data-stu-id="ea778-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ea778-110">子元素</span><span class="sxs-lookup"><span data-stu-id="ea778-110">Child Elements</span></span>

<span data-ttu-id="ea778-111">无。</span><span class="sxs-lookup"><span data-stu-id="ea778-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ea778-112">父元素</span><span class="sxs-lookup"><span data-stu-id="ea778-112">Parent Elements</span></span>

|<span data-ttu-id="ea778-113">元素</span><span class="sxs-lookup"><span data-stu-id="ea778-113">Element</span></span>|<span data-ttu-id="ea778-114">描述</span><span class="sxs-lookup"><span data-stu-id="ea778-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ea778-115">WideItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ea778-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="ea778-116">定义其值在宽视图中显示的属性或脚本块。</span><span class="sxs-lookup"><span data-stu-id="ea778-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ea778-117">文本值</span><span class="sxs-lookup"><span data-stu-id="ea778-117">Text Value</span></span>

<span data-ttu-id="ea778-118">指定显示其值的脚本。</span><span class="sxs-lookup"><span data-stu-id="ea778-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="ea778-119">备注</span><span class="sxs-lookup"><span data-stu-id="ea778-119">Remarks</span></span>

<span data-ttu-id="ea778-120">有关宽视图组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="ea778-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ea778-121">示例</span><span class="sxs-lookup"><span data-stu-id="ea778-121">Example</span></span>

<span data-ttu-id="ea778-122">此示例演示一个 `WideItem` 元素，该元素定义一个其值在视图中显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="ea778-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="ea778-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ea778-123">See Also</span></span>

[<span data-ttu-id="ea778-124">WideItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="ea778-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="ea778-125">创建宽视图</span><span class="sxs-lookup"><span data-stu-id="ea778-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ea778-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="ea778-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
