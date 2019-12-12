---
title: WideControl 的 AutoSize 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: def37479-7b6e-40cf-bc81-0f7cbc651b31
caps.latest.revision: 11
ms.openlocfilehash: 6dbaef5886a0600bd9fe96dbc8d21f00a674dfcf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369046"
---
# <a name="autosize-element-for-widecontrol-format"></a><span data-ttu-id="fd89b-102">AutoSize Element for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="fd89b-102">AutoSize Element for WideControl (Format)</span></span>

<span data-ttu-id="fd89b-103">指定是否根据数据大小调整列大小和列数。</span><span class="sxs-lookup"><span data-stu-id="fd89b-103">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>

<span data-ttu-id="fd89b-104">WideControl （Format）的 Configuration 元素（格式） ViewDefinitions 元素（格式） WideControl 元素（格式） Autosize 元素</span><span class="sxs-lookup"><span data-stu-id="fd89b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) Autosize Element for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fd89b-105">语法</span><span class="sxs-lookup"><span data-stu-id="fd89b-105">Syntax</span></span>

```xml
<AutoSize/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fd89b-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="fd89b-106">Attributes and Elements</span></span>

<span data-ttu-id="fd89b-107">以下各节介绍了 `AutoSize` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fd89b-107">The following sections describe attributes, child elements, and the parent element of the `AutoSize` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fd89b-108">属性</span><span class="sxs-lookup"><span data-stu-id="fd89b-108">Attributes</span></span>

<span data-ttu-id="fd89b-109">无。</span><span class="sxs-lookup"><span data-stu-id="fd89b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fd89b-110">子元素</span><span class="sxs-lookup"><span data-stu-id="fd89b-110">Child Elements</span></span>

<span data-ttu-id="fd89b-111">无</span><span class="sxs-lookup"><span data-stu-id="fd89b-111">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fd89b-112">父元素</span><span class="sxs-lookup"><span data-stu-id="fd89b-112">Parent Elements</span></span>

|<span data-ttu-id="fd89b-113">元素</span><span class="sxs-lookup"><span data-stu-id="fd89b-113">Element</span></span>|<span data-ttu-id="fd89b-114">描述</span><span class="sxs-lookup"><span data-stu-id="fd89b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fd89b-115">WideControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fd89b-115">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="fd89b-116">定义视图的宽（单值）列表格式。</span><span class="sxs-lookup"><span data-stu-id="fd89b-116">Defines a wide (single value) list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fd89b-117">备注</span><span class="sxs-lookup"><span data-stu-id="fd89b-117">Remarks</span></span>

<span data-ttu-id="fd89b-118">定义宽视图时，可以添加 `AutoSize` 元素或[ColumnNumber](./columnnumber-element-for-widecontrol-format.md)元素，但不能同时添加这两个元素。</span><span class="sxs-lookup"><span data-stu-id="fd89b-118">When defining a wide view, you can add the `AutoSize` element or the [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) element, but you cannot add both.</span></span>

<span data-ttu-id="fd89b-119">有关宽视图组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="fd89b-119">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="fd89b-120">有关宽视图的示例，请参阅[宽视图（基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="fd89b-120">For an example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fd89b-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fd89b-121">See Also</span></span>

[<span data-ttu-id="fd89b-122">WideControl 的 ColumnNumber 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fd89b-122">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="fd89b-123">创建宽视图</span><span class="sxs-lookup"><span data-stu-id="fd89b-123">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="fd89b-124">WideControl 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="fd89b-124">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="fd89b-125">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="fd89b-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
