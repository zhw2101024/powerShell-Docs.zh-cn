---
title: WideControl 的 WideItem 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361396"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="6b75c-102">WideItem Element for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="6b75c-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="6b75c-103">定义要显示其值的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="6b75c-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="6b75c-104">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（格式） WideItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6b75c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6b75c-105">语法</span><span class="sxs-lookup"><span data-stu-id="6b75c-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6b75c-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="6b75c-106">Attributes and Elements</span></span>

<span data-ttu-id="6b75c-107">以下各节介绍了 `WideItem` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6b75c-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="6b75c-108">@No__t 0 元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="6b75c-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="6b75c-109">但是，必须指定 @no__t 0 或 `ScriptBlock` 元素，但不能同时指定两者。</span><span class="sxs-lookup"><span data-stu-id="6b75c-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="6b75c-110">属性</span><span class="sxs-lookup"><span data-stu-id="6b75c-110">Attributes</span></span>

<span data-ttu-id="6b75c-111">无。</span><span class="sxs-lookup"><span data-stu-id="6b75c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6b75c-112">子元素</span><span class="sxs-lookup"><span data-stu-id="6b75c-112">Child Elements</span></span>

|<span data-ttu-id="6b75c-113">元素</span><span class="sxs-lookup"><span data-stu-id="6b75c-113">Element</span></span>|<span data-ttu-id="6b75c-114">描述</span><span class="sxs-lookup"><span data-stu-id="6b75c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6b75c-115">WideControl 的 WideItem 的格式字符串元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6b75c-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="6b75c-116">可选元素。</span><span class="sxs-lookup"><span data-stu-id="6b75c-116">Optional element.</span></span><br /><br /> <span data-ttu-id="6b75c-117">指定定义属性或脚本值在视图中显示方式的格式模式。</span><span class="sxs-lookup"><span data-stu-id="6b75c-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="6b75c-118">WideItem 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="6b75c-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="6b75c-119">指定对象的属性，其值显示在宽视图中。</span><span class="sxs-lookup"><span data-stu-id="6b75c-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="6b75c-120">WideItem 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6b75c-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="6b75c-121">指定其值在宽视图中显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="6b75c-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6b75c-122">父元素</span><span class="sxs-lookup"><span data-stu-id="6b75c-122">Parent Elements</span></span>

|<span data-ttu-id="6b75c-123">元素</span><span class="sxs-lookup"><span data-stu-id="6b75c-123">Element</span></span>|<span data-ttu-id="6b75c-124">描述</span><span class="sxs-lookup"><span data-stu-id="6b75c-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6b75c-125">WideEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6b75c-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="6b75c-126">提供宽视图的定义。</span><span class="sxs-lookup"><span data-stu-id="6b75c-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6b75c-127">备注</span><span class="sxs-lookup"><span data-stu-id="6b75c-127">Remarks</span></span>

<span data-ttu-id="6b75c-128">有关宽视图组件的详细信息，请参阅[宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="6b75c-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6b75c-129">示例</span><span class="sxs-lookup"><span data-stu-id="6b75c-129">Example</span></span>

<span data-ttu-id="6b75c-130">下面的示例演示了一个 `WideEntry` 元素，该元素定义单个 @no__t 1 元素。</span><span class="sxs-lookup"><span data-stu-id="6b75c-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="6b75c-131">@No__t-0 元素定义其值在视图中显示的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="6b75c-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="6b75c-132">有关宽视图的完整示例，请参阅[宽视图（基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="6b75c-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6b75c-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6b75c-133">See Also</span></span>

[<span data-ttu-id="6b75c-134">WideControl 的 WideItem 的格式字符串元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6b75c-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="6b75c-135">WideItem 的 PropertyName 元素（Format）</span><span class="sxs-lookup"><span data-stu-id="6b75c-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="6b75c-136">WideItem 的 ScriptBlock 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6b75c-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="6b75c-137">WideEntry 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="6b75c-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="6b75c-138">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="6b75c-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
