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
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066254"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="f41f9-102">DisplayError Element (Format)</span><span class="sxs-lookup"><span data-stu-id="f41f9-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="f41f9-103">指定当出错时显示一段数据显示 #ERR 的字符串。</span><span class="sxs-lookup"><span data-stu-id="f41f9-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="f41f9-104">配置元素 （格式） DefaultSettings 元素 （格式） DisplayError 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="f41f9-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f41f9-105">语法</span><span class="sxs-lookup"><span data-stu-id="f41f9-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f41f9-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f41f9-106">Attributes and Elements</span></span>

<span data-ttu-id="f41f9-107">以下各节描述了特性、 子元素和父元素的`DisplayError`元素。</span><span class="sxs-lookup"><span data-stu-id="f41f9-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f41f9-108">属性</span><span class="sxs-lookup"><span data-stu-id="f41f9-108">Attributes</span></span>

<span data-ttu-id="f41f9-109">无。</span><span class="sxs-lookup"><span data-stu-id="f41f9-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f41f9-110">子元素</span><span class="sxs-lookup"><span data-stu-id="f41f9-110">Child Elements</span></span>

<span data-ttu-id="f41f9-111">无。</span><span class="sxs-lookup"><span data-stu-id="f41f9-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f41f9-112">父元素</span><span class="sxs-lookup"><span data-stu-id="f41f9-112">Parent Elements</span></span>

|<span data-ttu-id="f41f9-113">元素</span><span class="sxs-lookup"><span data-stu-id="f41f9-113">Element</span></span>|<span data-ttu-id="f41f9-114">说明</span><span class="sxs-lookup"><span data-stu-id="f41f9-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f41f9-115">DefaultSettings 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="f41f9-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="f41f9-116">定义应用于的格式设置文件的所有视图的常见设置。</span><span class="sxs-lookup"><span data-stu-id="f41f9-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f41f9-117">备注</span><span class="sxs-lookup"><span data-stu-id="f41f9-117">Remarks</span></span>

<span data-ttu-id="f41f9-118">默认情况下，当出错时尝试显示一段数据，数据的位置是保留为空。</span><span class="sxs-lookup"><span data-stu-id="f41f9-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="f41f9-119">如果此元素设置为 true，#ERR 字符串将会显示。</span><span class="sxs-lookup"><span data-stu-id="f41f9-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="f41f9-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f41f9-120">See Also</span></span>

[<span data-ttu-id="f41f9-121">DefaultSettings 元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="f41f9-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="f41f9-122">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="f41f9-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
