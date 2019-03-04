---
title: DisplayError 元素 （格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 431e5d8407b9f689a5224b329d8c7b52802e19e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854913"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="c9cd8-102">DisplayError Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c9cd8-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="c9cd8-103">指定当出错时显示一段数据显示 #ERR 的字符串。</span><span class="sxs-lookup"><span data-stu-id="c9cd8-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="c9cd8-104">配置元素 （格式） DefaultSettings 元素 （格式） DisplayError 元素 (Frmat)</span><span class="sxs-lookup"><span data-stu-id="c9cd8-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Frmat)</span></span>

## <a name="syntax"></a><span data-ttu-id="c9cd8-105">语法</span><span class="sxs-lookup"><span data-stu-id="c9cd8-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c9cd8-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="c9cd8-106">Attributes and Elements</span></span>

<span data-ttu-id="c9cd8-107">以下各节描述了特性、 子元素和父元素的`DisplayError`元素。</span><span class="sxs-lookup"><span data-stu-id="c9cd8-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c9cd8-108">特性</span><span class="sxs-lookup"><span data-stu-id="c9cd8-108">Attributes</span></span>

<span data-ttu-id="c9cd8-109">无。</span><span class="sxs-lookup"><span data-stu-id="c9cd8-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c9cd8-110">子元素</span><span class="sxs-lookup"><span data-stu-id="c9cd8-110">Child Elements</span></span>

<span data-ttu-id="c9cd8-111">无。</span><span class="sxs-lookup"><span data-stu-id="c9cd8-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c9cd8-112">父元素</span><span class="sxs-lookup"><span data-stu-id="c9cd8-112">Parent Elements</span></span>

|<span data-ttu-id="c9cd8-113">元素</span><span class="sxs-lookup"><span data-stu-id="c9cd8-113">Element</span></span>|<span data-ttu-id="c9cd8-114">描述</span><span class="sxs-lookup"><span data-stu-id="c9cd8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c9cd8-115">DefaultSettings 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="c9cd8-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="c9cd8-116">定义应用于的格式设置文件的所有视图的常见设置。</span><span class="sxs-lookup"><span data-stu-id="c9cd8-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c9cd8-117">备注</span><span class="sxs-lookup"><span data-stu-id="c9cd8-117">Remarks</span></span>

<span data-ttu-id="c9cd8-118">默认情况下，当出错时尝试显示一段数据，数据的位置是保留为空。</span><span class="sxs-lookup"><span data-stu-id="c9cd8-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="c9cd8-119">如果此元素设置为 true，#ERR 字符串将会显示。</span><span class="sxs-lookup"><span data-stu-id="c9cd8-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9cd8-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c9cd8-120">See Also</span></span>

[<span data-ttu-id="c9cd8-121">DefaultSettings 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="c9cd8-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="c9cd8-122">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="c9cd8-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
