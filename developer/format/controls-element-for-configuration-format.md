---
title: 配置 （格式） 的 controls 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861173"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="8b221-102">Controls Element for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="8b221-102">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="8b221-103">定义可由格式设置文件的所有视图的公共控件。</span><span class="sxs-lookup"><span data-stu-id="8b221-103">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="8b221-104">配置 （格式） 的配置元素 （格式） 的 Controls 元素</span><span class="sxs-lookup"><span data-stu-id="8b221-104">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8b221-105">语法</span><span class="sxs-lookup"><span data-stu-id="8b221-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8b221-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="8b221-106">Attributes and Elements</span></span>

<span data-ttu-id="8b221-107">以下各节描述了特性、 子元素和父元素的`Controls`元素。</span><span class="sxs-lookup"><span data-stu-id="8b221-107">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8b221-108">特性</span><span class="sxs-lookup"><span data-stu-id="8b221-108">Attributes</span></span>

<span data-ttu-id="8b221-109">无。</span><span class="sxs-lookup"><span data-stu-id="8b221-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8b221-110">子元素</span><span class="sxs-lookup"><span data-stu-id="8b221-110">Child Elements</span></span>

|<span data-ttu-id="8b221-111">元素</span><span class="sxs-lookup"><span data-stu-id="8b221-111">Element</span></span>|<span data-ttu-id="8b221-112">描述</span><span class="sxs-lookup"><span data-stu-id="8b221-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8b221-113">配置 （格式） 的控件的控件元素</span><span class="sxs-lookup"><span data-stu-id="8b221-113">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="8b221-114">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="8b221-114">Required element.</span></span><br /><br /> <span data-ttu-id="8b221-115">定义可由格式设置文件的所有视图的公共控件。</span><span class="sxs-lookup"><span data-stu-id="8b221-115">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8b221-116">父元素</span><span class="sxs-lookup"><span data-stu-id="8b221-116">Parent Elements</span></span>

|<span data-ttu-id="8b221-117">元素</span><span class="sxs-lookup"><span data-stu-id="8b221-117">Element</span></span>|<span data-ttu-id="8b221-118">描述</span><span class="sxs-lookup"><span data-stu-id="8b221-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8b221-119">配置元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="8b221-119">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="8b221-120">表示格式设置文件的顶级元素。</span><span class="sxs-lookup"><span data-stu-id="8b221-120">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8b221-121">备注</span><span class="sxs-lookup"><span data-stu-id="8b221-121">Remarks</span></span>

<span data-ttu-id="8b221-122">可以创建任意数量的公共控件。</span><span class="sxs-lookup"><span data-stu-id="8b221-122">You can create any number of common controls.</span></span> <span data-ttu-id="8b221-123">对于每个控件，必须指定用来引用控件和控件的组件的名称。</span><span class="sxs-lookup"><span data-stu-id="8b221-123">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b221-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8b221-124">See Also</span></span>

[<span data-ttu-id="8b221-125">配置元素 （格式）</span><span class="sxs-lookup"><span data-stu-id="8b221-125">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="8b221-126">配置 （格式） 的控件的控件元素</span><span class="sxs-lookup"><span data-stu-id="8b221-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="8b221-127">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="8b221-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
