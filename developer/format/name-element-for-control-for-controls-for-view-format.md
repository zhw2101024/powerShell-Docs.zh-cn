---
title: 命名元素的控件的控件视图 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862383"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="9f764-102">Name Element for Control for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="9f764-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="9f764-103">指定控件的名称。</span><span class="sxs-lookup"><span data-stu-id="9f764-103">Specifies the name of the control.</span></span>

<span data-ttu-id="9f764-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 元素 （格式） 控件的 Controls 元素的控件视图 （格式） 名称元素控件视图 （格式）</span><span class="sxs-lookup"><span data-stu-id="9f764-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9f764-105">语法</span><span class="sxs-lookup"><span data-stu-id="9f764-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9f764-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="9f764-106">Attributes and Elements</span></span>

<span data-ttu-id="9f764-107">以下各节描述了特性、 子元素和父元素的`Name`元素。</span><span class="sxs-lookup"><span data-stu-id="9f764-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9f764-108">特性</span><span class="sxs-lookup"><span data-stu-id="9f764-108">Attributes</span></span>

<span data-ttu-id="9f764-109">无。</span><span class="sxs-lookup"><span data-stu-id="9f764-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9f764-110">子元素</span><span class="sxs-lookup"><span data-stu-id="9f764-110">Child Elements</span></span>

<span data-ttu-id="9f764-111">无。</span><span class="sxs-lookup"><span data-stu-id="9f764-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9f764-112">父元素</span><span class="sxs-lookup"><span data-stu-id="9f764-112">Parent Elements</span></span>

|<span data-ttu-id="9f764-113">元素</span><span class="sxs-lookup"><span data-stu-id="9f764-113">Element</span></span>|<span data-ttu-id="9f764-114">描述</span><span class="sxs-lookup"><span data-stu-id="9f764-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9f764-115">视图 （格式） 的控件的控件元素</span><span class="sxs-lookup"><span data-stu-id="9f764-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="9f764-116">定义可由该视图和用于引用该控件的名称的控件。</span><span class="sxs-lookup"><span data-stu-id="9f764-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="9f764-117">文本值</span><span class="sxs-lookup"><span data-stu-id="9f764-117">Text Value</span></span>

<span data-ttu-id="9f764-118">指定用来引用该控件的名称。</span><span class="sxs-lookup"><span data-stu-id="9f764-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="9f764-119">备注</span><span class="sxs-lookup"><span data-stu-id="9f764-119">Remarks</span></span>

<span data-ttu-id="9f764-120">此处指定的名称可以在以下元素中，用于引用此控件。</span><span class="sxs-lookup"><span data-stu-id="9f764-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="9f764-121">在创建表、 列表、 宽或自定义控件视图时，可以通过下面的元素指定的控件：[视图 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="9f764-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="9f764-122">当创建另一个控件，可以使用的视图时，此控件可以指定由以下元素：[ExpressionBinding CustomItem 视图 （格式） 的控件元素](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="9f764-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="9f764-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9f764-123">See Also</span></span>

[<span data-ttu-id="9f764-124">视图 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="9f764-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="9f764-125">ExpressionBinding CustomItem 视图 （格式） 的控件元素</span><span class="sxs-lookup"><span data-stu-id="9f764-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="9f764-126">视图 （格式） 的控件的控件元素</span><span class="sxs-lookup"><span data-stu-id="9f764-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="9f764-127">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="9f764-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
