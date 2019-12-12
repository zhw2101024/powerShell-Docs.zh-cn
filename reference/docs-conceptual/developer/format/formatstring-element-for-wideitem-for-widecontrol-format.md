---
title: WideControl 的 WideItem 的格式字符串元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bc6ea26-3ca6-4bab-8a13-29189821ba15
caps.latest.revision: 7
ms.openlocfilehash: a1dc145864a6904fd4af6c3b9187819c49e224b0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363026"
---
# <a name="formatstring-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="25228-102">FormatString Element for WideItem for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="25228-102">FormatString Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="25228-103">指定定义属性或脚本值在视图中显示方式的格式模式。</span><span class="sxs-lookup"><span data-stu-id="25228-103">Specifies a format pattern that defines how the property or script value is displayed in the view.</span></span>

<span data-ttu-id="25228-104">配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素 for WideControl （format）的元素对于 WideItem for WideControl （Format）</span><span class="sxs-lookup"><span data-stu-id="25228-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element for WideControl (Format) WideItem Element for WideControl (Format) FormatString Element for WideItem for WideControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="25228-105">语法</span><span class="sxs-lookup"><span data-stu-id="25228-105">Syntax</span></span>

```xml
<FormatString>PropertyPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="25228-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="25228-106">Attributes and Elements</span></span>

<span data-ttu-id="25228-107">以下各节介绍了 `FormatString` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="25228-107">The following sections describe the attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="25228-108">属性</span><span class="sxs-lookup"><span data-stu-id="25228-108">Attributes</span></span>

<span data-ttu-id="25228-109">无。</span><span class="sxs-lookup"><span data-stu-id="25228-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="25228-110">子元素</span><span class="sxs-lookup"><span data-stu-id="25228-110">Child Elements</span></span>

<span data-ttu-id="25228-111">无。</span><span class="sxs-lookup"><span data-stu-id="25228-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="25228-112">父元素</span><span class="sxs-lookup"><span data-stu-id="25228-112">Parent Elements</span></span>

|<span data-ttu-id="25228-113">元素</span><span class="sxs-lookup"><span data-stu-id="25228-113">Element</span></span>|<span data-ttu-id="25228-114">描述</span><span class="sxs-lookup"><span data-stu-id="25228-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="25228-115">WideControl 的 WideItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="25228-115">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="25228-116">定义其值显示在列表视图的行中的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="25228-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="25228-117">文本值</span><span class="sxs-lookup"><span data-stu-id="25228-117">Text Value</span></span>

<span data-ttu-id="25228-118">指定用于设置数据格式的模式。</span><span class="sxs-lookup"><span data-stu-id="25228-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="25228-119">例如，你可以使用此模式来[设置类型为](/dotnet/api/System.TimeSpan)system.string： {0： MMM} {0： dd} {0： HH}： {0： mm} 的任何属性的值的格式。</span><span class="sxs-lookup"><span data-stu-id="25228-119">For example, you can use this pattern to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="25228-120">备注</span><span class="sxs-lookup"><span data-stu-id="25228-120">Remarks</span></span>

<span data-ttu-id="25228-121">创建表视图、列表视图、宽视图或自定义视图时，可以使用格式字符串。</span><span class="sxs-lookup"><span data-stu-id="25228-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="25228-122">有关设置视图中显示的值的格式的详细信息，请参阅[设置显示的数据的格式](./formatting-displayed-data.md)。</span><span class="sxs-lookup"><span data-stu-id="25228-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="25228-123">有关在宽视图中使用格式字符串的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="25228-123">For more information about using format strings in wide views, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="25228-124">示例</span><span class="sxs-lookup"><span data-stu-id="25228-124">Example</span></span>

<span data-ttu-id="25228-125">下面的示例演示如何为 `StartTime` 属性的值定义格式字符串。</span><span class="sxs-lookup"><span data-stu-id="25228-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="25228-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="25228-126">See Also</span></span>

[<span data-ttu-id="25228-127">创建宽视图</span><span class="sxs-lookup"><span data-stu-id="25228-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="25228-128">WideControl 的 WideItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="25228-128">WideItem Element for WideControl (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="25228-129">编写 Windows PowerShell 格式设置和类型文件</span><span class="sxs-lookup"><span data-stu-id="25228-129">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
