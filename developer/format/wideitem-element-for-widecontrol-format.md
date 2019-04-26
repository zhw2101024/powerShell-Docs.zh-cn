---
title: WideControl （格式） 的 WideItem 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17352fc4-ba83-4f04-86bc-f591765d85a8
caps.latest.revision: 18
ms.openlocfilehash: fa9eda3ea1028c27dbfb3eb04747af3b817c1a81
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083631"
---
# <a name="wideitem-element-for-widecontrol-format"></a><span data-ttu-id="52cca-102">WideItem Element for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="52cca-102">WideItem Element for WideControl (Format)</span></span>

<span data-ttu-id="52cca-103">定义属性或其值显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="52cca-103">Defines the property or script whose value is displayed.</span></span>

<span data-ttu-id="52cca-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） WideControl 元素 （格式） WideEntries 元素 （格式） WideEntry 元素 （格式） WideItem 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="52cca-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="52cca-105">语法</span><span class="sxs-lookup"><span data-stu-id="52cca-105">Syntax</span></span>

```xml
<WideItem>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <FormatString>FormatPattern</FormatString>
</WideItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="52cca-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="52cca-106">Attributes and Elements</span></span>

<span data-ttu-id="52cca-107">以下各节描述了特性、 子元素和父元素的`WideItem`元素。</span><span class="sxs-lookup"><span data-stu-id="52cca-107">The following sections describe the attributes, child elements, and the parent element of the `WideItem` element.</span></span> <span data-ttu-id="52cca-108">`FormatString`元素是可选的。</span><span class="sxs-lookup"><span data-stu-id="52cca-108">The `FormatString` element is optional.</span></span> <span data-ttu-id="52cca-109">但是，必须指定`PropertyName`或`ScriptBlock`元素，但是您不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="52cca-109">However, you must specify a `PropertyName` or `ScriptBlock` element, but you cannot specify both.</span></span>

### <a name="attributes"></a><span data-ttu-id="52cca-110">属性</span><span class="sxs-lookup"><span data-stu-id="52cca-110">Attributes</span></span>

<span data-ttu-id="52cca-111">无。</span><span class="sxs-lookup"><span data-stu-id="52cca-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="52cca-112">子元素</span><span class="sxs-lookup"><span data-stu-id="52cca-112">Child Elements</span></span>

|<span data-ttu-id="52cca-113">元素</span><span class="sxs-lookup"><span data-stu-id="52cca-113">Element</span></span>|<span data-ttu-id="52cca-114">说明</span><span class="sxs-lookup"><span data-stu-id="52cca-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="52cca-115">WideControl （格式） 的 WideItem 的 FormatString 元素</span><span class="sxs-lookup"><span data-stu-id="52cca-115">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="52cca-116">可选元素。</span><span class="sxs-lookup"><span data-stu-id="52cca-116">Optional element.</span></span><br /><br /> <span data-ttu-id="52cca-117">指定格式模式，它定义如何在视图中显示的属性或脚本的值。</span><span class="sxs-lookup"><span data-stu-id="52cca-117">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>|
|[<span data-ttu-id="52cca-118">WideItem （格式） 的属性名称元素</span><span class="sxs-lookup"><span data-stu-id="52cca-118">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="52cca-119">指定其值宽视图中显示的对象的属性。</span><span class="sxs-lookup"><span data-stu-id="52cca-119">Specifies the property of the object whose value is displayed in the wide view.</span></span>|
|[<span data-ttu-id="52cca-120">WideItem （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="52cca-120">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)|<span data-ttu-id="52cca-121">指定其值宽视图中显示的脚本。</span><span class="sxs-lookup"><span data-stu-id="52cca-121">Specifies the script whose value is displayed in the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="52cca-122">父元素</span><span class="sxs-lookup"><span data-stu-id="52cca-122">Parent Elements</span></span>

|<span data-ttu-id="52cca-123">元素</span><span class="sxs-lookup"><span data-stu-id="52cca-123">Element</span></span>|<span data-ttu-id="52cca-124">说明</span><span class="sxs-lookup"><span data-stu-id="52cca-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="52cca-125">WideEntry 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="52cca-125">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="52cca-126">提供了宽的视图的定义。</span><span class="sxs-lookup"><span data-stu-id="52cca-126">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="52cca-127">备注</span><span class="sxs-lookup"><span data-stu-id="52cca-127">Remarks</span></span>

<span data-ttu-id="52cca-128">有关较宽的视图的组件的详细信息，请参阅[宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="52cca-128">For more information about the components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="52cca-129">示例</span><span class="sxs-lookup"><span data-stu-id="52cca-129">Example</span></span>

<span data-ttu-id="52cca-130">下面的示例演示`WideEntry`元素定义单个`WideItem`元素。</span><span class="sxs-lookup"><span data-stu-id="52cca-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="52cca-131">`WideItem`元素定义的属性或其值显示在视图中的脚本。</span><span class="sxs-lookup"><span data-stu-id="52cca-131">The `WideItem` element defines the property or script whose value is displayed in the view.</span></span>

```xml
<WideEntry>
  <WideItem>
    <PropertyName>ProcessName</PropertyName>
  </WideItem>
</WideEntry>
```

<span data-ttu-id="52cca-132">有关较宽的视图的完整示例，请参阅[宽的视图 （基本）](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="52cca-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="52cca-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="52cca-133">See Also</span></span>

[<span data-ttu-id="52cca-134">WideControl （格式） 的 WideItem 的 FormatString 元素</span><span class="sxs-lookup"><span data-stu-id="52cca-134">FormatString Element for WideItem for WideControl (Format)</span></span>](./formatstring-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="52cca-135">WideItem （格式） 的属性名称元素</span><span class="sxs-lookup"><span data-stu-id="52cca-135">PropertyName Element for WideItem (Format)</span></span>](./propertyname-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="52cca-136">WideItem （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="52cca-136">ScriptBlock Element for WideItem (Format)</span></span>](./scriptblock-element-for-wideitem-for-widecontrol-format.md)

[<span data-ttu-id="52cca-137">WideEntry 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="52cca-137">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="52cca-138">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="52cca-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
