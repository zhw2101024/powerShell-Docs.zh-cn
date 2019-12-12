---
title: 用于控件的控件（格式）的 CustomControl 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9d92a9e-c680-46ca-962e-e82452726953
caps.latest.revision: 10
ms.openlocfilehash: 1d72ce5b18e89bd81c7f81b27f4b8c60bed99764
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368966"
---
# <a name="customcontrol-element-for-control-for-controls-for-configuration-format"></a><span data-ttu-id="4546c-102">CustomControl Element for Control for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="4546c-102">CustomControl Element for Control for Controls for Configuration (Format)</span></span>

<span data-ttu-id="4546c-103">定义控件。</span><span class="sxs-lookup"><span data-stu-id="4546c-103">Defines a control.</span></span> <span data-ttu-id="4546c-104">此元素在定义可供格式设置文件中的所有视图使用的公共控件时使用。</span><span class="sxs-lookup"><span data-stu-id="4546c-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="4546c-105">Configuration 元素（Format）控制配置（format）控件元素的元素，用于配置（format） CustomControl 元素的控件以实现配置（格式）</span><span class="sxs-lookup"><span data-stu-id="4546c-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4546c-106">语法</span><span class="sxs-lookup"><span data-stu-id="4546c-106">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4546c-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="4546c-107">Attributes and Elements</span></span>

<span data-ttu-id="4546c-108">以下各节介绍了 `CustomControl` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4546c-108">The following sections describe the attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="4546c-109">此元素必须至少有一个子元素。</span><span class="sxs-lookup"><span data-stu-id="4546c-109">This element must have at least one child element.</span></span> <span data-ttu-id="4546c-110">对于可指定的子元素数没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="4546c-110">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="4546c-111">属性</span><span class="sxs-lookup"><span data-stu-id="4546c-111">Attributes</span></span>

<span data-ttu-id="4546c-112">无。</span><span class="sxs-lookup"><span data-stu-id="4546c-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4546c-113">子元素</span><span class="sxs-lookup"><span data-stu-id="4546c-113">Child Elements</span></span>

|<span data-ttu-id="4546c-114">元素</span><span class="sxs-lookup"><span data-stu-id="4546c-114">Element</span></span>|<span data-ttu-id="4546c-115">描述</span><span class="sxs-lookup"><span data-stu-id="4546c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4546c-116">用于配置的 CustomControl 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4546c-116">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="4546c-117">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="4546c-117">Required element.</span></span><br /><br /> <span data-ttu-id="4546c-118">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="4546c-118">Provides the definitions of a control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4546c-119">父元素</span><span class="sxs-lookup"><span data-stu-id="4546c-119">Parent Elements</span></span>

|<span data-ttu-id="4546c-120">元素</span><span class="sxs-lookup"><span data-stu-id="4546c-120">Element</span></span>|<span data-ttu-id="4546c-121">描述</span><span class="sxs-lookup"><span data-stu-id="4546c-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4546c-122">用于配置控件的控件元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4546c-122">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="4546c-123">定义一个公共控件，该控件可供格式设置文件的所有视图和用于引用控件的名称使用。</span><span class="sxs-lookup"><span data-stu-id="4546c-123">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4546c-124">备注</span><span class="sxs-lookup"><span data-stu-id="4546c-124">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="4546c-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4546c-125">See Also</span></span>

[<span data-ttu-id="4546c-126">用于配置控件的控件元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4546c-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="4546c-127">用于配置的 CustomControl 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="4546c-127">CustomEntries Element for CustomControl for Configuration (Format)</span></span>](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="4546c-128">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="4546c-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
