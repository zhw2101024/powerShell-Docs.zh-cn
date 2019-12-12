---
title: DisplayError 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363986"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="9d74a-102">DisplayError Element (Format)</span><span class="sxs-lookup"><span data-stu-id="9d74a-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="9d74a-103">指定在显示一段数据时出现错误时显示字符串 #ERR。</span><span class="sxs-lookup"><span data-stu-id="9d74a-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="9d74a-104">配置元素（格式） DefaultSettings 元素（format） DisplayError 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9d74a-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="9d74a-105">语法</span><span class="sxs-lookup"><span data-stu-id="9d74a-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9d74a-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="9d74a-106">Attributes and Elements</span></span>

<span data-ttu-id="9d74a-107">以下各节介绍了 `DisplayError` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9d74a-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="9d74a-108">属性</span><span class="sxs-lookup"><span data-stu-id="9d74a-108">Attributes</span></span>

<span data-ttu-id="9d74a-109">无。</span><span class="sxs-lookup"><span data-stu-id="9d74a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="9d74a-110">子元素</span><span class="sxs-lookup"><span data-stu-id="9d74a-110">Child Elements</span></span>

<span data-ttu-id="9d74a-111">无。</span><span class="sxs-lookup"><span data-stu-id="9d74a-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9d74a-112">父元素</span><span class="sxs-lookup"><span data-stu-id="9d74a-112">Parent Elements</span></span>

|<span data-ttu-id="9d74a-113">元素</span><span class="sxs-lookup"><span data-stu-id="9d74a-113">Element</span></span>|<span data-ttu-id="9d74a-114">描述</span><span class="sxs-lookup"><span data-stu-id="9d74a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9d74a-115">DefaultSettings 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9d74a-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="9d74a-116">定义适用于格式设置文件的所有视图的常见设置。</span><span class="sxs-lookup"><span data-stu-id="9d74a-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9d74a-117">备注</span><span class="sxs-lookup"><span data-stu-id="9d74a-117">Remarks</span></span>

<span data-ttu-id="9d74a-118">默认情况下，在尝试显示一段数据的过程中出现错误时，数据的位置将保留为空。</span><span class="sxs-lookup"><span data-stu-id="9d74a-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="9d74a-119">如果此元素设置为 true，则将显示 #ERR 字符串。</span><span class="sxs-lookup"><span data-stu-id="9d74a-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d74a-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9d74a-120">See Also</span></span>

[<span data-ttu-id="9d74a-121">DefaultSettings 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="9d74a-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="9d74a-122">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="9d74a-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
