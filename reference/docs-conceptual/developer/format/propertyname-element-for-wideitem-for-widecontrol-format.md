---
title: WideControl 的 WideItem 的 PropertyName 元素（格式） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364936"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="76be9-102">PropertyName Element for WideItem for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="76be9-102">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="76be9-103">指定对象的属性，其值显示在宽视图中。</span><span class="sxs-lookup"><span data-stu-id="76be9-103">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="76be9-104">用于 WideItem 的配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（格式） WideItem 元素（格式） PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="76be9-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="76be9-105">语法</span><span class="sxs-lookup"><span data-stu-id="76be9-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="76be9-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="76be9-106">Attributes and Elements</span></span>

<span data-ttu-id="76be9-107">以下各节介绍 `PropertyName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="76be9-107">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="76be9-108">属性</span><span class="sxs-lookup"><span data-stu-id="76be9-108">Attributes</span></span>

<span data-ttu-id="76be9-109">无。</span><span class="sxs-lookup"><span data-stu-id="76be9-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="76be9-110">子元素</span><span class="sxs-lookup"><span data-stu-id="76be9-110">Child Elements</span></span>

<span data-ttu-id="76be9-111">无。</span><span class="sxs-lookup"><span data-stu-id="76be9-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="76be9-112">父元素</span><span class="sxs-lookup"><span data-stu-id="76be9-112">Parent Elements</span></span>

|<span data-ttu-id="76be9-113">元素</span><span class="sxs-lookup"><span data-stu-id="76be9-113">Element</span></span>|<span data-ttu-id="76be9-114">描述</span><span class="sxs-lookup"><span data-stu-id="76be9-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="76be9-115">WideItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="76be9-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="76be9-116">定义其值在宽视图中显示的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="76be9-116">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="76be9-117">文本值</span><span class="sxs-lookup"><span data-stu-id="76be9-117">Text Value</span></span>

<span data-ttu-id="76be9-118">指定显示其值的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="76be9-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="76be9-119">备注</span><span class="sxs-lookup"><span data-stu-id="76be9-119">Remarks</span></span>

<span data-ttu-id="76be9-120">有关宽视图组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="76be9-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="76be9-121">示例</span><span class="sxs-lookup"><span data-stu-id="76be9-121">Example</span></span>

<span data-ttu-id="76be9-122">此示例显示了一个宽视图，其中[显示了 ProcessName 对象的](/dotnet/api/System.Diagnostics.Process)"" 属性的值。</span><span class="sxs-lookup"><span data-stu-id="76be9-122">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="76be9-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="76be9-123">See Also</span></span>

[<span data-ttu-id="76be9-124">WideItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="76be9-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="76be9-125">创建宽视图</span><span class="sxs-lookup"><span data-stu-id="76be9-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="76be9-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="76be9-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
