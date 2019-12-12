---
title: GroupBy （格式）的标签元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3351d237-e8c2-4ec5-9500-4eceadb407c2
caps.latest.revision: 11
ms.openlocfilehash: e7158711c60d13c745bbdfab9b1b9fc7d98b34e2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365196"
---
# <a name="label-element-for-groupby-format"></a><span data-ttu-id="7a874-102">Label Element for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="7a874-102">Label Element for GroupBy (Format)</span></span>

<span data-ttu-id="7a874-103">指定在遇到新组时显示的标签。</span><span class="sxs-lookup"><span data-stu-id="7a874-103">Specifies a label that is displayed when a new group is encountered.</span></span>

<span data-ttu-id="7a874-104">GroupBy 的 "视图（格式）" 标签元素的配置元素（格式） ViewDefinitions 元素（格式） GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7a874-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) Label Element for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7a874-105">语法</span><span class="sxs-lookup"><span data-stu-id="7a874-105">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7a874-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="7a874-106">Attributes and Elements</span></span>

<span data-ttu-id="7a874-107">以下各节介绍 `Label` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7a874-107">The following sections describe the attributes, child elements, and parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7a874-108">属性</span><span class="sxs-lookup"><span data-stu-id="7a874-108">Attributes</span></span>

<span data-ttu-id="7a874-109">无。</span><span class="sxs-lookup"><span data-stu-id="7a874-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7a874-110">子元素</span><span class="sxs-lookup"><span data-stu-id="7a874-110">Child Elements</span></span>

<span data-ttu-id="7a874-111">无。</span><span class="sxs-lookup"><span data-stu-id="7a874-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7a874-112">父元素</span><span class="sxs-lookup"><span data-stu-id="7a874-112">Parent Elements</span></span>

|<span data-ttu-id="7a874-113">元素</span><span class="sxs-lookup"><span data-stu-id="7a874-113">Element</span></span>|<span data-ttu-id="7a874-114">描述</span><span class="sxs-lookup"><span data-stu-id="7a874-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7a874-115">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7a874-115">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="7a874-116">定义如何显示新的对象组。</span><span class="sxs-lookup"><span data-stu-id="7a874-116">Defines how a new group of objects is displayed.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7a874-117">文本值</span><span class="sxs-lookup"><span data-stu-id="7a874-117">Text Value</span></span>

<span data-ttu-id="7a874-118">指定每当 Windows PowerShell 遇到新的属性或脚本值时所显示的文本。</span><span class="sxs-lookup"><span data-stu-id="7a874-118">Specify the text that is displayed whenever Windows PowerShell encounters a new property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="7a874-119">备注</span><span class="sxs-lookup"><span data-stu-id="7a874-119">Remarks</span></span>

<span data-ttu-id="7a874-120">除了此元素指定的文本，Windows PowerShell 还显示启动组的新值，并在组的前面和后面添加一个空白行。</span><span class="sxs-lookup"><span data-stu-id="7a874-120">In addition to the text specified by this element, Windows PowerShell displays the new value that starts the group, and adds a blank line before and after the group.</span></span>

## <a name="example"></a><span data-ttu-id="7a874-121">示例</span><span class="sxs-lookup"><span data-stu-id="7a874-121">Example</span></span>

<span data-ttu-id="7a874-122">下面的示例显示了新组的标签。</span><span class="sxs-lookup"><span data-stu-id="7a874-122">The following example shows the label for a new group.</span></span> <span data-ttu-id="7a874-123">显示的标签将如下所示： `Service Type: NewValueofProperty`</span><span class="sxs-lookup"><span data-stu-id="7a874-123">The displayed label would look similar to this: `Service Type: NewValueofProperty`</span></span>

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

<span data-ttu-id="7a874-124">有关包括此元素的完整格式化文件的示例，请参阅[宽视图（GroupBy）](./wide-view-groupby.md)。</span><span class="sxs-lookup"><span data-stu-id="7a874-124">For an example of a complete formatting file that includes this element, see [Wide View (GroupBy)](./wide-view-groupby.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7a874-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7a874-125">See Also</span></span>

[<span data-ttu-id="7a874-126">View 的 GroupBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="7a874-126">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="7a874-127">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="7a874-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
