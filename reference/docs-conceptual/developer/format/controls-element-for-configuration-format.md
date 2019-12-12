---
title: 用于配置的 Controls 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368996"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="a6050-102">Controls Element for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="a6050-102">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="a6050-103">定义可供格式设置文件的所有视图使用的公共控件。</span><span class="sxs-lookup"><span data-stu-id="a6050-103">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="a6050-104">配置元素（格式）控件配置的元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6050-104">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a6050-105">语法</span><span class="sxs-lookup"><span data-stu-id="a6050-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a6050-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="a6050-106">Attributes and Elements</span></span>

<span data-ttu-id="a6050-107">以下各节介绍了 `Controls` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a6050-107">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a6050-108">属性</span><span class="sxs-lookup"><span data-stu-id="a6050-108">Attributes</span></span>

<span data-ttu-id="a6050-109">无。</span><span class="sxs-lookup"><span data-stu-id="a6050-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a6050-110">子元素</span><span class="sxs-lookup"><span data-stu-id="a6050-110">Child Elements</span></span>

|<span data-ttu-id="a6050-111">元素</span><span class="sxs-lookup"><span data-stu-id="a6050-111">Element</span></span>|<span data-ttu-id="a6050-112">描述</span><span class="sxs-lookup"><span data-stu-id="a6050-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a6050-113">用于配置控件的控件元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6050-113">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="a6050-114">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="a6050-114">Required element.</span></span><br /><br /> <span data-ttu-id="a6050-115">定义可供格式设置文件的所有视图使用的公共控件。</span><span class="sxs-lookup"><span data-stu-id="a6050-115">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a6050-116">父元素</span><span class="sxs-lookup"><span data-stu-id="a6050-116">Parent Elements</span></span>

|<span data-ttu-id="a6050-117">元素</span><span class="sxs-lookup"><span data-stu-id="a6050-117">Element</span></span>|<span data-ttu-id="a6050-118">描述</span><span class="sxs-lookup"><span data-stu-id="a6050-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a6050-119">配置元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6050-119">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="a6050-120">表示格式设置文件的顶级元素。</span><span class="sxs-lookup"><span data-stu-id="a6050-120">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a6050-121">备注</span><span class="sxs-lookup"><span data-stu-id="a6050-121">Remarks</span></span>

<span data-ttu-id="a6050-122">您可以创建任意数量的公共控件。</span><span class="sxs-lookup"><span data-stu-id="a6050-122">You can create any number of common controls.</span></span> <span data-ttu-id="a6050-123">对于每个控件，您必须指定用于引用控件和控件组件的名称。</span><span class="sxs-lookup"><span data-stu-id="a6050-123">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="a6050-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a6050-124">See Also</span></span>

[<span data-ttu-id="a6050-125">配置元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6050-125">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="a6050-126">用于配置控件的控件元素（格式）</span><span class="sxs-lookup"><span data-stu-id="a6050-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="a6050-127">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="a6050-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
