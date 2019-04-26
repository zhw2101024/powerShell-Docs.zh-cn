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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065083"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a><span data-ttu-id="a718a-102">Name Element for Control for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="a718a-102">Name Element for Control for Controls for View (Format)</span></span>

<span data-ttu-id="a718a-103">指定控件的名称。</span><span class="sxs-lookup"><span data-stu-id="a718a-103">Specifies the name of the control.</span></span>

<span data-ttu-id="a718a-104">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） 元素 （格式） 控件的 Controls 元素的控件视图 （格式） 名称元素控件视图 （格式）</span><span class="sxs-lookup"><span data-stu-id="a718a-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) Name Element for Control for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a718a-105">语法</span><span class="sxs-lookup"><span data-stu-id="a718a-105">Syntax</span></span>

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a718a-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="a718a-106">Attributes and Elements</span></span>

<span data-ttu-id="a718a-107">以下各节描述了特性、 子元素和父元素的`Name`元素。</span><span class="sxs-lookup"><span data-stu-id="a718a-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a718a-108">属性</span><span class="sxs-lookup"><span data-stu-id="a718a-108">Attributes</span></span>

<span data-ttu-id="a718a-109">无。</span><span class="sxs-lookup"><span data-stu-id="a718a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a718a-110">子元素</span><span class="sxs-lookup"><span data-stu-id="a718a-110">Child Elements</span></span>

<span data-ttu-id="a718a-111">无。</span><span class="sxs-lookup"><span data-stu-id="a718a-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a718a-112">父元素</span><span class="sxs-lookup"><span data-stu-id="a718a-112">Parent Elements</span></span>

|<span data-ttu-id="a718a-113">元素</span><span class="sxs-lookup"><span data-stu-id="a718a-113">Element</span></span>|<span data-ttu-id="a718a-114">说明</span><span class="sxs-lookup"><span data-stu-id="a718a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a718a-115">视图 （格式） 的控件的控件元素</span><span class="sxs-lookup"><span data-stu-id="a718a-115">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)|<span data-ttu-id="a718a-116">定义可由该视图和用于引用该控件的名称的控件。</span><span class="sxs-lookup"><span data-stu-id="a718a-116">Defines a control that can be used by the view and the name that is used to reference the control.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a718a-117">文本值</span><span class="sxs-lookup"><span data-stu-id="a718a-117">Text Value</span></span>

<span data-ttu-id="a718a-118">指定用来引用该控件的名称。</span><span class="sxs-lookup"><span data-stu-id="a718a-118">Specify the name that is used to reference the control.</span></span>

## <a name="remarks"></a><span data-ttu-id="a718a-119">备注</span><span class="sxs-lookup"><span data-stu-id="a718a-119">Remarks</span></span>

<span data-ttu-id="a718a-120">此处指定的名称可以在以下元素中，用于引用此控件。</span><span class="sxs-lookup"><span data-stu-id="a718a-120">The name specified here can be used in the following elements to reference this control.</span></span>

- <span data-ttu-id="a718a-121">在创建表、 列表、 宽或自定义控件视图时，可以通过下面的元素指定的控件：[视图 （格式） 的 GroupBy 元素](./groupby-element-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="a718a-121">When creating a table, list, wide or custom control view, the control can be specified by the following element: [GroupBy Element for View (Format)](./groupby-element-for-view-format.md)</span></span>

- <span data-ttu-id="a718a-122">当创建另一个控件，可以使用的视图时，此控件可以指定由以下元素：[ExpressionBinding CustomItem 视图 （格式） 的控件元素](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span><span class="sxs-lookup"><span data-stu-id="a718a-122">When creating another control that can be used by a view, this control can be specified by the following element: [ExpressionBinding Element for CustomItem for Controls for View (Format)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="a718a-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a718a-123">See Also</span></span>

[<span data-ttu-id="a718a-124">视图 （格式） 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="a718a-124">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="a718a-125">ExpressionBinding CustomItem 视图 （格式） 的控件元素</span><span class="sxs-lookup"><span data-stu-id="a718a-125">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="a718a-126">视图 （格式） 的控件的控件元素</span><span class="sxs-lookup"><span data-stu-id="a718a-126">Control Element for Controls for View (Format)</span></span>](./control-element-for-controls-for-view-format.md)

[<span data-ttu-id="a718a-127">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="a718a-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
