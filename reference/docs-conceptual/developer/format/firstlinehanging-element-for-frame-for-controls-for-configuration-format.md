---
title: 用于配置的控件的框架的 FirstLineHanging 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 679c8bcb-b49d-4bb4-91f5-ea1af6c217e3
caps.latest.revision: 8
ms.openlocfilehash: 4553f95e48a2b1440c00b4951bea56376b00628a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363166"
---
# <a name="firstlinehanging-element-for-frame-for-controls-for-configuration-format"></a><span data-ttu-id="382a3-102">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="382a3-102">FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

<span data-ttu-id="382a3-103">指定将第一行数据向左移动的字符数。</span><span class="sxs-lookup"><span data-stu-id="382a3-103">Specifies how many characters the first line of data is shifted to the left.</span></span> <span data-ttu-id="382a3-104">此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。</span><span class="sxs-lookup"><span data-stu-id="382a3-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="382a3-105">Configuration 元素（格式）控制配置（format） CustomControl 元素的控件的配置（Format）控件元素的元素，以控制 CustomControl for configuration （Format） CustomEntries 元素的配置（Format）用于 CustomControl 的 CustomEntry 元素，用于配置（Format） CustomItem 元素 for CustomEntry 的的配置框架元素的控件用于配置的控件（格式）</span><span class="sxs-lookup"><span data-stu-id="382a3-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration Frame Element for CustomItem for Controls for Configuration (Format) FirstLineHanging Element for Frame for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="382a3-106">语法</span><span class="sxs-lookup"><span data-stu-id="382a3-106">Syntax</span></span>

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="382a3-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="382a3-107">Attributes and Elements</span></span>

<span data-ttu-id="382a3-108">以下各节介绍 `FirstLineHanging` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="382a3-108">The following sections describe attributes, child elements, and parent element of the `FirstLineHanging` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="382a3-109">属性</span><span class="sxs-lookup"><span data-stu-id="382a3-109">Attributes</span></span>

<span data-ttu-id="382a3-110">无。</span><span class="sxs-lookup"><span data-stu-id="382a3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="382a3-111">子元素</span><span class="sxs-lookup"><span data-stu-id="382a3-111">Child Elements</span></span>

<span data-ttu-id="382a3-112">无。</span><span class="sxs-lookup"><span data-stu-id="382a3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="382a3-113">父元素</span><span class="sxs-lookup"><span data-stu-id="382a3-113">Parent Elements</span></span>

|<span data-ttu-id="382a3-114">元素</span><span class="sxs-lookup"><span data-stu-id="382a3-114">Element</span></span>|<span data-ttu-id="382a3-115">描述</span><span class="sxs-lookup"><span data-stu-id="382a3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="382a3-116">用于配置的控件的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="382a3-116">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="382a3-117">定义数据的显示方式，例如，将数据向左或向右移动。</span><span class="sxs-lookup"><span data-stu-id="382a3-117">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|

## <a name="text-value"></a><span data-ttu-id="382a3-118">文本值</span><span class="sxs-lookup"><span data-stu-id="382a3-118">Text Value</span></span>

<span data-ttu-id="382a3-119">指定要将数据的第一行移动到的字符数。</span><span class="sxs-lookup"><span data-stu-id="382a3-119">Specify the number of characters that you want to shift the first line of the data.</span></span>

## <a name="remarks"></a><span data-ttu-id="382a3-120">备注</span><span class="sxs-lookup"><span data-stu-id="382a3-120">Remarks</span></span>

<span data-ttu-id="382a3-121">如果指定此元素，则不能指定 `FirstLineIndent` 元素。</span><span class="sxs-lookup"><span data-stu-id="382a3-121">If this element is specified, you cannot specify the `FirstLineIndent` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="382a3-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="382a3-122">See Also</span></span>

[<span data-ttu-id="382a3-123">用于配置的控件的 CustomItem 的框架元素（格式）</span><span class="sxs-lookup"><span data-stu-id="382a3-123">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="382a3-124">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="382a3-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
