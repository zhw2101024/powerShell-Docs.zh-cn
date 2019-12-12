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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364936"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="526d0-102">PropertyName Element for WideItem for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="526d0-102">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="526d0-103">指定对象的属性，其值显示在宽视图中。</span><span class="sxs-lookup"><span data-stu-id="526d0-103">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="526d0-104">用于 WideItem 的配置元素（格式） ViewDefinitions 元素（格式）查看元素（格式） WideControl 元素（格式） WideEntries 元素（格式） WideEntry 元素（格式） WideItem 元素（格式） PropertyName 元素</span><span class="sxs-lookup"><span data-stu-id="526d0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="526d0-105">语法</span><span class="sxs-lookup"><span data-stu-id="526d0-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="526d0-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="526d0-106">Attributes and Elements</span></span>

<span data-ttu-id="526d0-107">以下各节介绍 `PropertyName` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="526d0-107">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="526d0-108">属性</span><span class="sxs-lookup"><span data-stu-id="526d0-108">Attributes</span></span>

<span data-ttu-id="526d0-109">无。</span><span class="sxs-lookup"><span data-stu-id="526d0-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="526d0-110">子元素</span><span class="sxs-lookup"><span data-stu-id="526d0-110">Child Elements</span></span>

<span data-ttu-id="526d0-111">无。</span><span class="sxs-lookup"><span data-stu-id="526d0-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="526d0-112">父元素</span><span class="sxs-lookup"><span data-stu-id="526d0-112">Parent Elements</span></span>

|<span data-ttu-id="526d0-113">元素</span><span class="sxs-lookup"><span data-stu-id="526d0-113">Element</span></span>|<span data-ttu-id="526d0-114">描述</span><span class="sxs-lookup"><span data-stu-id="526d0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="526d0-115">WideItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="526d0-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="526d0-116">定义其值在宽视图中显示的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="526d0-116">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="526d0-117">文本值</span><span class="sxs-lookup"><span data-stu-id="526d0-117">Text Value</span></span>

<span data-ttu-id="526d0-118">指定显示其值的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="526d0-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="526d0-119">备注</span><span class="sxs-lookup"><span data-stu-id="526d0-119">Remarks</span></span>

<span data-ttu-id="526d0-120">有关宽视图组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="526d0-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="526d0-121">示例</span><span class="sxs-lookup"><span data-stu-id="526d0-121">Example</span></span>

<span data-ttu-id="526d0-122">此示例显示了一个宽视图，其中[显示了 ProcessName 对象的](/dotnet/api/System.Diagnostics.Process)"" 属性的值。</span><span class="sxs-lookup"><span data-stu-id="526d0-122">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="526d0-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="526d0-123">See Also</span></span>

[<span data-ttu-id="526d0-124">WideItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="526d0-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="526d0-125">创建宽视图</span><span class="sxs-lookup"><span data-stu-id="526d0-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="526d0-126">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="526d0-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
